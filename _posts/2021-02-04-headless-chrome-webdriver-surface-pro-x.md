---
layout: post
title: 
date: 2021-02-3 14:45
tags: ["wsl2", "surface pro x", "chrome", "webdriver"]
summary:
---

When I try to execute a WebDriver-IO script in my Surface Pro X with the use of headless Chrome, I encounter the following exception,

```
[0-0] 2021-02-04T03:53:28.970Z ERROR webdriver: RequestError: connect ECONNREFUSED 127.0.0.1:9515
```

Resolution is to start the chromedriver manually first in one console with the command

`chromedriver`

Then start another console to run the testing script `npx wdio wdio.conf.js`