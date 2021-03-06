---
layout: post
title: "When DDD and DevOps saved a startup"
author: Rod Caldas
date: 2021-07-10 12:00:00
tags: DDD DevOps FinTech Startup
category: mentoring
featured_image: /images/cover.jpg
---

One time I joined a startup in a weird place. They spent three years building their product before going live, and when they did, it didn't make any sense commercially.

Oh, but customers loved the product? No - they hated it, and their TrustPilot looked like a nuclear bomb hit it.

And the worst of it: they burned $100 mil of investor cash in the process and had nothing to show for, and yes, that's one million dollars times a hundred. That's a lot of money!

**Spoiler alert:** this story has a happy ending! This is the story of how a group of software engineers managed to turn around a failing business by using DDD and DevOps practices.

## How they got to this

They had a crumbling platform. When starting a new engagement, I enjoy quickly learning about the Domain and the codebase, but this was particularly hard. The last dev team didn't use the foundation of Domain-Driven Design when designing their Platform, and the codebase was rigid to change and counterintuitive to understand. I know DDD is hard. I'm not saying everyone should know how to do DDD because you don't really need to know DDD to reap the most benefits from DDD!

The hard stuff like Anti-Corruption Layers, Aggregates, Events, Commands, Repositories are just implementation details, and not every project needs them. Surprisingly this usually comes to mind when people think of DDD!

The three essential aspects of DDD: the Ubiquitous Language, the Bounded Context and the Domain Model are easy to learn. They also bring the most value! These principles enable technologists to build a bridge with domain experts and delegate some tech decisions to business people.

## The business differentiators

This is how the business is going to have an advantage over the competition. This is where it makes sense to build your own intellectual property: because you can make it whatever way you want it, thus earning an advantage over the competition. This is known as the core domain, and it can be beneficial in deciding what to build yourself and what to buy.

![Types of Domains]({{ site.url }}/img/domain_types.png)

Sadly the original dev team had a lot of pressure from the investors to get something out very quickly, and they decided to buy a costly black-box solution to enable their core Domain. They also never gave a step back to build a strong foundation for the Platform. There was no tooling for anything, and everything was configured by point and click!

## Four critical areas of our turnaround strategy

We were given one year to pivot and make the business commercially viable. The team knew it would have to create many new services quickly. We then gave a step back and decided to create a solid foundation that would allow devs to move fast. 

## 1) Domain-Driven Design at the centre of everything

We moved away from the word "Service", and instead, we would have "Contexts". Humans like to anchor their thoughts around words, and this simple change in naming was to make sure they always had the domain model in mind when building a new service.

The ubiquitous language would dictate our bounded contexts. To illustrate this in code, we had UserPersonalIdentity context containing the User's identity as a person. We also had a UserDigitalIdentity context for the stuff the User logs in with. Later on, this was very helpful when onboarding customers from third-party providers who did not have a Digital Identity but had a Personal Identity.

Event Storming was our chosen tool to build a relationship with our stakeholders and flesh out our project. Like a Pizza, there is no right or wrong way to pick ingredients you like. The elements for our Event Storming pizza would be Aggregates, Commands, Events and Policies. After a few sessions, we were able to plan what teams we needed to create and their mission.

![Pizza ingredients]({{ site.url }}/img/pizza_ingredients.png)

## 2) Loose coupling through Event-Driven Architecture

The business had a complex financial domain, and it was prone to needing batch processing to run it like clockwork. A process would trigger an API request somewhere; this would, in turn, be coupled to another request where else and so on. The result of this request chain was some crazy coupling!

We decided rather than pinning API requests to more requests, we would instead use Event-Driven Architecture. The team had a group of some of the most pragmatic software engineers I ever worked with. They thought the added complexity of implementing this architecture would simplify the solution because coupling would be significantly loose.

## 3) Removing Platform as a blocker

We couldn't afford to have much-needed Platform related tickets sitting in someone's queue for weeks. It would derail our entire project. There was a need for a scalable way to quickly spin new Contexts. 

We decided all Infrastructure and Pipelines should be scripted. This was no easy choice given the time constraints and pressure to save this company. It was like starting a long journey somewhere by giving three steps back, but it was a bet we were willing to make.

Infrastructure as code removed all paralysis caused by platform tickets. Pipeline as code cleared all the time wasted in configuring pipelines for new Contexts.

## 4) Creating a framework

We had decided on using Event-Driven architecture, Infrastructure and Pipeline as Code. Now we needed a way to distribute this to different groups of software engineers.

I know Frameworks have a terrible reputation. They are usually seen as a cookie-cutter approach to any problem instead of using the right tool for the job. But we weren't going to use someone else's Framework. Instead, we were going to build our own for this job.

Originally our plan was:
- Create a tool to spin a new project with a new Aggregate, sample Events and basic tests
- Create all docker configuration
- Add Infrastructure automation scripts for any cloud resources
- Add Pipeline automation scripts for this project

This worked really well, and then we created tooling to:

- Add a new aggregate to an existing project
- Update dependencies in a project

## Final Thoughts

After an intense 12 month period, we had decommissioned the old platform, customers were happy, and the organisation was well on track to break even. 

The business became more stable and hired more product managers and delivery managers. Instead of Tech Leads managing the relationship with stakeholders, there would be PMs and DMs. Counterintuitively this had a particularly negative effect on the relationship with stakeholders. They felt their pains stopped being heard, and they got unhappy. People started escalating complaints to their C level executives, and this became a board level issue.

I might be wrong, and I accept my opinion is based only on my personal observation. I believe when Tech Leads were managing stakeholders, it worked so well because they used Domain-Driven Design. The business experts had their hands on the product when moving cards around the Event Storming board. They felt their voices were being heard. They could see what the big picture was and what part of it teams were working on.

The more experienced I get the more I see software engineering is about people than technology.

Note: the pizza analogy might have been stolen from Alberto Brandolini - the creator of event storming
