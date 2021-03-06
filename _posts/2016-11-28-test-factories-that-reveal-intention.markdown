---
layout:     post
title:      Test factories that reveal intention
author:     Rod Caldas
tags: 		TDD Test Factory Builder Pattern
category:  software-engineering
---
<!-- Start Writing Below in Markdown -->
I've been creating test factories and I always think they are hard to read. Recently I have been reading a book called Growing Object-Oriented Software Guided by Tests. This gave me the idea of applying the Builder pattern to my test factory itself. Now was this a good idea or am I over complicating this? See for yourself and decide.

Below is my test case factory built with the Builder pattern:

<script src="https://gist.github.com/kaldas/559454d9daea1d5598863684a2d67c2f.js"></script>

Below is an example of an execution of this factory:

![test factory example]({{ site.url }}/img/idverificationtest.PNG)

Now should I use the Builder pattern in every test factory? Probably not but when dealing with creating complex objects it is definitely a good idea.