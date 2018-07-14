---
layout: post
title:  "Design Patterns"
date:   2018-05-18 16:14:00 -0700
published: true
comments:  true
tags: notes design-patterns
---

Notes covering my foray into software design. ie. realizations that perhaps aren't as obvious as they might seem.

## Chain of Responsibility
Not knowing what objects send and receive the data may seem like an unusual characteristic; the reason it's desireable here is due to effect on an object's modularity.
In essence, it's fundamental to a concept known as 'black-box' abstraction. 
This has multiple advantages, among them processing steps (lovingly referred to as handlers) of the chain can be reordered as needed without having to modify their respective neighbors.
This makes the program's ability to insert/remove/reorder handlers more flexible.

## Command
This is an abstraction and ecapsulation of an 'action' to be performed, ie. a guideline for said action's object structure. 
In the 3rd project of CISC187 (a calculator), the command didn't directly perform the operation, instead acting as an interface layer which called the the overloads of the user-defined type (in this case operators of a 'big int' object). 
This UDT that contained said overloads acts as the receiver. 
The caller, or 'client', was the handler object from the chain of responsibility in the previous example.
