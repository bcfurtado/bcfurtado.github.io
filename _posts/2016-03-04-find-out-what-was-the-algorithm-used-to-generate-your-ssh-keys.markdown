---
layout: post
title:  "Find out what was the algorithm used to generate your ssh keys."
date:   2016-03-04 00:00:00 -0200
categories: everydayisanewday
---
Find out what was the algorithm used to generate your ssh keys.

I create my ssh keys at some long time ago I do not even remember with was the algorithm and the encryption level I used to generate them.

Lucky you can type this for find it out:

```sh
[palvarez@oizon ~]$ ssh-keygen -l -f ~/.ssh/id_rsa.pub 2048 2e:8c:fd:aa:9f:95:86:9e:b0:d2:a6:1a:7e:d3:3e:74 .ssh/id_rsa.pub (RSA)
```


Explanation:
 -l          Show the fingerprint of the key file.
 -f filename Filename of the key file.

Source: [http://superuser.com/a/139311](http://superuser.com/a/139311)
