---
layout: post
title: Accessing Docker container exposed port from host
date: 2020-10-27 10:50
tags: ["wsl", "network"]
summary:
---

I published ports from the docker container but when I try to access it from the host, it cannot be reached.

Found a post explaining that only ipv6 is bind and thus I have to use the ipv6 localhost in accessing the container.

`http://[::1]/`

Original posts from [this location](https://github.com/microsoft/WSL/issues/4983)
