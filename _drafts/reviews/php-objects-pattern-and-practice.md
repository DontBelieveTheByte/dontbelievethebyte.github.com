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

I've owned PHP Objects, Patterns, and Practice for over a year, and it's still one of those books I go back to. It's a well written, generally well executed book on what constitutes Object Oriented Programming in the PHP5 environment.

First, the good news:

This book is a crash course on OOP design and thought. It borrows heavily from two monumentous texts in the field - the Gang of Four's book, and Java Enterprise Patterns - and condences their essences into an easy to swallow form. The basics are all here: how to create well designed classes, how to instantiate objects, etc. There's a hidden gem in the introductory portion of the book: the Reflection API. This API is built into PHP, and gives the coder unparalleled access to the guts of the classes and objects in a given project. It definitely has its uses.

The patterns are all generally useful, with the only exception perhaps being the Interpreter pattern. I'm just not convinced that creating one's own command line interface syntax is necessary, given that PHP projects aren't usually interactive. It seems like something best left to an appendex, or extra web content.

Now, for the bad news:

Some sections of the book, especially some of the code examples, could've used a better editor. Small things, the kinds of things that can trip up inexperienced coders, crop up. Using private properties instead of protected. Using the wrong variable name between examples. That sort of thing.

There's also a lack of a satisfying conclusion, so-to-speak. Zandstra himself claims that generating objects is perhaps the hardest thing to demonstrate. Yet, most of his examples (excepting the patterns late in the book) are canned. Objects and classes exist only to drive the theory behind a pattern home. Few real world examples are given. Admittedly, some patterns are simple to transfer to a real project, but concrete examples of that nature could serve to further cement his point. For example, it's not difficult to see how the Composite pattern would work well for dealing with an XML document, but would there ever be a need for a Visitor object to act on one?

Finally, and in continuation of my last criticism, Zandstra never touches one of the things PHP is used the most for: form handling. Can forms be represented by classes? Could forms be generated by objects (perhaps using a Factory pattern)? What about form validators? Wouldn't the Strategy or Decorator pattern work? Supplementing his online Civilization game and CLI/quiz examples with this would've really put the book over the top.

Still, with that said, PHP Objects, Patterns, and Practice is still a text that gets far more right than wrong. It's definitely a must-buy for those PHP coders looking to write modular code.


It's been about a year and a half since I've read this, I have the first edition, but I think most of what I write is still relevant for this second one.

At the moment, very few php books come close in trying to actually present the language as a real contender for serious and professional web development. This book attempts just that.

PHP has come a long way since its inception, but the teaching material has not really caught up and the community is still pestered with bad code, architecture and practice. This book is an eye opener as it presents php for what it can be: a convenient and flexible tool that, in the right hands, can tough up and allow a programmer to get work done efficiently. It's not to say that php can do everything, but before you blame it as the root of all evil, you should definitely understand how you, the programmer, can work at improving the quality of your code. This text offers some insight into tried and true practices, usually well established in other more mature communities.

There are 3 parts:

The Objects part is a nice introduction to many goodies in the new PHP5 object model (the whole thing is php5 centric).

Some of the topics covered in the section matter more than others imo, since in your practice you'll encounter and will definitely draw some values from them. So pay particular attention to: Autoloading, Exception handling, magic methods, namespaces, reflection.

Because PHP is still a language in search for an identity, it borrows features, coding styles and development philosophy from other languages. Despite the fact that the two are fundamentally very different, Java has heavily influenced PHP's OO design and syntax. However, some of the PHP reimplementation just ended up being "simili" stuff, rather than the real thing. That is, it has the Java flavor, but doesn't actually carry any caffeine. Unfortunately, the book doesn't dig into those details and just serves the Kool-Aid as is.

Another complaint is that you are shown many tools and given a description of how they work, but there is little depth as to when to actually use them. Java and Python programmers borrowing PHP for a project might have an easier time translating this knowledge into actual practice, since their community would have likely previously exposed them to situations these tools were meant for.

If I had to pick one particular topic that I felt was missing from the Objects section, it would be an intro to the SPL. Look for it.

[aside]
If you would allow me some personal and opinionated advices (be forewarned that a lot of these go against the current dogma in PHP):
- private/protected/public: it's definitely useful to understand the _idea_ behind having a public and a private programming interface, but it's a bit of a fallacy to enforce this with actual language constructs in a dynamic technology like PHP, since it doesn't actually provide much benefits to the interpreter. Who are we then "protecting" the code from exactly, the programmer? When other concepts like inheritance get involved, things get even more cumbersome, because PHP is missing some features that allow a technology like Java to get away with it all (method overloading anyone?). An alternative approach is to leave everything public and then follow the widely adopted _convention_ to prefix what is considered private with an underscore. Programmers using your API will get a hint that the $_purifiedData property was probably not meant to be directly accessed, but in case they decide to transgress that rule, they can. If you still insist on enforcing visibility though, then only use the protected and public keywords, forget private altogether.
- inheritance: learn how it works, but most importantly, learn when to avoid it and remember to strive for "Composition over Inheritance" (see Patterns section).
- interfaces: Learn about type-checking and type-hinting and use interfaces for that purpose specifically. You can declare constants within your interfaces, but I'd recommend against also declaring methods in them. It will only constrain your APIs, since PHP doesn't allow method overloading like Java would (this is one thing many PHP so-called experts are completely oblivious about when they merrily sprinkle their code with interfaces). Another route altogether would be to simply stop relying on interfaces and type-hinting and adopt 'duck-typing', an approach more natural to dynamically-typed languages such as Python, Ruby and I dare to say, PHP.
[/aside]

The next section of the book is on Patterns. It's not so much about PHP than it is an attempt at making a less crappy programmer out of YOU. If you're relatively new to programming and you've chosen PHP to make your first steps, please read this section of the book, for the sake of minimizing the damage you certainly will do. This is an intro to better code organization and to the world of design patterns as they can be applied to php. If you've heard of such things as Singleton, Observer, Registry, Controller, MVC and are still scratching your head, this could apply to you to.

The Practice section was a bit of a let down. If the author cares for some suggestions:
- forget CVS: there are currently a number of popular and very good open source SCMs, Git and Mercurial currently leading the pack. At the very least, teach the increasingly outdated SVN, but this book would actually gain some value if you only just mentioned the concept of revision control, without actually naming CVS.
- forget PEAR: instead have a chapter on frameworks, which nicely ties up with what the book tries to teach.