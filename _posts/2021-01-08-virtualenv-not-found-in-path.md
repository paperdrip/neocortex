---
layout: post
title: Installing virtualenv in Ubuntu 20.04
date: 2021-01-08 14:45
tags: ["linux", "python"]
summary:
---

I am following [this article](https://itnext.io/how-to-set-up-python-virtual-environment-on-ubuntu-20-04-a2c7a192938d) to install Virtualenv on my Lemur Pro. All goes well until I execute `source ~/.bashrc` which prompts me with the following error,

`bash: /usr/local/bin/virtualenvwrapper.sh: No such file or directory`

Turns out the installtion are kept in my HOME directory, under a hidden folder called ".local/bin". Updated the .bashrc, "source" it but hit another error when I try to create a new virualenv `mkvirtualenv depthai`. 

`ERROR: virtualenvwrapper could not find virtualenv in your path`

Need to change the environment variable again and this is how it looks like now,

```
#Virtualenvwrapper settings:
export WORKON_HOME=$HOME/.virtualenvs
export VIRTUALENVWRAPPER_VIRTUALENV=$HOME/.local/bin/virtualenv
VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
. $HOME/.local/bin/virtualenvwrapper.sh
```
