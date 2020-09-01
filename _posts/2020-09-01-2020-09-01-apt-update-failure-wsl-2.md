---
layout: post
title: Failed to 'apt update' in Ubuntu within WSL 2
date: 2020-09-01 13:45
tags: ["wsl", "linux"]
summary: 
---
One day when I boot up my Ubuntu instances in WSL and do the 'apt update', 

Then I looked at the date and realize it's off for days from the host. Googling around and find that it is [a bug in WSL] (https://github.com/microsoft/WSL/issues/4245)

`sudo hwclock -s` do the tricks
