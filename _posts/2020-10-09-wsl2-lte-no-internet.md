---
layout: post
title: WSL2 cannot connect to the internet through LTE
date: 
tags: ["wsl2", "network"]
summary:
---

Bringing back my Surface Pro X back to the office and want to hack something out through WSL2. Given it is my own machine and I cannot connect to the office Wi-Fi which I intend on my LTE for internet connectivity.

Trying to update my ubuntu instance but encounter connectiity issue but ping is giving me back a result so it is not DNS issue.

Google `wsl2 lte` and found I am not alone. For some reason the WSL2 instance cannot connect to the internet through LTE but it would work if a VPN connection is first established.

Now I have another issue that none of the VPN provider I use provides an ARM64 client. But there is an OpenVPN client called [Viscosity](https://www.sparklabs.com/) that offers an ARM64 deliverable.

Install, configured my OpenVPN profile and ta-da, wsl2 can now connect to the internet.
