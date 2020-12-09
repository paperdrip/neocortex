---
layout: post
title: Passing environment variable to GO application in startup
date: 2020-11-14 09:15
tags: ["go"]
summary:
---

Sometimes, we want to pass attribute values as environment variable, either for security reason (like password) or to ease the deployment across envrionment.

The argument can be passed in runtime as below,

`ENV_VAR=VALUE go run main.go`

And VALUE can be retrieved using os.Getenv