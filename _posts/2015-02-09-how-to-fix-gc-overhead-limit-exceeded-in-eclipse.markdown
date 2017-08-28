---
layout: post
title:  "How to fix GC overhead limit exceeded in Eclipse"
date:   2015-01-10 00:00:00 -0200
categories: everydayisanewday
---
IntelliJ is a amazing IDE, however not always we can use this IDE in our work environment. So, Eclipse is a default IDE in a lot of companies and we spend working with those tools.

Some time I notice when I started working with Workspaces with a lot of project is Eclipse start to had a poor performance and constantly have some locks when it doesn’t just stop and throw a exception in your face. Something I never had using IntelliJ, for example.

One error I usually was always receiving was GC overhead limit exceeded. This means the Eclipse was in need of more memory to execute your command than actually was available.

Something what had worked for me was just increase the memory to Eclipse. The solution for this problem I found [here](https://docs.oseems.com/general/application/eclipse/fix-gc-overhead-limit-exceeded).
