---
layout: post
title:  "Sending email with emacs and gmail."
date:   2015-10-02 00:00:00 -0200
categories: everydayisanewday emacs
---
How can I send a email with emacs using google smtp servers?

Emacs has an email client. To use it you just need type:

`C-x m`

But before that, you need configure the smtp server and authentication files.
Open your emacs configuration file: ~/.emacs and insert the following lines bellow to use gmail for example:


```lisp
(setq smtpmail-stream-type ‘ssl)
(setq smtpmail-smtp-server “smtp.gmail.com”)
(setq smtpmail-smtp-service 465)
```

Create a new file called: `~/.authinfo` and:

```
machine smtp.gmail.com login email@gmail.com password your_password port 465
```

After `C-x` m you can write your email as usual and at end, just type: `C-c C-c` and your email will be sent. :)

## Notes:

- If you are having some issue to send emails with gmail stmp server, try enable this feature in your gmail account:
[https://www.google.com/settings/u/0/security/lesssecureapps](https://www.google.com/settings/u/0/security/lesssecureapps)

- If you has 2 step verification login enabled, you will need create a specific password for this app.

- Keep passwords in text-plain files is insecure, but looks like you can encrypt the `.authinfo` file with your gpg key without problems.[http://emacswiki.org/emacs/GnusAuthinfo](http://emacswiki.org/emacs/GnusAuthinfo)

- This configuration was used with Emacs 24 and OS X Yosemite: 10.10.5

- Before I come with this configuration, I had tried others and I had installed the gnutls library via brew. I don’t think you will need, but I any case you can try install.

Sources:

- [http://www.emacswiki.org/emacs/GnusGmail#toc10](http://www.emacswiki.org/emacs/GnusGmail#toc10)
- [http://superuser.com/a/476716](http://superuser.com/a/476716)
