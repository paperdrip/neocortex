---
layout: post
title: DNS resolving issue in WSL2
date: 2020-09-01 15:34
tags: ["wsl", "linux"]
summary:
---
My WSL instances failed to `apt update` and stuck at "0% [working]". Try to do a wget to the repo and realize the domain name failed to resolve.

Google around and find it might be [WSL issue with domain resolution] (https://github.com/microsoft/WSL/issues/4285).

Follow one of the suggestion to just shutdown wsl and start it again. All works again.

