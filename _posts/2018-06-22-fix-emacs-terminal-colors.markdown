---
layout: post
title:  "Emacs terminal using unusual colors"
date:   2018-06-15 17:32:11 -0700
published: true
comments:  true
tags: emacs fix
---

## Problem:
Emacs terminal was not using the correct color pallette, much text was unreadable because it was highlighted in a mismatched color with similar contrast.

![Weird Colors](/images/emacs-term-wrong-colors.png "Weird Colors")

## Attempts:
- Changing them in `gnome-terminal` preferences had no effect. 
- Changing emacs' theme had no effect.
- Altering the colors for the `ls` program in bashrc (or in my case zshrc) had no effect.

## Fix:
1. `M-x customize`
2. search term: `terminal`
3. open the drop-down for `Mm External Terminal Program`
4. enter your terminal of choice, in my case this was `gnome-terminal`
   - The name of your terminal is what isused to launch an instance (`xterm`, `termite`, et al.)
5. restart (might not be necessary, but just in case).

![Color Fix](/images/emacs-terminal-color-fix.png "Color Fix")
