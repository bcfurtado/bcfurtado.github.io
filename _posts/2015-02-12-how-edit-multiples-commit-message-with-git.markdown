---
layout: post
title:  "How edit multiples commit message with git"
date:   2015-02-12 00:00:00 -0200
categories: everydayisanewday
---
If you want to edit more than one commit message, run:

```sh
git rebase -i HEAD~commit_count
```

Replace `commit_count` with number of commits that you want to edit.

This command launches your editor. Mark the first commit (the one that you want to change) as “edit” instead of “pick”, then save and exit your editor. Make the change you want to commit and then run

[http://stackoverflow.com/a/7070976/1133742](http://stackoverflow.com/a/7070976/1133742)
