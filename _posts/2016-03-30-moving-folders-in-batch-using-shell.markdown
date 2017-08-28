---
layout: post
title:  "Moving folders in batch using shell"
date:   2016-03-20 00:00:00 -0200
categories: everydayisanewday
---
It's more like a mental note.


```
tree -L 1 | grep something | awk ’{print $2}’ | xargs -n 1 -I {} mv {} newfolder/
```
