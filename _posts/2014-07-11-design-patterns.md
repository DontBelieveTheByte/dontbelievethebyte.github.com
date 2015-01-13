---
layout: post
category : review
tagline: "Design patterns elements of reusable object-oriented software review"
tags : [books, review, design pattern]
---
{% include JB/setup %}

![Design patterns elements of reusable object-oriented software](/assets/img/reviews/gof.jpg)


### Overview

GoF is a classic that doesn't need much of an introduction. 

It helps to understand the fundamental paradigms of software in place today and will help you acquire a deeper understanding 
of how many project are structured today.

Patterns are also helpful to learn because they are part of a standardised way to communicate high level abstract ideas 
among programmers.

The code examples are written mostly in C++ and Smalltalk, it doesn't matter if you're not a guru in any of these
languages as long as you know at least one object oriented language, you will be able to understand the demonstrated 
patterns.

First of all, it certainly has an academic feel to it but the intention of rigor behind it should be celebrated. 

The book is divided in three main parts, the first one about nicer ways to create objects, the second one is about patterns 
that can help structure your applications and the third one is about elegantly adding behavior to different parts of your 
software.

### What I got out of it

Information is easy to find, whenever I find myself confronted with a pattern I want to get a quick refresh on, I can find 
the information within seconds.

Some of the patterns are almost irrelevant today since they come built it languages, for example : you always expect and Iterators 
when looping over a data structure, Memento is often used when you call the magic of serialization, Observers are all over the place 
even when registering events listeners on a DOM element in JavaScript. But I must admit that it's really nice knowing and 
demystifies how things are probably implemented under the hood.

This book also started to change how I approach the design of application in general, it really got me thinking about 
better ways to use code. 

I try to avoid adding patterns for the sake of having nice patterns; with more structure often comes more 
complexity but when I know that down the road I will have to maintain a piece of software or that I will have to modify it, 
I better give my best effort to make it easy as possible to work with down the road.

After reading the book, I could also easily translate the illustrated concept to other languages like Java or PHP, it makes 
sense since they are all higher level concepts of application design but it was nice feeling that I have something new in my 
toolbox.

One nice other thing, is that you learn about the original meaning of MVC as it was intended at first. As of today, MVC seems 
to be an abused term about anything that has to do with high level of separation of concern between the data model and the 
presentation layer.

### Conclusion

Although it's getting seriously outdated in some aspects and the pattern scene evolved a lot since the time it was published, 
it remains an undeniable classic an a must read for any intermediate software developer looking to expand beyond the basics. 


Then there are the State and Strategy patterns, which are two sides of the same coin, and needn't be given two different names.