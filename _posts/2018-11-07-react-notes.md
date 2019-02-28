---
layout: post
title: "React-js Notes"
date: 2018-11-07 11:10:00 -0700
comments: true
tags: notes react
---

A friend recommended React JS as a framework to build websites. Here I'll document concepts and snippets that helped me.

# Big Ideas

```React is a declarative, efficient, and flexible JavaScript library for building user interfaces. It lets you compose complex UIs from small and isolated pieces of code called “components”.```[2]
React's main purpose is to build web interface applications.
If you'r new to web development, or code in general, it's going to be a bumpy ride.
At the time of this writing I find this framwork to be really complex, I've been reading the documentation for months and still don't feel like I can use it.

- React is efficient, it seems to take the 'do less' approach to optimization.
- everytime the 'page''s content changes, react updates only the part that changed.

## What is special about React

- "React is built around the concept of components. This is in contrast to frameworks like Angular and Ember, which use two-way data bindings to update the HTML of the page. In my opinion React is easier to learn than Angular and Ember - it is much smaller and plays nicely with jQuery and other frameworks. It is also extremely fast, because it uses a virtual DOM, and syncs only the changed parts with the underlying page (accessing the DOM is still the slowest part of a modern web application, which is why the framework gets a performance boost by optimizing it).[1]

# JSX

It's javascript, that looks like html.
It looks like you're mixing html with javascript in the code, but it's not really html (it's actually xml?).

# CDN

React has a CDN, but I don't know what benefits it provides as compared to just using the react source.

{% highlight html %}
<script src="http://fb.me/react-0.10.0.min.js"></script>
{% endhighlight %}

# Components

Big part of the 'React Model'.
Attempt to put it simply: with functions, you can define it, the input, the behavior and so on.
With components, you are defining the "parts" of your UI, like buttons, menus and thier items, profile picture, options, content and so on.
React doesn't handle styling or animation, css still does that.

# State vs Props

These seem to stem from the weird way javascript handles scope.

## State

- is an object (or in this case a component)'s local attributes, or in other words, it's an object's data.
- It's (supposed to be) immutable.
- it gets passed onto the child's objects as props.
- it can't be accessed outside outside of the object's scope (like by a parent or sibling function)

### Important

- the `render()` method is called every time state c~hanges.
- this is when react checks for changes and updates th changed parts.

## Props

- can be thought of like options, or parameters.
- the super() method is invoked with `props` as an argument in a components' constructor to create a bridge between the component and it's parent (unsure pls fix???).

# Flux Design Pattern

- A suggested way of handling 'data flow' in your react application.

# ReactDOM

- The DOM is the 'model' we have for how wbpages are structured. it's akin the the <body> and <head> tags and their respective contents.
- React has an object that... does something to it????

# Methods

## Lifecycle Methods

- These are member functions (ie. methods) of a component which are executed at different parts of the component's lifecycle.
- think of it like a constructor /destructor but instead of just running at the start / end, there are extra stages.


[1]: https://tutorialzine.com/2014/07/5-practical-examples-for-learning-facebooks-react-framework
[2]: https://reactjs.org/tutorial/tutorial.html