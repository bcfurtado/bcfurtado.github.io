---
layout: post
title:  "A better git log"
date:   2015-01-23 00:00:00 -0200
categories: everydayisanewday
---
A better git log.

![A better git log.](/assets/images/2015-01-23-git-log.jpg)

Add it to your git config file in `~/.gitconfig` in the `alias` section:

```
[alias]
    lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
    lg2 = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit --date=short
```

Then use on console: `git lg` or `git lg2` on your project.

[https://coderwall.com/p/euwpig/a-better-git-log](https://coderwall.com/p/euwpig/a-better-git-log)
