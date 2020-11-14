---
layout: post
title: Using REDIS container image and assign it with a password
date: 2020-11-14 08:45
tags: ["docker","redis"]
summary:
---

By default, the Docker image provided by REDIS is having no authentication password. To secure the access, we need to either pack our container image together with a configuration file or volume mount where the configuration file resides.

Just learnt another trick that we can pass the password as an attributes when we start up the container.

`docker run --name redis -p 6379:6379 -d redis redis-server --requirepass "<your strong password>"`

