---
layout: post
status: publish
published: true
title: My 2009 Thousand Parsec Proposal
author_login: admin
author_email: github@laudicina.net
wordpress_id: 31
wordpress_url: http://alanp.ca/blog/?p=31
date: '2009-05-04 02:39:35 -0400'
date_gmt: '2009-05-04 06:39:35 -0400'
categories:
- GSoC
tags:
- GSoC
- thousand parsec
comments: []
---
I mentioned previously that I would be posting my complete proposal to this blog. Today, I have gone ahead with that and it is viewable in this post. Throughout the summer as I become more acclimated to Thousand Parsec and the Google Summer of Code process I will be posting regarding possible areas for improvement for this proposal.

## Missile and Torpedo Wars (MTSec)

### Summary

In this Google Summer of Code project, I plan to complete the MTSec ruleset, ultimately delivering a working and enjoyable ruleset to tpserver-cpp. This second milestone game is meant to be a fun game and to exercise the object design capabilities of the Thousand Parsec framework.

### Proposal

**What I plan to do:**

I plan to deliver to the Thousand Parsec project, a working implementation of the MTSec ruleset by the end of the summer break. To make sure that this ruleset is fun I plan on playtesting all new features at every stage of development. Should something hinder the playability of this ruleset, I will discuss that with the mentor(s) immediately and suggest changes to the specification. During this time I plan to post daily to weekly reports of my progress on a blog that will be setup should I get accepted. A full time line is outlined below.

**Why this is important:**

This milestone game is important because it expands what is possible with the first milestone ruleset, Minisec. This game will be fun, exciting and is built to show off newer features of the Thousand Parsec framework. Completing this ruleset is important to the future of Thousand Parsec because it provides a good reference for future, more advanced, rulesets.

##Timeline:

###Now – April 30:

*   As time permits, I plan on contributing patches to Thousand Parsec.
	*   This process has already began with a patch being committed: Issue#74.
*   Setup a development environment on my workstation.
*   Familiarize myself with the code base and standard coding conventions.

###May 1 - May 23:
*   During this time I plan to familiarize myself with the Thousand Parsec framework.
*   Study the C++ server and protocol library.
*   Study various rulesets to give myself a good idea of standard implementations.
*   Study llnz's “Ruleset development with tpserver-cpp” to gain a better understanding of the Thousand Parsec framework.
*   Study and gain advanced knowledge of the current MTSec implementation. Approaching 40,000 lines, the current ruleset will take some time to study.

###May 24 – June 23, Milestone #1:
*   Deliver a working implementation of the MTSec framework.
*   Finish all of the remaining components.
*   While browsing the code I have not found any references yet to the varioius components that make up the ship, this includes:
	*   Launch Tube
    *   Missile Rack
    *   Torpedo Rack
    *   Armor
    *   Colonisation Module
*   At this stage all ship configurations using the components should be feasible.

###June 24 – July 10, Milestone #2:
*   This iteration will support a large portion of the MTSec ruleset.
*   This iteration will include the association between missile designs and the responding missile shop component.
*   The second milestone will include a primitive combat engine.
*   At this stage the game should be playable and somewhat enjoyable. Combat will be possible.

###July 11 – August 9, Milestone #3:
*   This iteration will include a complete, working, fun and playable MTSec ruleset. Will include such things as:
    *   Hit points for ships.
    *   Damange from explosions.
*   This includes a full combat engine.
*   At this stage the game will be complete, full featured and playable.

###August 10-August 17:
*   “Pencil Down Date”
*   This week will be used for cleaning up code, updating documentation and verify various test cases.
*   During this time, I am hopeful we can roll the new MTSec ruleset into the next release.

##Deliverables

When this project has been completed it will consist of a full MTSec ruleset module for the tpserver-cpp. This will include full single player support. Single player support will be available. The XML description for single player support of the ruleset will be kept current as work on MTSec progresses. An AI client will not be part of my deliverables, but I will keep AI accessibility in mind during the development of this ruleset.

My plan is to deliver this ruleset by the end of Summer of Code. In the unlikely event that this ruleset is not delivered by the end of summer break, I still plan on being a part of the Thousand Parsec development team. This means that I will be working throughout the school semester as time allows to finish any outstanding issues.

##Maintenance

Since the MTSec ruleset is a core ruleset, it is very important that this code stay manageable. To maintain the code I plan to make good use of documentation, both in spec and comments throughout the progression of this ruleset. I believe that the docs created, updated and maintained by myself throughout this project will give any interested developers a SOLID base to continue or expand my work.

##Availability

I plan to work on this project 4-8 hours per day (25-45 hours per week), mostly based in the Eastern Time zone's afternoon. This will include various weekends as well as weekdays. I plan to take one day off per week to enjoy the weather, but I plan on being very dedicated to the project. I do not plan on taking any classes during the Summer semester. I do have a part time job at a local internet provider, but the hours are extremely flexible.

##Contingency Plan

I plan on maintaining my code and my upcoming development blog in such a way that if some emergency should occur, it would not be very difficult for another programmer to pick up from where I have left off. The thorough documentation that I leave behind will be of great use should this unexpected event occur.

##Myself

I am a senior student at Wayne State University in Detroit, Michigan, USA. I commute to school every day from Windsor, Ontario, Canada. My future plans include pursuing a PhD. I founded the Windsor UNIX Users Group, which meets monthly in various locations around the Windsor, Ontario area. During the summer of 2008 I was involved in the joint Wayne State-University of Michigan Trading Agent Competition – Procurement Challenge (http://www.sics.se/tac/page.php?id=13). In the past I have volunteered for Daemon News and have committed various ports to the FreeBSD port tree. I enjoy playing various 4X games when time allows, most notably civilization.
