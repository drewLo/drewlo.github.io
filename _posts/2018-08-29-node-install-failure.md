---
layout: post
title: "Difficulties installing node/npm [Solved]"
date: 2018-08-29 15:10:00 -0700
published: true
comments: true
tags: nodejs yarn issue closed
---

Node.js seems to be installed but my system is having trouble running it. 

# More Information:

- I can install both node and npm from my package manager (`dnf`) but I can't run them, and they don't appear in `/usr/local/bin`
- `npm` appears to install, but running it gives back the command `zsh: permission denied: npm`, even when running as sudo. some chmod's I tried didn't seem to affect it either, but that's an insecure and way to go about it regardless.
- Searching for node binaries, node_modules and npm files with `find` yields no results.
- Why would `dnf` see node and npm as installed, but can't be found on the system?
- node is installed, but using `which node` returns the error message: `/usr/bin/which: 'node not found' $PATH`.

## Solution:

- It appears the name of the node.js package is indeed `nodejs` and not `node`.
- `sudo dnf remove nodejs` : it uninstald node.js as well as `yarn` (as it depended on node and was now orphaned).
- This is uninstalling/rinstalling with `dnf` didn't work, it wasn't the right package. this is also why npm was behaving stragely, because it's normally bundled with node.js, and that may have explained th cause behind some package redundancy errors (`Can't install, package already exists`) I was experiencing prior to this.
  - these errors where occuring when trying to use `npm install`, I was receiving several `error: permission denied. package already exists` which was preventing installs from working. Come to think of it, this has probably been an issue for quite some time now, and why I haven't had much luck with npm-dependant projects I clone from git.

## Post Mortem:
- Lesson #1: make sure you have the right package names.
- Lesson #2: yarn and npm can cause file conflicts and it's not necessarily transparent. Based on error messages, it seemed the root issue was with permissions when in fact the permission errors were a symptom of `nodejs` not being properly installed.
  - In retrospect this should have been obvious to me when the 'package already exists' messages popped up, but I hadn't considered that yarn and npm would install the same packages. 
