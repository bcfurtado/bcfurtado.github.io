---
layout: post
title:  "Hidding / Pausing your process in shell"
date:   2015-08-19 00:00:00 -0200
categories: everydayisanewday
---
This is some interesting thing to know. I already had read about it sometimes, but how I not used to use this command I always forget.

Imagine you had opened your shell command. You are editing a file in a remote server behind a ssh connection. You are using the VI as text editor. You had started to edit him, but now you need come back to home directory of your remote machine, but you don’t want lost your changes, don’t wanna save him and don’t want open another remote connection. What do you do?

You just need press `Ctrl + Z` and your process will go to background and when you finished to come back just type `bg`.
