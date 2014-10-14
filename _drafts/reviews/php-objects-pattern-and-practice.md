---
layout: post
category : review
tagline: "PHP Object Pattern Practice"
tags : [book, review, PHP]
---
{% include JB/setup %}

## Overview

Let's get things straight from the start, PHP is moving fast and this books is a bit outdated.

If you were like me when I started reading the book, a novice programmer struggling to understand object oriented programming, it is worth your attention and money spent.

The books was written at the crossroad of PHP4 and PHP5. 

The book is divided into 3 main parts.
    
    - Objects
    - Patterns
    - Practice
    
### Objects

The relic of pre PHP5 is apparent when the author talks about passing objects using the '&' operator and uneless and unless you have the task of maintaining a legacy system, .
Now, if you already know the basic principles of Object Oriented Programming this may bore you but you could also use it as a quick recap. On the other hand, if
you're a neophyte on the subject, using a very hands on approach, the author takes you by the hand and walks along very gently, step by step, into giving you a decent understanding behind the
core principles of object oriented programming. 

### Patterns

This is probably the most interesting section of the book. 

One of PHP's biggest strength is that it's easy to use with a very low barrier of entry but this also becomes one of it's greatest weakness.

Withing minutes you can create your very own spaghetti code that will be a nightmare to maintain.

This is probably why this book appealed to me so much because it proposed an easy way to get into design patterns and start thinking about
better application design using a common language.

also easy to misuse. Don't get me wrong, there are many brilliant PHP developers.
If you have never learned design patterns from other sources such as Gang of Four and you're most comfortable with PHP, this book will open up a world of possibilities.
    
    - Singleton : Now considered a dark pattern or an anti-pattern by many. While it can seems useful at first, the problem is that it introduces global
    variables by the backdoor and if you're into unit testing your code, it makes it especially difficult to deal.
    - Interpreter : Lean how to build a mini language with a fixed set of commands. The proposed example is not very appealing but if at some point you
     need to build some kind of interpreter as part of a system you're building, this pattern could come in handy.
    - Observer : This pattern is often used in implementing hooks or registering callbacks in web applications or in GUI applications.
    - Visitor : Visitor is a pretty cool guy and he isn't afraid of anything. The example from the book to illustrate this pattern takes a tiled based
    game akin to civilization where different units visit a particular tile. I don't think this is appropriate since it doesn't represent a real world use
    case scenario for PHP.
    
### Practice

You can safely read this section if you've never delved into unit testing. The rudiments are well explained and concise. However, most of tools 
presented are outdated. 

Today's PHP wizards then to use Composer instead of PEAR. There is a new tendency for dependencies inside of a project to be isolated into the project itself 
and not system wide.
 
SVN is still in use in some places but is outshined by more modern
tools like GIT or Mercurial. There is no mention of branching strategies and ways to collaborate into the hyper connected social media world of today. 
 
There is a section about build systems and deployement using Phing which is closely modeled after Java Ant. I have never seen any PHP application built with Phing
 and this may be ignorant but I'm assuming most people.
 
### Conclusion

Despite the criticism of being outdated in many ways, I would buy this book again. 

In the end, it made me a better programmer and I learned a lot. 

If I were to edit the book and include a revision, I would drop anything related lower to PHP5, add in new things about version control, test driven development,
collaboration, virtualization using vagrant or other tools, Composer, etc.