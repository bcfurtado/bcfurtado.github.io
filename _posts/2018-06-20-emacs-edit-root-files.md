---
layout: post
title:  "How to edit root files using emacs"
date:   2018-06-20 00:00:00 -0200
categories: everydayisanewday emacs
---
Why use `vi/vim` to edit root files when you can use Emacs to do it?

Emacs TRAMP mode allows you to easily access and edit remote files as if they were local. So you get the benefits of using all your local settings without the need of close your current instance or open a new one.

I don't use TRAMP frequently because I don't need to edit remote files anymore as I used to but it's interesting to share that you can use TRAMP to edit root local files as long you have `sudo` permissions.

I already shared a post on how to `Open remote files with emacs`. The principle is the same but in this case I'll share how to edit a file that has root permissions.

Steps:

1. Open the file with the root permissions by pressing `C-x C-f`.
1. Type `C-x C-q` to toggle read-only mode for the current buffer.
1. When you finish editing the file, type `C-x C-w` to save the file.
1. Delete the whole existing patch on minibuffer
1. Type `/sudo::/youfile.txt`. Enter.

Note that the `::` double colon is required.

```sh
  -rw-r--r--   1 root  wheel     895 Jun 20 16:41 myfile.txt
```

A gif worth more than 1000 words:

![Editing root files with emacs.](/assets/images/2018-06-20-emacs-edit-root-files.gif)

You can actually use `TRAMP` to open a new dired buffer as root using using `C-x D`  and then all the following buffers will be opened as sudo.

References:
- [https://www.gnu.org/software/tramp/](https://www.gnu.org/software/tramp/)
- [https://www.gnu.org/software/emacs/manual/html_node/elisp/Read-Only-Buffers.html](https://www.gnu.org/software/emacs/manual/html_node/elisp/Read-Only-Buffers.html)
- [https://www.emacswiki.org/emacs/TrampMode](https://www.emacswiki.org/emacs/TrampMode)

Few posts related to subject:
- [http://cestlaz.github.io/posts/using-emacs-25-tramp/](http://cestlaz.github.io/posts/using-emacs-25-tramp/)
- [https://swizec.com/blog/cool-thing-thursday-emacs-tramp-mode/swizec/5646](https://swizec.com/blog/cool-thing-thursday-emacs-tramp-mode/swizec/5646)
- [https://medium.com/@Drowzy/tramp-in-spacemacs-ef82b9e703ee](https://medium.com/@Drowzy/tramp-in-spacemacs-ef82b9e703ee)

Good luck!
