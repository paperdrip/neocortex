---
layout: post
title: How do you define which user to start the terminal
date: 2021-03-06 11:34
tags: ["linux", "vs code"]
summary: Define the user to run the terminal
---

I have installed Code Server according to [this instruction](https://www.digitalocean.com/community/tutorials/how-to-set-up-the-code-server-cloud-ide-platform-on-ubuntu-20-04). All goes well except the terminal is running as root.

Digging up for information and turns out an additional line in the systemctl service configuration file `/lib/systemd/system/code-server.service` would do.

```
[service]
user=USERNAMEGOESHERE
```
