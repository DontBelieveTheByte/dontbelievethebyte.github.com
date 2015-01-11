---
layout: post
category : script
tagline: "An up to date review of the Gang of Four classic"
tags : [perl, script]
---
{% include JB/setup %}

Just a few I've learned over the last few months and taken notes on:
Do One Thing (DOT)
Keep it Simple, Stupid (KISS)
Don't Repeat Yourself (DRY)
Open Closed Principle (OCP) - Classes should be able to be extended without modifying its original behavior.
Single Responsibility Principle (SRP) - Every class should have a single, self-contained responsibility. As a result, classes are often small. A large class typically has multiple responsibility. A small class does not imply a lack of references to other classes used internally.
Dependency Inversion Principle (DIP) - High-level modules should not have low-level modules as a dependency. Details should depend on abstractions, not the reverse. Both often reference the same interface.
Liskov Substitution Principle (LSP) - derivative classes must be able to be substituted for their base class.
Command-query, a class or function should either be a command (action) or a query (return data) but never both.
Interface segregation principle, prefer client specific interfaces over general-purpose or catch-all interfaces
Law of Demeter (LOD) - each module should have limited knowledge of other modules and only with those with which it has high cohesion. "Don't talk to strangers, talk to your friends" Assume as little as possible.
Inversion of Control (IoC) - decouple implementation and execution. Modules should be replaceable. Do not make assumptions, depend on contracts (expect a specific condition on entry, guarantee a certain post-condition, class invariant should be preserved, assumed on entry and guaranteed on exit)
You aren't gonna need it (YAGNI) do not add functionality until deemed necessary. Don't write code with the intention to deprecate. Prefer simple, replaceable, approaches that work over complex functionality that is difficult to replace.
Simple Constructions, objects should be easy to create. Constructors should only initialize members that have an equal lifetime, all others should be set via methods.
Prefer Polymorphism to nested conditional statements
Name interfaces after their functionality
Name classes after interfaces they implement
Cohesion, elements within the same module should have high cohesion, meaning they logically belong together.
Follow standard conventions, design guidelines, naming guidelines, code quality.
Fail early, errors should be thrown as early as possible, when they are detected
Maintain a high level of consistency, naming, patterns, etc.
Prefer explanatory naming conventions over cryptic ones
Vertical Separation, variables and methods should be defined near where they are used. Local variables should be declared directly before they are used and should have a short lifetime. I.e. don't declare variables before they are needed
Stay Positive, negated conditionals can be cryptic and hard to read
Refrain from unnecessary nesting, nested code should either handle specific situations or when a task is highly specific.
Encapsulation, encapsulate conditionals and data, refrain from accessing raw class data.
Simple tasks should have simple implementation and use
Ideas should be represented directly
Independent ideas should be independent of one another
Similar ideas should share a common interface and derive from the same base
Prefer local variables over global variables
Abstract, but don't generalize or gloss over functionality

