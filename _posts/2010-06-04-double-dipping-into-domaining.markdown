---
layout: post
status: publish
published: true
title: Double Dipping into Domaining
author:
  display_name: alanp
  login: admin
  email: github@laudicina.net
  url: ''
author_login: admin
author_email: github@laudicina.net
wordpress_id: 136
wordpress_url: http://alanp.ca/blog/?p=136
date: '2010-06-04 01:33:44 -0400'
date_gmt: '2010-06-04 05:33:44 -0400'
categories:
- Software
tags: []
comments: []
---
<p>When I first read <a href="http:&#47;&#47;ianab.com&#47;log&#47;">Andrew Badr<&#47;a>'s post on his <a href="http:&#47;&#47;ianab.com&#47;log&#47;1&#47;my-dip-into-domaining&#47;">tests with domain squatting^W speculation<&#47;a>, I was immediately interested in the methods that he used. &nbsp;Having checked out <a href="http:&#47;&#47;www.namepros.com&#47;">multiple<&#47;a> <a href="http:&#47;&#47;www.snapnames.com&#47;">domain<&#47;a> <a href="http:&#47;&#47;www.dnforum.com&#47;">speculation<&#47;a> websites in the past, I knew that there were some improvements to be had in the offerings that people put forth.</p>
<p>Coincidentally, I have been reading up on Python lately and have become pretty interested in the language. &nbsp;For my first script implementation, I decided to explore the 4,4 space in English word .com domains. &nbsp;I like this space because it is pretty common (facebook), and I believed that with so many possibilities there would be some great names available.</p>
<p><a href="http:&#47;&#47;ianab.com&#47;log&#47;">Andrew<&#47;a> used a method that included some manual work, which I wanted to avoid. &nbsp;I quickly found an English dictionary online and used the grep pattern "^....$" which would work fine for my simple case. &nbsp;I ended up with 3903 4-letter English words. &nbsp;This space (3903^2) was far too large to start sending queries out, and also too large to manually edit. &nbsp;What to do?</p>
<p>I quickly decided that trends on each word was the way to go, and obtained some statistics on how common each word was. &nbsp;After inserting each word and it's relevance into a simple <a href="http:&#47;&#47;www.mysql.com&#47;?bydis_dis_index=1">MySQL<&#47;a> table, I was ready to begin hammering away to see what was available for registration.</p>
<p>Once I had this data, I stored a reference to each word and the combined relevance of the prefix and&nbsp;suffix&nbsp;in another table of the database. &nbsp;According to my heuristics, I had the list of the most relevant domains with 2 four character words possible.</p>
<p>The results are pretty interesting, with many (what I would consider) top-term .com domains available. &nbsp;Here are some of my favorites quickly off of the file (inb4registration):</p>
<ul>
<li>thisholy.com<&#47;li>
<li>thatecho.com<&#47;li>
<li>homehide.com<&#47;li>
<li>homemeet.com<&#47;li>
<li>havethem.com<&#47;li><br />
<&#47;ul><br />
Can we do better? &nbsp;Like Andrew, I also stored a counter for each time a 4-letter word was either a prefix or a suffix. &nbsp;Tomorrow I will try using this information as a factor to my current heuristics. &nbsp;I think the most major improvement possible would be to distribute these requests over a few different boxes (it's definitely MapReduceable). &nbsp;If you have any methods for improvement, I would like to hear them as well. &nbsp;Leave a note in the comments section.</p>
<p>If there's any interest, I will post my full list &nbsp;(it's hosted on my home computer). &nbsp;There are massive possibilities to explore the 3,4 space and 4,3 space, I would love to hear from you if you begin your exploration in these spaces.</p>
