---
layout: post
title: Installing K3S with read access by non-root user
date: 2021-03-06 14:34
tags: ["linux", "k3s"]
summary: File access right of k3s.yaml
---

Installed K3S in Ubuntu but I need to `sudo` for `kubectl` command. Not ideal.

Turns out there's an environment variable to configure the access mode of `k3s.yaml`

Re-install using the command below and I can manage my cluster without using `sudo`

```
curl -sfL https://get.k3s.io | sh -s - --write-kubeconfig-mode 644
```