---
layout: post
title: Monitor NodeJS app with New Relic
date: 
tags: ["observability", "nodejs"]
summary:
---
I would like to add observability to the demo app Let's Chat. It is written in NodeJS and I am following [this page](https://docs.newrelic.com/docs/agents/nodejs-agent/installation-configuration/install-new-relic-nodejs-agent-docker) to add the agent needed.
- Modify package.json and add `"newrelic": "latest",` according to the alphabatical orders.
- Modify app.js and add `require('newrelic');` at the beginning of the file. In my case, I put it in front of the line `require('colors');`