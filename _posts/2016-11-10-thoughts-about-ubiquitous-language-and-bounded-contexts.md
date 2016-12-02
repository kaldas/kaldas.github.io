---
layout: post
title: "Thoughts about Ubiquitous Language and Bounded-Contexts"
date: 2016-11-10 12:00:00
categories: Software_Engineering
featured_image: /images/cover.jpg
---

Long story short my team was creating a new fraud detection product that had four bounded contexts. The team as a whole had a question about why they couldn't have a generic DTO package and then add project references to it. Isn't avoiding code repetition good?

Well... Not when you wish to avoid corruption between Bounded Contexts. I think the fundamental point of the strategic patterns of DDD is that the Model is a representation of the Ubiquitous Language. So what does this mean? It means that every Bounded Context will have its own Ubiquitous Language.

Also, DTO's are a great place to validate data. Obviously one could argue that all validations should be done within the domain to avoid making it anaemic but I think that is too extreme.

## Now going to practical example...

Many years ago before I moved to London I worked for various firms in Brazil and one of them was the national telephone company. When I worked there I found a great example of Ubiquitous language within bounded contexts and this was the word TELEPHONE.

In the bounded context of the operations department, a telephone was what they installed at customers houses

For the telematic’s department, a telephone meant a number within an area code which was either being a caller or a callee

For finance, a telephone meant a bill to be sent every month

This is why every bounded context has its own ubiquitous language and why the anti-corruption pattern between bounded contexts is so important in domain driven design.