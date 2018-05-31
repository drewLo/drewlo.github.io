---
layout:  post
title:   "Setting Up Github Pages"
date:    2018-05-16 06:34:00 -0700
categories: jekyll setup github-pages
---

Getting DNS configured correctly has been somewhat of a headache. Partially because networking is still unexplored territory for me, but also because of the time websites take to update their cache. It makes it difficult to determine if the action I just took had any effect.

Removing either of the CNAME or redirects caused problems, but I was able to find the local minima of stuff that needed to be configured, after a few (5!) hours. 

Mostly it came down to not knowing what I was supposed to actually do, to get the settings correctly configured. I was able to get the aliasing done probably 3 hours in, but I kept working because https wasn't getting set up, and I also wanted to get more familair with the process, since it could pay off for me in the future (with other pages).

Despite having to sift through a ton of documentation (scoured every bit of github docs on custom domains...), partly to learn the vocabulary (Like dns records, `CNAME` vs redirects, `A` vs `ALIAS` and so on) and also because some descriptions weren't specific, I finally encountered a [namecheap help page][nc-gh-setup] to get set up and running with github pages. what took me 5 hours probably could have been accomplished in less than 1 had I simply search namecheap's knowledgebase, oh well!

Now to begin work on the actual page! This took up way more time than I should have given it, but there was definitely lessons learned in the process of getting this up and working. It was supposed to be a break from my last programming project for the semester! And it turned into the programming project of the day!

Anyway, here were my successful settings + steps, and the sites they were performed on:

1. [namecheap] then set github's 4 IP's as A records under the advanced DNS tab.
2. [namecheap] and my page's github url (drewlo.github.io) as the (host: www) CNAME record.
3. [github] set the custom domain field in the github repo's settings to my custom namespace domain.

[nc-gh-setup]: https:https://www.namecheap.com/support/knowledgebase/article.aspx/9645/2208/how-do-i-link-my-domain-to-github-pages
