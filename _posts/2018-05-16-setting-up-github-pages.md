---
layout:  post
title:   "Setting Up Github Pages"
date:    2018-05-16 06:34:00 -0700
categories: web
published: true
comments: true
tags: notes github-pages web
---

Getting DNS configured correctly was an adventure. 
Partially due to the intricacies of DNS still being unexplored territory for me.

Like the the time websites take to update their cache or to propagate changes, vs my local environment. 
Redirect records and TCP/IP also acted a point of confusion.. 
At first it took some getting used to discerning if the action I just took had any effect. 
In my defense, I've never considered myself much of a web developer.

Removing either of the CNAME or redirects caused problems, but I was able to find the local minima of stuff that needed to be configured, after a few (5!) hours. 

Most of the time-cost was due to my own inexperience and not knowing which steps to take.
I was able to get the aliasing done probably 3 hours in, but I kept working because https wasn't turning on.
It still isn't working, I assume I need to wait for my previous cert to expire.
I'm thankful that I was able to get more familair with the process, since it could pay off for me in the future (with other pages).

Despite having to sift through a ton of documentation (scoured every bit of github docs on custom domains...), partly to learn the vocabulary (Like dns records, `CNAME` vs redirects, `A` vs `ALIAS` and so on) and partly because several descriptions weren't specific. 
I finally encountered a [namecheap help page][nc-gh-setup] to get set up and running with github pages. what took me 5 hours probably could have been accomplished in less than 1 had I simply search namecheap's knowledgebase, oh well! 
I should mention that the namecheap help page, while being more catered to my needs, still required digging to discover confident solutions. 

Now to begin work on the actual page content! 
This took up way more time than I should have given it, but there were definitely some important basics learned in the process of getting this up and working. 
It was supposed to be a break from my last programming project for the semester! And it turned into the programming project of the day!

Anyway, here were my successful settings + steps, and the sites they were performed on:
1. [namecheap][namecheap] then set github's 4 IP's as A records under the advanced DNS tab.
2. [namecheap][namecheap] and my page's github url (drewlo.github.io) as the (host: www) CNAME record.
3. [github][github] set the custom domain field in the github repo's settings to my custom namespace domain.

[nc-gh-setup]: https:https://www.namecheap.com/support/knowledgebase/article.aspx/9645/2208/how-do-i-link-my-domain-to-github-pages
[namecheap]: https://www.namecheap.com/
[github]: https://github.com/
