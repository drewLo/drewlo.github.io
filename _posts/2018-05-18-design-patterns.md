---
layout: post
title: Design Patterns
date: 2018-05-18 16:14:00 -0700
comments: true
published: true
categories: swe
tags: design-patterns notes
---

Notes regarding my foray into software desgin patterns. ie. discoveries and realizations that perhaps aren't as obvious as they might seem.

# Chain of Responsibility
Not knowing what objects send and receive the data may seem like an unusual characteristic, the reason it's desireable here is due to it's modularity. In essence a conept known as 'black-box' abstraction. this has multiple advantages, namely the procssing steps (lovingly referred to as handlers) of the chain can be reordered as needed without having to modify their respective neighbors. This makes the program's ability to insert/remove/reorder handlers more flexible.

# Command
Insofar I can determine, this is an abstraction and ecapsulation of an 'action' to be performed, ie. a guideline for said action's object structure. 
In the 3rd class project of CISC187 (a calculator), the command didn't actually perform the function, rather acted as an interface layer which called the the overloads of the user-defined type (a 'big int'). The UDT that contained said overloads in this scenario is the receiver. 
The caller, or 'client', was the handler from the chain of responsibility from the in the same project.
