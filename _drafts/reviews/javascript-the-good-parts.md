---
layout: post
category : review
tagline: "An up to date review of the Gang of Four classic"
tags : [books, review, design pattern]
---
{% include JB/setup %}

## Overview
Do you struggle when creating objects in Javascript?
Do you find the syntax to be non-intuitive and frustrating?
Do you know the difference between using a function as an object vs using an object literal?
Do you know how using object literals can simplify your code and create something similar to namespaces?
Do you know how to augment the type system -- for example, if wanted all strings to have a trim() method?
Do you know why the "new" statement is so dangerous? Do you know an alternative that eliminates the use of "new" entirely?

These are some of the topics that the book touches upon.

This book is aimed at someone with intermediate programming experience that wants to know the best way to create and use objects, arrays, types, etc. Crockford takes his experience with Javascript to show you best practices coding techniques and styles to use with Javascript. In addition, the book provides insights into what makes Javascript so confusing and what can be done about it.

You might ask "Isn't this stuff already covered in other books that I have?" The answer is no. For one, most other books use a psuedo-classical coding style (see below) to explain objects that is a source of confusion.

Javascript can be very confusing, especially for programmers who have extensive experience in other C-based languages (like myself). Writing good Javascript that uses objects, methods, etc. is hard. In Javascript, if you want to create objects, use inheritance and create methods, you have several different ways to write your code and it's difficult to know what the strengths and weaknesses of each are.

Crockford explains the problem plainly. Other C-based languages use class inheritance (Crockford calls this classical inheritance). Javascript, on the other hand, is the only popular language that uses prototype inheritance, which does not have classes. However, the syntax which Javascript uses to create object is Java-like (Crockford calls this pseudo-classical syntax). It's confusing, because it keeps you in a class-based frame of mind while working in a language that has no concept of classes.

Clarifying what's going on with the object model is the best part of this book. Crockford also explains other parts of Javascript that can be problematic and the techniques that he prefers for handling them. I don't necessarily agree with all of them, but the important thing is that he explains his reasoning.

To effectively learn Javascript, I recommend that you buy 1) a book that covers the details of the language and can be used as a reference (e.g. Javascript, the Definitive Guide) and 2) Crockford's book. Advanced programmers might also enjoy Pro Javascript Design Patterns, which shows a number of ways to combine Javascript with some of the GoF patterns. I would avoid any cookbook style books on Javascript, because you're better off using YUI, JQuery or one of the other Javascript libraries than writing your own drag-and-drops, calendars, etc.

There are a series of Yahoo! videos by Crockford that mirror the material in this book and can be found as podcasts under YUI Theater. They contain nearly all of the material in the book and probably a little more. Those videos are:

- Douglas Crockford/An Inconvenient API: The Theory of the DOM (3 parts)
- Douglas Crockford/The JavaScript Programming Language (4 parts)
- Douglas Crockford/Advanced JavaScript (3 parts)
- Douglas Crockford/Javascript The Good Parts