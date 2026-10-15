---
layout: post
title: Cloudflared failed to start due to routing issue with Tailscale
date: 2026-10-15 12:08
tags: ["linux", "cloudflared", "tailscale", "raspberry-pi"]
summary:
---

`cloudflared` failed to establish a tunnel on a Raspberry Pi that also runs Tailscale as an exit node. There were two separate problems.

## Problem

* **UDP buffer bottleneck:** `cloudflared` (via the `quic-go` library) requested 7168 KiB UDP send and receive buffers to handle QUIC traffic efficiently, but the Raspberry Pi OS kernel was limited to the default 208 KiB (`net.core.rmem_max` / `net.core.wmem_max`).
* **Connection timeouts to Cloudflare edge:** `cloudflared` repeatedly timed out trying to reach the Cloudflare Anycast IPs (`198.41.192.0/24` and `198.41.200.0/24`) on port 7844, because Tailscale was acting as an exit node and capturing all default outbound traffic (`0.0.0.0/0`).
* **Static route overrides did not work:** Adding a standard route with `ip route add` had no effect. Tailscale uses Linux policy routing (`table 52`), and the kernel evaluates that table before the `main` table where the physical interface (`eth0`) lives.

## Resolution

### 1. Adjust the kernel UDP buffers

Raise the maximum socket read and write limits to `7340032` bytes (7168 KiB) in `/etc/sysctl.d/99-quic-buffers.conf`,

```
net.core.rmem_max=7340032
net.core.wmem_max=7340032
```

Apply it with `sudo sysctl --system`. This removes the buffer starvation warnings and prevents dropped QUIC packets.

### 2. Bypass Tailscale with policy routing rules

Add high-priority rules (`priority 5000`) that match the Cloudflare public IP ranges and force them to look up `table main`. The tunnel traffic then goes out the physical interface (`eth0`) before Tailscale's rules (`table 52`) can intercept it.

```
sudo ip rule add to 198.41.192.0/24 lookup main priority 5000
sudo ip rule add to 198.41.200.0/24 lookup main priority 5000
```

Verify with `ip rule show`.

### 3. Apply the rules at boot with systemd

Create `/etc/systemd/system/cloudflare-bypass.service`,

```
[Unit]
Description=Bypass Tailscale for Cloudflare edge traffic
After=network-online.target
Wants=network-online.target
Before=cloudflared.service

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/sbin/ip rule add to 198.41.192.0/24 lookup main priority 5000
ExecStart=/usr/sbin/ip rule add to 198.41.200.0/24 lookup main priority 5000
ExecStop=/usr/sbin/ip rule del to 198.41.192.0/24 lookup main priority 5000
ExecStop=/usr/sbin/ip rule del to 198.41.200.0/24 lookup main priority 5000

[Install]
WantedBy=multi-user.target
```

Then enable it with `sudo systemctl daemon-reload && sudo systemctl enable --now cloudflare-bypass.service`.

`Before=cloudflared.service` makes sure the routing rules are active before the tunnel daemon tries to connect to the edge, which avoids a boot-time race condition.
