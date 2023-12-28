---
layout: default
title: "Preparing for that first security job - Intro"
date: 2019-01-20 07:27:03 -0500
categories: uncategorized
---

The purpose of this series is to help an aspiring Security professional get their first experience in the field. Each post will give provide discussion and questions to point you in the direction of learning about a topic. The goal is not only to acquire the knowledge but also to build skills in research and self learning.

The importance of self learning will never go away. As you move up the organizational structure the direction and amount of instructions you’re given will become more and more generalized. Once you reach the CISO level the only direction you might receive is “Build or maintain a security program that protects the organization from risk”. It is simply not possible for a college degree or certification to provide all of this knowledge and even if it did you would still have to learn as technology changes.

This series is meant to cover responsibilities you may have in a technical security role such as an Analyst or Engineer:

* Protect: identify existing or potential risks in the environment and take action to reduce the risk to an acceptable level
* Detect: monitor the environment to identify security incidents
* Respond: when there has been a confirmed incident, contain, eradicate and recover from it

(Protect, Detect, and Respond are components of the NIST Cyber Security Framework. Not everyone follows NIST, but if you want to familiarize yourself with how an overall program might look, I suggest reading up on it)

It’s an important note that I said “Risks” and not only “Vulnerability”. You may be asked to identify Vulnerabilities as part of your duties but the overall program should be looking at Risk, which includes the aspects of likelihood of exploitation as well as the impact. As an example, a vulnerability would be if a door to a room which connects to a common area does not have a lock. The room is vulnerable to entry by anyone with relative ease and thus could be considered a Critical vulnerability. However, the amount of risk would depend on whether the room is a cash office or a public restroom.

A another real life example could be the EternalBlue exploit from 2017 which was utilized by WannaCry and other malware. If a Windows system is missing the MS17-010 patch which addresses that vulnerability it can be remotely and completely compromised with relative ease. But what is the risk of this vulnerability existing on a system which only displays a slideshow for digital signage purposes and has no network connection? What if that patch is missing on a Windows domain controller? How does this risk change if the host has a local firewall which blocks access to port tcp/445 ? Figuring out these questions allow you to respond appropriately and prioritize where to spend your energy.

The posts in the coming weeks will examine the three bullet points above in more detail. In the mean time, here’s an article discussing Risk vs. Vulnerability:

[Vulnerability vs. risk: Knowing the difference improves security](https://www.csoonline.com/article/3211443/vulnerability-vs-risk-knowing-the-difference-improves-security.html)

