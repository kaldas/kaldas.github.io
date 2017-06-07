---
layout: post
title: "Understanding Cross-cutting concerns and Domain code"
date: 2016-11-10 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

Many years ago I found a wise general rule called DRY. This is an acronym for Don't-Repeat-Yourself. It's easy to see why repeating behaviour around a code base will make it rigid to change. The outcome of doing DRY is that we end up with a lot of abstractions that can be shared and is this always a good idea? Well, not entirely and let's find out why...

## Understanding Cross-cutting concerns

They are the concerns that are shared throughout the application. They are most likely technical tasks and this is where having shared libraries with their own release pipeline worked really well for me.

When I joined WorldRemit the first task that I picked up involved changing how Logging was performed. Now tweaking Log4net was easy. The hard part of distributing the changes to some 20 projects. This is when we created a NuGet package that could be easily distributed and versioned. We ended up creating more of these packages and other teams started using and contributing to them. Alas identifying our cross-cutting concerns was very helpful to us.

Below is how our pipeline looks like in Team City:

![microservices extended from base]({{ site.url }}/images/pipeline.png)

## Understanding Domain concerns

Not all technical tasks are cross-cutting concerns and this is something that has been biting me on daily basis. I have been working with some cloud microservices which all derive from the same base service. This is done via a project reference. The problem comes when Domain specific behaviour is necessary. 

![microservices extended from base]({{ site.url }}/images/service_base.png)

What happens given the above architecture when we try to implement different strategies for circuit breakers? Should they go on the upstream code? Dependency Injection? Create wrappers? Extension methods? So very easily something simple became complex...

Now don't get me wrong because shared code does work very well for internal technical tasks, like Logging or accessing a NoSQL database but when Domain specific behaviour is involved, it doesn't work well.

## Understanding the value of simple procedural code

In the book Refactoring by Martin Fowler and Kent Beck, the authors propose that code repetition is the foundation of all abstractions. This is because repeated code indicates the right moment of when to jump from the simplest procedural code to an abstraction. The problem of introducing design patterns head on is that usually, it overcomplicates what could have been a simple, elegant, intention revealing solution.

## Final thoughts

Shared code between projects is good for technical tasks (i.e client to connecting to Azure databases or Logging). Shared code between projects is bad when there is domain specifc behaviour involved. Shared code within the same project is generally good - even if it contains domain specific behaviour.
