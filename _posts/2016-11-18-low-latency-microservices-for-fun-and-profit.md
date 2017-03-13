---
layout: post
title: "Low latency Microservices for fun and profit"
date: 2016-11-18 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---
When I was young I thought the fastest applications in the universe were coded in Assembly by mythical bearded software engineers. In reality a visual basic application making the right use of the CAP theorem can be a lot faster than any Asm or C application.

## Did I just say Visual Basic can be faster than Assembly?

Indeed I have and its easy to understand why. How long does it take to read something from the processor cache? Not much, right? This is where assembly, c and perhaps c++ to some extent could optimize the execution time. Now how long does it take to open a tcp connection, authenticate to a database, run a query and retreive some data? Well, a lot more than reading from cache or ram. Database I/O is everything in low latency and this post is about how to get rid of I/O from your Microservices.

## So what is the CAP theorem?

It's an acronym created by a computer science professor. It stands for Consistency, Availability and Partioning. The theorem states that it is impossible for a distributed system to provide all of these three guarantees simultaneously.

But fortunately just like your Microservices don't just fail, but instead, they handle fail, you can have Microservices that handle the CAP theorem differently given the situation.

## Access by Reference, but only when necessary

There are three strategies for feeding asynchronous services with data. The first is feeding them with the actual data they need to process. This is what is called Access by value but very quickly we can see the pitfall of this approach. By being in asynchronous the data can already have changed when the service actually handles it. Therefore sacrificing Consistency over Availability.

The second strategy is called access by reference. This consists of feeding the service with just a reference like an 'Id' and then let it find out the current state of the data when it runs. The problem of this approach is that it adds I/O time and a point of failure.

Now comes the third implementation which is a mix of both of the above. This is done through the concept of Freshness. If the data is fresh then use the value. If its not then access by reference.

## Shared database when using state machines

