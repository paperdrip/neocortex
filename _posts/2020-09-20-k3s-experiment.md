---
layout: post
title: K3S Experiment
date: 
tags: ["k8s","k3s","edge"]
summary:
---

Edge cluster is a topic I would like to explore. I am leveraging some free services I found to conduct my experiment.

### Edge Cluster
[Civo](https://www.civo.com) is the first company offering commercial hosting of K3S cluster. They are now offering a campaign called #Kube100 which $70 credits is provided monthly in trying out their service. The smallest instance is only $5/month so a 2 nodes cluster would only cost $10. I could easily scale 7 clusters without paying a dime. 

That's my original plan but it didn't work out because I could not fit everything in a tiny cluster.

### Observability
[NewRelic](https://www.newrelic.com) is my all time favorite. Setting up both the infrastructure and APM is very easy and straight forward.

### Deployment
[Codefresh](https://www.codefresh.io) is what I use for build and deploy. One tools for all is the reason for my pick. It's offering 14-days of trial, I will need to decide if I need to pay for it.

### Cluster management
[Lens](https://k8slens.dev/) is an amazing tool. Once I imported the kube_config file, I can start managing the cluster and conduct most of the operation with a GUI
