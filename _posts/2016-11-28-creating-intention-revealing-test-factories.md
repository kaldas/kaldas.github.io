---
layout: post
title: "Creating intention revealing test factories"
date: 2016-11-28 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

I've been creating test factories and I thought my code was pretty good. Recently I have been reading a book called Growing Object-Oriented Software Guided by Tests and I found a much more intention revealing practice. This is what is called the Builder pattern.

Below is an example of a test factory before being refactored:

<script src="https://gist.github.com/kaldas/227b96dadf074b9ca42f62aa57462d52.js"></script>

Now nothing wrong with the above. Its just not the easiest code to understand what is it doing. Below is an example of an execution of this factory:

![test factory example]({{ site.url }}/images/test_factory_example.png)

Now nothing wrong with the above. Its just not the easiest code to understand what its doing.

