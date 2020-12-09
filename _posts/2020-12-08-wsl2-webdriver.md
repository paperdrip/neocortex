---
layout: post
title: Deverloping UI testing script in WSL2 using WebDriver 
date: 2020-12-08 16:14
tags: ["wsl", "development", "testing"]
summary:
---

I want to use webdriver in my WSL2 environment and there are several challenges. 

First, need to install Chromium Browser for ARM64. Secondly, I want to use headless browser so some changes are needed. Below are steps taken,

- Install NVM through a curl + bash execution
- Install NPM using NVM
- Cannot install Chromium through Snap and I am adding a PPA for DEB installation

```
sudo add-apt-repository ppa:xalt7x/chromium-deb-vaapi

cat <<EOF | sudo tee /etc/apt/preferences.d/pin-xalt7x-chromium-deb-vaapi
Package: *
Pin: release o=LP-PPA-xalt7x-chromium-deb-vaapi
Pin-Priority: 1337
EOF
```
- Install Chromium through apt get install chromium-browser which has a version for ARM64
- Install build essential so that I can create the needed node modules `apt install build-essential`
- Make sure package.json is using the same chromedriver version as the chromium browser
- Need to start chromedriver manually at the background, somehow wdio cannot put this up
- Add the args in wdio.conf.js including headless mode