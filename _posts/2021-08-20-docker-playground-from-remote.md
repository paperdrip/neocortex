---
layout: post
title: Accessing docker playground from remote
date: 2021-08-19 14:34
tags: ["linux", "docker"]
summary:
---

Looking for a solution similar to katacoda, which we can learn interactively. Came across [this project](https://github.com/play-with-docker/play-with-docker) which provides a 'docker-in-docker' enviornment to try things out. Follow through the document and bring up the application but I cannot access it in the browser using anything but 'localhost'. From the log, I have noticed the following lines,

```
pwd        | 2021/08/20 06:18:50 Error retrieving playground f0cb7ed8-ee3b-59f2-843b-841fcb100825. Got: NotFound
pwd        | 2021/08/20 06:18:50 Playground for domain 100.115.33.20 was not found!
pwd        | [negroni] Started GET /
pwd        | [negroni] Completed 404 Not Found in 220.176µs
```

Found a hint from the issue log. I need to modify the file `config/config.go`, replace the value 'localhost' with the hostname I want to expose the site to. 

```
flag.StringVar(&PlaygroundDomain, "playground-domain", "localhost", "Domain to use for the playground")
```

Then I `docker-compose down --rmi all` and `docker-compose up` which have all things working now.