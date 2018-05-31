---
title: design patterns
date: 2018-05-18 16:14:00 -0700
---
# Design Patterns
thoughts regarding my foray into desgin patterns. ie. mental notes and realizations that aren't as obvious as they seem.

# Chain of responsibility
Not knowing what objects send and receive the data may seem like an unusual characteristic, the reason it's desireable here is due to it's modularity. In essence a conept known as 'black-box' abstraction. this has multiple advantages, namely the procssing steps (lovingly referred to as handlers) of the chain can be reordered as needed without having to modify their respective neighbors. This makes the program's ability to insert/remove/reorder handlers more flexible.

# Command
insofar I can tell, this is an abstraction and ecapsulation of an 'action' to be taken, ie. a guideline of it's funcitonal structure. In the 3rd class project of CISC187 (a calculator), the command didn't actually perform the function, but rather acted as an interface layer to the overloads of the user-defined type (a 'big int').
