---
layout: post
title: "When code repetition is good"
date: 2016-11-10 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

Many years ago I found a very wise general rule called DRY. This is an acronym for Don't-Repeat-Yourself. It's easy to see why repeating behaviour around a code base will make it rigid to change. So code repetition is completely bad? Well, not entirely and let's find out why...

## It's always part of the development process

In the classic book Refactoring by Martin Fowler and Kent Beck, the authors propose that repetition is the foundation of all abstractions. This is because repetition indicates the right moment of when to jump from the simplest procedural code to an abstraction. The problem of introducing design patterns head first is that usually, it overcomplicates what could have been a simple, elegant, intention revealing solution.

## Shared code has side effects on Domain specific behaviour

This is something that has been biting me on daily basis. I have been working with some Azure cloud microservices which all derive from the same service. This is done via a project reference. The problem arises when Domain specific behaviour is necessary. 

An example of the above is implementing different strategies for circuit breakers. Should they go on the upstream code? Dependency Injection? But some Azure libraries haven't got interfaces. Inject wrappers? Extension methods? Very easily something simple became extremely complex...

Now don't get me wrong because shared code does work very well for internal technical tasks, like Logging or accessing a NoSQL database but when Domain specific behaviour is involved, it doesn't work well.

## Shared code can create Boundary corruption

The fundamental point of the strategic patterns of DDD is that the Model is a representation of the Ubiquitous Language. So what does this mean? It means that every Bounded Context will have its own Ubiquitous Language.

Therefore technically every bounded context will have its own building blocks i.e entities, aggregates and value objects. But this still leaves us with our DTO's that live in the Adapter layer - outside our core domain.

Not long ago I was in a team creating a new fraud detection product for banks. There was a lot of repetition in Data Transfer Objects (DTO's) so there was the obvious desire of creating a generic DTO package. Would that have been a good idea?

It depends on how you are mapping your DTO's to your domain. In my experience, DTO's are a great place to perform Domain specific validation before it's mapped into the Domain. This wouldn't be so easy when using a generic library.

## In the end

There is no absolute right or wrong and its best to do what makes sense given the situation.

