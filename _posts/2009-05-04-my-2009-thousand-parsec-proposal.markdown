---
layout: post
status: publish
published: true
title: My 2009 Thousand Parsec Proposal
author:
  display_name: alanp
  login: admin
  email: github@laudicina.net
  url: ''
author_login: admin
author_email: github@laudicina.net
excerpt: "I mentioned previously that I would be posting my complete proposal to this
  blog. Today, I have gone ahead with that and it is viewable in this post.&nbsp;
  Throughout the summer as I become more acclimated to Thousand Parsec and the Google
  Summer of Code process I will be posting regarding possible areas for improvement
  for this proposal.\r\n"
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
<p>I mentioned previously that I would be posting my complete proposal to this blog. Today, I have gone ahead with that and it is viewable in this post.&nbsp; Throughout the summer as I become more acclimated to Thousand Parsec and the Google Summer of Code process I will be posting regarding possible areas for improvement for this proposal.<br />
<a id="more"></a><a id="more-31"></a></p>
<h3><strong>Missile and Torpedo Wars (MTSec)<br />
<&#47;strong><&#47;h3></p>
<h2><strong>Summary<br />
<&#47;strong><&#47;h2><br />
In this Google Summer of Code project, I plan to complete the MTSec ruleset, ultimately delivering a working and enjoyable ruleset to tpserver-cpp.&nbsp; This second milestone game is meant to be a fun game and to exercise the object design capabilities of the Thousand Parsec framework.</p>
<h2><strong>Proposal<&#47;strong><&#47;h2><br />
<span><strong>What I plan to do:<&#47;strong><&#47;span></p>
<p>I plan to deliver to the Thousand Parsec project, a working implementation of the MTSec ruleset by the end of the summer break.&nbsp; To make sure that this ruleset is fun I plan on playtesting all new features at every stage of development.&nbsp; Should something hinder the playability of this ruleset, I will discuss that with the mentor(s) immediately and suggest changes to the specification.&nbsp; During this time I plan to post daily to weekly reports of my progress on a blog that will be setup should I get accepted.&nbsp; A full time line is outlined below.</p>
<p><span><strong>Why this is important:<&#47;strong><&#47;span></p>
<p>This milestone game is important because it expands what is possible with the first milestone ruleset, Minisec.&nbsp; This game will be fun, exciting and is built to show off newer features of the Thousand Parsec framework.&nbsp; Completing this ruleset is important to the future of Thousand Parsec because it provides a good reference for future, more advanced, rulesets.</p>
<p><span><strong>Time line:<br />
<&#47;strong><&#47;span></p>
<p><strong>Now &ndash; April 30:<&#47;strong></p>
<ul>
<li>As time permits, I plan on contributing patches to Thousand Parsec.
<ul>
<li>This process has already began with a patch being committed: Issue#74.<&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>Setup a development environment on my workstation.<&#47;li>
<li>Familiarize myself with the code base and standard coding conventions.<&#47;li><br />
<&#47;ul><br />
<strong>May 1&nbsp; - May 23:<br />
<&#47;strong></p>
<ul>
<li>During this time I plan to familiarize myself with the Thousand Parsec framework.<&#47;li>
<li>Study the C++ server and protocol library.<&#47;li>
<li>Study various rulesets to give myself a good idea of standard implementations.<&#47;li>
<li>Study llnz's &ldquo;Ruleset development with tpserver-cpp&rdquo; to gain a better understanding of the Thousand Parsec framework.<&#47;li>
<li>Study and gain advanced knowledge of the current MTSec implementation.&nbsp; Approaching 40,000 lines, the current ruleset will take some time to study.<&#47;li><br />
<&#47;ul><br />
<strong>May 24 &ndash; June 23, Milestone #1:<br />
<&#47;strong></p>
<ul>
<li>Deliver a working implementation of the MTSec framework.<&#47;li>
<li>Finish all of the remaining components.
<ul>
<li>While browsing the code I have not found any references yet to the varioius components that make up the ship, this includes:<&#47;li>
<li>Launch Tube<&#47;li>
<li>Missile Rack<&#47;li>
<li>Torpedo Rack<&#47;li>
<li>Armor<&#47;li>
<li>Colonisation Module<&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>At this stage all ship configurations using the components should be feasible.<&#47;li><br />
<&#47;ul><br />
<strong>June 24 &ndash; July 10, Milestone #2:<&#47;strong></p>
<ul>
<li>This iteration will support a large portion of the MTSec ruleset.<&#47;li>
<li>This iteration will include the association between missile designs and the responding missile shop component.<&#47;li>
<li>The second milestone will include a primitive combat engine.<&#47;li>
<li>At this stage the game should be playable and somewhat enjoyable.&nbsp; Combat will be possible.<&#47;li><br />
<&#47;ul><br />
<strong>July 11 &ndash; August 9, Milestone #3:<&#47;strong></p>
<ul>
<li>This iteration will include a complete, working, fun and playable MTSec ruleset.&nbsp; Will include such things as:
<ul>
<li>Hit points for ships.<&#47;li>
<li>Damange from explosions.<&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>This includes a full combat engine.<&#47;li>
<li>At this stage the game will be complete, full featured and playable.<&#47;li><br />
<&#47;ul><br />
<strong>August 10-August 17:<br />
<&#47;strong></p>
<ul>
<li>&ldquo;Pencil Down Date&rdquo;<&#47;li>
<li>This week will be used for cleaning up code, updating documentation and verify various test cases.<&#47;li>
<li>During this time, I am hopeful we can roll the new MTSec ruleset into the next release.<&#47;li><br />
<&#47;ul><br />
<strong>Deliverables<&#47;strong></p>
<p>When this project has been completed it will consist of a full MTSec ruleset module for the tpserver-cpp.&nbsp; This will include full single player support.&nbsp; Single player support will be available. The XML description for single player support of the ruleset will be kept current as work on MTSec progresses.&nbsp; An AI client will not be part of my deliverables, but I will keep AI accessibility in mind during the development of this ruleset.</p>
<p>My plan is to deliver this ruleset by the end of Summer of Code.&nbsp; In the unlikely event that this ruleset is not delivered by the end of summer break, I still plan on being a part of the Thousand Parsec development team.&nbsp; This means that I will be working throughout the school semester as time allows to finish any outstanding issues.</p>
<p><strong>Maintenance<&#47;strong></p>
<p>Since the MTSec ruleset is a core ruleset, it is very important that this code stay manageable.&nbsp; To maintain the code I plan to make good use of documentation, both in spec and comments throughout the progression of this ruleset.&nbsp; I believe that the docs created, updated and maintained by myself throughout this project will give any interested developers a SOLID base to continue or expand my work.</p>
<p><span><strong>Availability<br />
<&#47;strong><&#47;span></p>
<p>I plan to work on this project 4-8 hours per day (25-45 hours per week), mostly based in the Eastern Time zone's afternoon.&nbsp; This will include various weekends as well as weekdays.&nbsp; I plan to take one day off per week to enjoy the weather, but I plan on being very dedicated to the project.&nbsp; I do not plan on taking any classes during the Summer semester.&nbsp; I do have a part time job at a local internet provider, but the hours are extremely flexible.</p>
<p><span><strong>Contingency Plan<br />
<&#47;strong><&#47;span></p>
<p>I plan on maintaining my code and my upcoming development blog in such a way that if some emergency should occur, it would not be very difficult for another programmer to pick up from where I have left off.&nbsp; The thorough documentation that I leave behind will be of great use should this unexpected event occur.</p>
<p><span><strong>Myself<br />
<&#47;strong><&#47;span></p>
<p>I am a senior student at Wayne State University in Detroit, Michigan, USA.&nbsp; I commute to school every day from Windsor, Ontario, Canada.&nbsp; My future plans include pursuing a PhD.&nbsp; I founded the Windsor UNIX Users Group, which meets monthly in various locations around the Windsor, Ontario area.&nbsp; During the summer of 2008 I was involved in the joint Wayne State-University of Michigan Trading Agent Competition &ndash; Procurement Challenge (http:&#47;&#47;www.sics.se&#47;tac&#47;page.php?id=13).&nbsp; In the past I have volunteered for Daemon News and have committed various ports to the FreeBSD port tree.&nbsp; I enjoy playing various 4X games when time allows, most notably civilization.</p>
