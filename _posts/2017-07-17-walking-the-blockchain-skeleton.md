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

According to Alistair Cockburn who coined the term:

> "A Walking Skeleton is a tiny implementation of the system that performs a small end-to-end function. It need not use the final architecture, but it should link together the main architectural components. The architecture and the functionality can then evolve in parallel."

This is a term coined by Alistair Cockburn to describe the smallest implementation of an end to end functionality in a system.