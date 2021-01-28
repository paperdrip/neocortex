---
layout: post
title: Installing DB-less Kong API GW in Ubuntu 20.04
date: 2021-01-27 14:45
tags: ["kong", "linux", "api"]
summary:
---

Kong provides APT repository to ease the installation but it would need the following files to start the service,

- kong.yml
- kong.conf

kong.yml is created by `kong config init` and a template of kong.conf can be downloaded from `https://raw.githubusercontent.com/Kong/kong/master/kong.conf.default` 

Next, we need to add the following three lines to the kong.con

```
database = off
declarative_config = <location where the kong.yml could be found>
admin_listen = 0.0.0.0:8001
```

We can then start Kong and pass in the location of the configuration file as an argument

`sudo kong start -c <path to the kong.conf>`

Admin portal could be reached from `ip:8001`
