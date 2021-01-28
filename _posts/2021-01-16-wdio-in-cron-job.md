---
layout: post
title: Run Selenium test using WebDriverIO in a cron job 
date: 2021-01-16 10:45
tags: ["linux", "selenium"]
summary:
---

I want to generate some traffic to my blog for analytic purpose. Wrote a selenium script using a headless Chrome Browser and WebdriverIO. All works well but it doesn't work when I put it as a cron job.

```
[0-0] TypeError in "Open Web browser in the chrome Page should open"
TypeError: Cannot read property 'getAttribute' of undefined
```

I guess the issue is the crontab session has not load the NVM library so I added a line to load the `.bashrc` which resolved the issue.