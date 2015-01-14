---
layout: post
category : reviews
tagline: "Design patterns elements of reusable object-oriented software review"
tags : [books, reviews, design patterns]
---
{% include JB/setup %}

![Design patterns elements of reusable object-oriented software](/assets/img/reviews/gof.jpg)


### Overview

GoF is a classic that doesn't need much of an introduction. 

After talking to other programmers, it came evident that I was expected to read it, so I did.

Reading GoF helps to understand the fundamental paradigms of software that are in place today and helps you to acquire a 
deeper understanding of how many project are structured.

Patterns are also helpful to learn because they are part of a standardised way to communicate high level abstract ideas 
among programmers.

### What I got out of it

The code examples are written mostly in C++ and Smalltalk, it doesn't matter if you're not a guru in any of these
languages as long as you know at least one object oriented language, you will be able to understand the demonstrated 
patterns.

GoF certainly has an academic feel to it but the intention of rigor behind it should be celebrated. 

Decoupling and extensibility is at the center stage of all the chapters.

The book is divided into three main parts, the first one about finding nicer ways to create objects and managing this process, 
the second one is about patterns that can help structure your applications and the third one is about elegantly adding 
behavior to different parts of your software in an extensible manner. 

Information is also easy to find since it's nicely indexed, whenever I find myself confronted with a pattern I want to get 
quick refresh on, I can usually find what I'm looking for a few within seconds.

Some of the patterns are almost irrelevant today since they come built it the languages we all use. 
For example : you always expect an Iterator when looping over just about any data structure, 
Memento is often used when you call the magic of serialization, Observers are all over the place when registering events 
listeners on a DOM element in JavaScript. 

But I must admit that it's really nice knowing how things might be implemented under the hood, it demystifies a lot of things 
that seemed magical and also helps you at finding better ways to leverage those mechanism already in place in whatever language, 
framework or platform you're already using.

This book also started to change how I approach the design of application in general, it really got me thinking about 
better ways to use code in a more extensible and decoupled manner.

I try to avoid the trap of adding patterns for the sake of having nice patterns; with more structure often comes more 
complexity but when I know that down the road, I will have to maintain a piece of software or that I will have to modify it, 
I better give my best effort and make it easy as possible to work with in the future.

After reading the book, I could also easily translate the illustrated concept from C++ to other languages like Java or PHP, 
it makes sense since they are all higher level concepts of application design. It a nice feeling to have something new in my 
toolbox.

One other thing, is that you get to learn about the original meaning of MVC as it was intended at first in the particular context 
of a text editor. As of today, MVC seems to be an abused term about anything that has to do with high level of separation 
of concern between the data model, the application logic and the presentation layer.

### Conclusion

Although it's getting seriously outdated in some aspects and the pattern scene evolved a lot since the time it was published during the 
90s, it remains an undeniable classic an a must read for any intermediate software developer looking to expand beyond the basics. 

