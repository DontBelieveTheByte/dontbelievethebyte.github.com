---
layout: post
category : reviews
tagline: "PHP Object Pattern Practice"
tags : [books, reviews, PHP, webdev]
---
{% include JB/setup %}

![PHP Object Pattern Practice](/assets/img/reviews/php-objects-patterns-practice.jpg)

## Overview

Let's get things straight from the start, PHP is moving fast and this books is a bit outdated.

The books was written at the crossroad of PHP4 and PHP5 when the former was dying off and the later came into full vitality.

Even with this downfall, I found it to be an invaluable resource into my learning journey. 

If you were like me when I started reading the book, a novice programmer struggling to understand object oriented programming 
wanting to learn more about design patterns and application design in general, I think it is worth your attention and every penny spent.

I have owned this book for a while and I've read it three times from cover to cover so far, I find myself going back to it often 
since at the moment, I'm trying to implement my own MVC application from scratch as a learning tool that will transpose to 
larger frameworks like Symfony.

The book is divided into 3 main parts which I will review individually.
    
    - Objects
    - Patterns
    - Practice
    
### Objects

As the first chapters get going, the relic of pre PHP5 is apparent. 

The OOP additions to the language was an afterthought, never had to code in PHP4 or less in my and and seeing the author 
writing about passing objects using the '&' operator in order to avoid automatic copying like primitives and instead 
explicitly passing by reference. This is not an issue anymore for objects and when you're using the '&' symbol it's mostly for 
passing around primitives with a particular intent you want to achieve.

The chapter does a decent job at gently introducing what OOP is by showing clear examples in code. 

There are no formal definitions, just logical inferences from what's happening as you run the provided examples either in your head 
or taking the time to type out the examples.

If you know the basics of OOP, you may want to skip this chapter as you'll find it boring, otherwise go ahead and read it.

### Patterns

This is probably the most interesting section of the book and fortunately, it becomes PHP5 centric at this point and PHP4 is 
never mentioned again.

One of PHP's biggest strength is that it's easy to use with a very low barrier of entry but this also becomes one of it's 
greatest weakness. 

Let me explain.

Don't get me wrong, there are many brilliant PHP developers out there but withing minutes, you can create your very own spaghetti 
code that will be a nightmare to maintain for years.

This is probably why this book appealed to me so much after because it proposed an easy way to get into design patterns 
with a language I already knew and got me started thinking about better application design using a common language.

If you have never learned design patterns from other sources such as Gang of Four and you're most comfortable with PHP, 
this book will open up a world of possibilities until you're able to dig a little deeper.

One caveat I must mention is that sometimes, the pattern examples seemed forced.
 
I will explain this further. They seemed forced in the sense that the examples do not relate to a real world PHP use case.

It misses many opportunities to show scenarios where you would recognize that you can indeed apply this pattern in order to 
solve web applications related problems you have since after all, this is in the context of PHP.

The biggest offender here is probably the visitor pattern which showcases a civilisation type game example. 

I have not seen any serious game engines made with PHP, ever.

I'm not sure either why I would need the interpreter pattern in PHP since proper form validation would be more appropriate in 
the provided example.

A discussion on singletons and it's alternatives would be nice, since it's often considered a dark pattern. 

I appreciated the chapter about MVC, it's all I hear about these days. Learning about separation of concern 
of different layers in this manner gave me tools to understand the architectural decision between the most popular web frameworks 
of today, it's all suddenly a much clearer in my head now.
 
### Practice

This section of the  book should be modernized to reflect the PHP world of today. 

Drop anything related to older PHP versions, revise the chapter about version control to include git instead of CVS, 
modern TDD techniques (which I'm very curious about) to go along with the chapter about unit testing chapter, 
composer instead of PEAR, virtualization tools like vagrant, etc.

You can safely read this section if you've never delved into unit testing since the rudiments are well explained and concise.
I'm still guilty of not writing tests though. 

I also learned a lot about reflection but I'm sure why I should use it so far.
 
### Verdict

Despite the criticism of being outdated in many ways, I would buy this book again. 

In the end, it made me a better programmer, got me thinking about application design in general from a higher level standpoint
and I learned a lot from it. 

I will soon be able to read the classic Gang of Four after this introduction to design patterns and that's what I'm really 
after from the start.
