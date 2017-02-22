---
layout: post
title: "Creating intention revealing test factories"
date: 2016-11-28 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

I've been creating test factories and I always think they are hard to read. Recently I have been reading a book called Growing Object-Oriented Software Guided by Tests. This gave me the idea of applying the Builder pattern to my test factory itself. Now was this a good idea or am I over complicating this? See for yourself and decide.

Below is my test case factory built with the Builder pattern:

<script src="https://gist.github.com/kaldas/559454d9daea1d5598863684a2d67c2f.js"></script>

Below is an example of an execution of this factory:

![test factory example]({{ site.url }}/images/idverificationtest.PNG)

Now should I use the Builder pattern in every test factory? Probably not but when dealing with creating complex objects it is definitely a good idea.