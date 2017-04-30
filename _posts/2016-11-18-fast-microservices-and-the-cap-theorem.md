---
layout: post
title: "Fast Microservices and the CAP theorem"
date: 2016-11-18 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

When I was young I thought the fastest applications in the universe were coded in Assembly, C and C++ by mythical bearded software engineers. In reality, a visual basic application making smart decisions about when to do I/O calls can be faster than any C application that does too much I/O.

## Did I just say Visual Basic can be faster than C++?

Indeed I have and it's easy to understand why. How long does it take to read something from the processor cache? Not much, right? This is where assembly, c and perhaps c++ to some extent could optimise the execution time. Now how long does it take to open a TCP connection, authenticate to a database, run a query and retrieve some data? Well, a lot more than reading from cache or ram. The database I/O is everything in low latency and this post is about how to get rid of I/O from your Microservices.

## Understanding the CAP theorem

It's an acronym created by a computer science professor. It stands for Consistency, Availability and Partitioning. The theorem states that it is impossible for a distributed system to provide all of these three guarantees simultaneously. Now giving that we are talking about Microservices we are already picking Partition out of the CAP theorem. We can only choose from Availability and Partitioning or Consistency and Partitioning.

Consistency: every request receives the most recent write or an error

Availability: every request receive a non-error response

Partitioning: the system continues to operate if network errors between nodes occur

## Access by Value Pattern

![access by value pattern]({{ site.url }}/images/byvalue.png)

Above is an example of a microservice that reads messages from a queue and then maps the data into a SQL database. This is the simplest way of feeding a microservice with data. You give it the data it needs and you let it do its work. 

The problem with this approach is if your service is asynchronous like in the picture above then you never know when it's going to run and pick up the message. What if the data in the message has changed by the time the service runs? The pitfall of the Access by Value Pattern is that it sacrifices Consistency.

## Access by Reference Pattern

![access by value pattern]({{ site.url }}/images/byreference.png)

In the picture above something changed. Our microservice still has a connection to a SQL database where it maps data to but now also has a connection to a NoSQL database. This is because this time our service will be fed with just a reference to the data, not the actual data itself, and it will then find out what the current state of the data is.

Now consistency has been maintained and the service will always have the latest version of data. Sounds great? Not really. We just added a point of failure and possibly doubled the execution time of our microservice.

## Access by Freshness Pattern

![access by value pattern]({{ site.url }}/images/byfreshness.png)

Now comes how to have the best of both worlds. This time our microservice will be fed with both the value of the data and also a reference to it. We then set an amount of time for how long the value of the data is fresh. If the data isn't fresh we get the latest version using the reference.

## Final thoughts

Fortunately just like your Microservices don't just fail, but instead, they handle fail, you can have Microservices that handle the CAP theorem differently given the situation. In this post, we looked at some cool design patterns and thus how we can cut down on the database I/O.