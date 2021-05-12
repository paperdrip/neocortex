---
layout: post
title: Setting up virtualenv
date: 2021-05-12 06:34
tags: ["python", "linux"]
summary: Using virtualenv in Linux
---

It won't be the single post that talks about virtualenv since everytime I set this up, I forgot what I have done.

Installing virtualenv is straight forward; `python3 -m pip install virtualenv` and `python3 -m pip install virtualenvwrapper`

But there are configurations that needs to put in `~/.profile`

```
# adding virtualenvwrapper to path
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
export WORKON_HOME=~/Envs
export PATH=$PATH:/home/ronnie/.local/bin
```

The first line define where the python executable should be used. Since the virtualenvwrapper.sh, it will look for the python command using `which python` and since we are using python3, it won't work.

The second line define where the virtual environment should be created.

The last line is adding the virtualenvwrapper command to path so that I can create environment using `mkvirtualenv`