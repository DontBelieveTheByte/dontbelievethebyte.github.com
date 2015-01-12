---
layout: post
category : review
tagline: "PHP Object Pattern Practice"
tags : [book, review, PHP]
---
{% include JB/setup %}

![PHP Object Pattern Practice](/assets/img/reviews/php-objects-patterns-practice.jpg)

## Overview

Let's get things straight from the start, PHP is moving fast and this books is a bit outdated.

The books was written at the crossroad of PHP4 and PHP5.

Even with this downfall, I found it to be an invaluable resource. If you were like me when I started reading the book,
 a novice programmer struggling to understand object oriented programming, it is worth your attention and every penny spent.

I've owned this book for a while and I've read it three times from cover to cover and I find myself going back to it often
 since I'm trying to implement my own MVC application from scratch.

The book is divided into 3 main parts which I will review individually.
    
    - Objects
    - Patterns
    - Practice
    
### Objects

The relic of pre PHP5 is apparent as the OOP addition the language was an afterthought, the author talks about passing
 objects using the '&' operator to avoid automatic copying like primitives and instead passing by reference,
this is not an issue anymore for objects and when using the '&' symbol, it's an explicit behavior you want to achieve.

The chapter does a decent job at gently introducing what OOP is by showing clear examples in code. There are no formal 
definitions just logical inferences from what's happening as you run the provided examples.

If you know the basics of OOP, you may want to skip this chapter as you'll find it boring, otherwise go ahead and read it.

### Patterns

This is probably the most interesting section of the book and fortunately it becomes PHP5 centric at this point and no more 
PHP4.

One of PHP's biggest strength is that it's easy to use with a very low barrier of entry but this also becomes one of it's greatest weakness.

Don't get me wrong, there are many brilliant PHP developers but withing minutes you can create your very own spaghetti code
 that will be a nightmare to maintain for years.

This is probably why this book appealed to me so much because it proposed an easy way to get into design patterns and start thinking about
better application design using a common language.

If you have never learned design patterns from other sources such as Gang of Four and you're most comfortable with PHP, 
this book will open up a world of possibilities until you're able to.

Sometimes, the pattern examples seemed forced in order to show the pattern, I will explain this further. They seemed forced
in the sense that they do not relate to real world PHP examples and it misses the opportunity to show a use case where 
you would recognize that you can indeed apply this pattern in order to solve a web application related problem you have.
The biggest offender here is probably the visitor pattern which showcases a game example. I have not seen any game made with PHP, ever.
I'm not sure either why I would need the interpreter pattern in PHP.

A discussion on singletons, that is considered a dark pattern would have saved me some time in order to never implement such a thing.

I appreciated the chapter about MVC, it's all I hear these days, anything becomes MVC. Learning about separation of concern
 in this manner gave me tools to understand the architectural decision between the most popular frameworks of today, it's 
 all suddenly a much clearer in my head now.
 
### Practice

This section of the  book should be modernized to reflect the PHP world of today, drop anything related to PHP4 and lower, revise the chapter 
about version control to include git instead of CVS, modern TDD techniques (which I'm very curious about) to go along with the chapter 
about unit testing chapter, composer instead of PEAR, virtualization tools like vagrant, etc.

You can safely read this section if you've never delved into unit testing and the rudiments are well explained and concise.
I'm still guilty of not writing tests though. 

I also learned a lot about reflection but I'm sure why I should use it. 
 
### Conclusion

Despite the criticism of being outdated in many ways, I would buy this book again. 

In the end, it made me a better programmer, got me thinking about application design in general from a higher level standpoint
and I learned a lot from it. I will soon be able to read the classic Gang of Four after this introduction to design patterns 
and that's what I'm really after from the start.

