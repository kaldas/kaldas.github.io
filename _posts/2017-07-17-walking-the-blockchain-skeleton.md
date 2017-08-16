---
layout: post
title: "Walking the blockchain skeleton"
date: 2017-03-17 12:00:00
tags: Hackaton Blockchain Walking Skeleton
category: blockchain
featured_image: /images/cover.jpg
---

Last week I had my first Hackathon with my current employer. We were free to work on any ideas we wanted to and to team up with anyone in the company. We had the Hackathon kickoff at the Churchill War Rooms in Westminster with a very motivating speech from the CEO about how we are directly fighting poverty world wide. I got in a cross functional team with people from almost every engineering team and we picked up bringing blockchain technology to the business.

![mr.robot hacker team]({{ site.url }}/img/fsociety.png)
<center>(My favourite hacker team from Mr.Robot tv series)</center>

Being already a financial institution, we decided to look at blockchain as a ledger for our existing business flow, more like smart contracts, instead of as a crypto currency like Bitcoin. This is when we found about Stellar.

![mr.robot hacker team]({{ site.url }}/img/stellar.jpg)
<center>(the above image is not a Google Ad)</center>

They are a payment scheme built on top of blockchain technology where financial institutions can join as anchor nodes and make the bridge between the real world hard currency/fiat money and the e-money. We started the hackaton with a spike to investigate the feasibility of integrating with stellar and after an hour or so we had already moved some lumens to a wallet. This is when we decided that we would present a walking skeleton of an integration with stellar as our hackaton project.

## The Walking Skeleton

As our hackathon project we decided to present an end to end integration of our platform with stellar. We had a large pool of developers in our group so we decided to go ahead with a walking skeleton. So what is a walking skeleton?

> "A Walking Skeleton is a tiny implementation of the system that performs a small end-to-end function. It need not use the final architecture, but it should link together the main architectural components. The architecture and the functionality can then evolve in parallel." - Alistair Cockburn

This meant creating an api to serve as an adapter between our domain and stellar, a web page where our agents could keep track of debits issued through stellar and another web page where our partners could view credits to their wallets. We also had an android developer in our team so we hooked this up to our android app for demonstration purposes and I was very satisfied with the outcome. Our project finished in the top 3 with the other two being related to fraud detection and fintech aid.

