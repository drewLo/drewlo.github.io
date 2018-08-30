---
layout: post
title: "[Open] node/npm install failure"
date: 2018-08-29 15:10:00 -0700
published: true
comments: true
tags: GNU+Linux issue open
---

# Problem:

- Somewhere in the process of installing/Uninstalling node I messed something up big time.
- I can install both node and npm from my package manager (`dnf`) but I can't run them, and they don't appear in `/usr/local/bin`
- `npm` appears to install, but running it gives back the command `zsh: permission denied: npm`, even when running as sudo. some chmod's I tried didn't seem to affect it either, but that's an insecure and way to go about it regardless.
- Searching for node binaries, node_modules and npm files with `find` yields no results.
- Why would `dnf` see node and npm as installed, but can't be found on the system?