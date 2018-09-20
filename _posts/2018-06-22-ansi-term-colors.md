---
layout: post
title:  "Terminal using unusual color palette/face for ls [Closed]"
date:   2018-06-15 17:32:11 -0700
published: true
comments:  true
tags: emacs issue
---

Emacs' ANSI-term had some hard to read colors. 
Text was unreadable.

![Weird Colors](/images/emacs-term-wrong-colors.png "Weird Colors")

## Attempts:

- Changing them in `gnome-terminal` preferences had no effect. 
- Changing emacs' theme had no effect.
- Altering the colors for the `ls` program in .bashrc (or in my case, .zshrc) worked for gnome-terminal, but not for anything in emacs.
- using different terminal emulators had a slight effect, nothing seemingly controllable though.

## Solution:

1.  `M-x customize`
2.  search term: `term color`
3.  set the term color variables from here.
  3a. you can also go into `M-x customize-group` and search for `ansi-color-names-vector` and edit the values. some color variables' are pulled from here.
