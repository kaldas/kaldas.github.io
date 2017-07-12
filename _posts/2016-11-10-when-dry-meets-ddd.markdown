---
layout:     post
title:      When DRY meets DDD
author:     Rod Caldas
tags: 		DRY principle ddd software engineering
category:  software-engineering
---
<!-- Start Writing Below in Markdown -->

Many years ago I found a very wise principle called DRY. This is an acronym for Don't-Repeat-Yourself. It's easy to see why repeating behaviour around a code base will make it rigid to change. The outcome of doing DRY is that we end up with a lot of abstractions that can be shared and is this always a good idea? Well, not entirely and let's find out why...

## Why simple procedural code is important

There is a book that I like very much called "Refactoring: Improving the Design of Existing Code" by Martin Fowler and Kent Beck. This book will show you some smells and how you can refactor them using design patterns and this is great but this is not what I like the most about this book. The best part of this book for me is when they teach you how to think. My favourite part is when they discuss the right moment of introducing a design pattern. They propose that code repetition is the foundation of all abstractions. This is because repeated code indicates the right moment of when to jump from the simplest procedural code to an abstraction. I believe this book was written in the 1990s before TDD was invented so if you are doing proper TDD i.e the simplest code that will make the test pass then this should be happening naturally. The problem of introducing design patterns head on is that usually, it overcomplicates what could have been a simple, elegant, intention revealing solution.

Now if you did all of the above correctly you should then be getting some repeated code. When and how should you DRY it? This is where Domain Driven Design can help you. In DDD there is a concept of a Cross-cutting concerns and Domain concerns. In the rest of this post we will look at both of them.

## Understanding Cross-cutting concerns

They are the concerns that are shared throughout the application. They are most likely technical tasks and this is where having shared libraries with their own release pipeline worked really well for me.

When I joined WorldRemit the first task that I picked up involved changing how Logging was performed. Now tweaking Log4net was easy. The hard part of distributing the changes to some 20 projects. This is when we created a NuGet package that could be easily distributed and versioned. We ended up creating more of these packages and other teams started using and contributing to them. Alas identifying our cross-cutting concerns was very helpful to us.

Below is how our pipeline looks like in Team City:

![microservices extended from base]({{ site.url }}/img/pipeline.png)

## Understanding Domain concerns

Not all technical tasks are cross-cutting concerns and this is something that has been biting me on daily basis. I have been working with some cloud microservices which all derive from the same base service. This is done via a project reference. The problem comes when Domain specific behaviour is necessary. 

![microservices extended from base]({{ site.url }}/img/service_base.png)

What happens given the above architecture when we try to implement different strategies for circuit breakers? Should they go on the upstream code? Dependency Injection? Create wrappers? Extension methods? So very easily something simple became complex...

Now don't get me wrong because shared code does work very well for internal technical tasks, like Logging or accessing a NoSQL database but when Domain specific behaviour is involved, it doesn't work well.

## Final thoughts

Shared code between projects is good for technical tasks (i.e client to connecting to Azure databases or Logging). Shared code between projects is bad when there is domain specifc behaviour involved. Shared code within the same project is generally good - even if it contains domain specific behaviour.
