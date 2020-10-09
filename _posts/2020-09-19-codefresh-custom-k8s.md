---
layout: post
title: Using custom Kubernetes Cluster in Codefresh
date: 2020-09-19 22:14
tags: ["k8s"]
summary:
---
1. Give full permission to default account

`kubectl create clusterrolebinding default-admin --clusterrole cluster-admin --serviceaccount=default:default -n default
`

2. Obtain Host IP
Look for the API URL that is accessible from the internet

3. Obtain Certificate

`kubectl get secret -o yaml`

Look for the field "ca.crt" and copy the value

4. Obtain Token

Look for the field "token" and copy the value