---
layout: post
title: Set the default container enginer in minikube
date: 2021-03-23 14:34
tags: ["minikube"]
summary:
---

Minikube supports to run on different virtualization engine, such as docker or podman. We can define it in the runtime as argument, or we can put it into configuration file located in

`$HOME/.minikube/config/config.json`

The content of the file as follows,

```
{
    "driver": "podman"
}
