---
layout: post
title: Managing K3S cluster from remote
date: 2023-10-05 14:34
tags: ["linux", "k3s"]
summary:
---

Provisioned a K3S cluster on a remote machine and try to manage it through the `kubectl` cli command.

After the cluster is provisioned, download `/etc/rancher/k3s/k3s.yaml` and modify the line `server: https://127.0.0.1:6443`, replace the localhost IP with the IP of the remote server

Then, set the ENV VAIRABLE poiniting to where the file is kept as below,

`export KUBECONFIG=/where the k3s.yaml is located/`

You could then use `kubectl` to manage the cluster 
