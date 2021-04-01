---
layout: post
title: Running multiple minikube
date: 2021-04-01 06:43
category: 
author: 
tags: ["minikube", "linux"]
summary: 
---

Want to try something out but don't want to mess up the minikube cluster I am using. Turns out there's a way to run multiple of minikube on the same machine by passing in the `-p` options. Example below,

`minikube start -p ambassador`

What that mean is, I will start a minikube cluster with the profile name "ambassador".

Next, I would need set the context to use in kubectl.

First, I can get a list of all context with this command,

`kubectl config get-contexts`

Next, I can set the context I want to use with,

`kubectl config use-context ambassador`