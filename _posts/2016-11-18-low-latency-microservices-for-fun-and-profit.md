---
layout: post
title: "Low latency Microservices for fun and profit"
date: 2016-11-18 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---
When I was young I thought the fastest applications in the universe were coded in Assembly by mythical bearded software engineers. In reality a visual basic application making the right use of the CAP theorem can be a lot faster than any Asm or C application.

## Did I just say Visual Basic can be much faster than Assembly??

Indeed I have and its easy to understand why. How long does it take to read something from the processor cache? Not much, right? This is where assembly, c and perhaps c++ to some extent could optimize the execution time. Now how long does it take to open a tcp connection, authenticate to a database, run a query and retreive some data? Well, a lot more than reading from cache or ram. In low latency I/O is everything.

## So what is the CAP theorem?

It's an acronym created by a computer science professor. It stands for Consistency, Availability and Partioning. The theorem states that it is impossible for a distributed system to provide all of these three guarantees simultaneously.

But fortunately just like your Microservices don't just fail, but instead, they handle fail, you can have Microservices that handle the CAP theorem differently given the situation.

## Access by Reference, but only when necessary

An example of this would be a store with a ShipOrder microservice that is fed once an order is ready to be shipped. Now bear in mind this store doesn’t ship orders during weekends and religious holidays. The edge case is when a customer changes the shipping address after the order was made ready to be shipped. The solution with the said implementation would be providing the ShipOrder with just a reference i.e an ‘Id’ and then letting it find what the current state of the order is when it runs.


## Shared database when using state machines


