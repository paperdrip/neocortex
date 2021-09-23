---
layout: post
title: 
date: 2021-05-27 14:34
tags: ["wsl2", "k3d", "k3s"]
summary:
---

I am trying out something with k3d and want to access from the external host. The key to make this happen is to publish the ports needed when I create the cluster.

```
k3d cluster create mycluster -p 8082:30080@agent[0]
```

The above will create a K3S cluster named "mycluster" with localhost port 8082 to the nodeport 30080 where "agent[0]" is the first working agent in the cluster.

Alternatively, we can create the cluster and map the port to the ingress.

```
k3d cluster create --api-port 6550 -p "8081:80@loadbalancer"
```

Each provisioned cluster will has a loadbalancer labelled "loadbalancer". So the sytax is to map the local port 8081 to port 80 of the loadbalancer and it is looked up using the "loadbalancer" tag through nodefilter.

