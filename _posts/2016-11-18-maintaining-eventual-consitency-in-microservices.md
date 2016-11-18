---
layout: post
title: "Maintaining eventual consistency in Microservices"
date: 2016-11-18 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

I got an interesting A2A on Quora which touched the CAP theorem. Their question was: Is it a typical pattern to design a microservice to receive an async event indicating that it then should call a rest endpoint to get the real data?

## My answer was...

If maintaining eventual consistency is a requirement then yes. Would the microservice you described be used entirely in an internal system? Probably. Would Rest be the best way to do this? Probably not.

I can see a Good, a Bad and an Ugly implementation of this.

Warning: no Netflix examples have been used in the making of this post.

## The Good

When the service you described may run in a future moment in time and you have to maintain eventual consistency. An example of this would be a store with a ShipOrder microservice that is fed once an order is ready to be shipped. Now bear in mind this store doesn’t ship orders during weekends and religious holidays. The edge case is when a customer changes the shipping address after the order was made ready to be shipped. The solution with the said implementation would be providing the ShipOrder with just an ‘Id’ and then letting it find what the current state of the order is when it runs.

## The Bad

When there is no reason to justify the architecture above. It’s past the time when software engineers could use design patterns because “ its cool “. Say we have a CalculateOrder microservice that is always available and receives an order and calculates the combined price of these items. It would make no sense whatsoever to use the said architecture.

## The Ugly

Rolling back a few years in time when Domain Driven Design started to gain traction and people were doing the onion architecture (because it makes you cry when you cut through its layers) then it was common to expose the domain via rest. An example of this would be: Web site > REST API > Domain. Now no need in 2016 to describe the deficiencies of this.