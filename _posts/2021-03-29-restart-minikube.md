---
layout: post
title: Resuming the minikube cluster
date: 2021-03-28 14:34
tags: ["wsl", "minikube"]
summary:
---

Work machine get restarted over the weekend and I realize the minikube cluster is not running.

Need to do the below in regaining the services,

1. minikube stop
2. minikube start
3. minikube service frontend-external (replace the last argument with service name you want to expose)

The docker container should then be started and I can start using kubectl to monitor the cluster
