---
layout: post
title: Installing pip packages from local
date: 2021-05-12 07:34
tags: ["linux", "python"]
summary: PIP packages local install
---

Installing packages behind firewall is troublesome, to say the least. Connectivity is always the culprit since explicit remote host access is never to be a once off exercise. 

The fall back plan is to download all the files to your local machine, upload to the server in need and conduct a local install.

The command below could do the tricks

```
python3 -m pip download -d ./python_pkg -r requirement.txt
python3 -m pip install -r requirements.txt --no-index --find-links file:///./python_pkg
```