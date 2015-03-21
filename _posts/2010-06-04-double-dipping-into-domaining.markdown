---
layout: post
status: publish
published: true
title: Double Dipping into Domaining
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
When I first read [Andrew Badr](http://ianab.com/log/)'s post on his [tests with domain squatting^W speculation](http://ianab.com/log/1/my-dip-into-domaining/), I was immediately interested in the methods that he used. Having checked out [multiple](http://www.namepros.com/)[domain](http://www.snapnames.com/)[speculation](http://www.dnforum.com/) websites in the past, I knew that there were some improvements to be had in the offerings that people put forth.

Coincidentally, I have been reading up on Python lately and have become pretty interested in the language. For my first script implementation, I decided to explore the 4,4 space in English word .com domains. I like this space because it is pretty common (facebook), and I believed that with so many possibilities there would be some great names available.

[Andrew](http://ianab.com/log/) used a method that included some manual work, which I wanted to avoid. I quickly found an English dictionary online and used the grep pattern "^....$" which would work fine for my simple case. I ended up with 3903 4-letter English words. This space (3903^2) was far too large to start sending queries out, and also too large to manually edit. What to do?

I quickly decided that trends on each word was the way to go, and obtained some statistics on how common each word was. After inserting each word and it's relevance into a simple [MySQL](http://www.mysql.com/?bydis_dis_index=1) table, I was ready to begin hammering away to see what was available for registration.

Once I had this data, I stored a reference to each word and the combined relevance of the prefix andsuffixin another table of the database. According to my heuristics, I had the list of the most relevant domains with 2 four character words possible.

The results are pretty interesting, with many (what I would consider) top-term .com domains available. Here are some of my favorites quickly off of the file (inb4registration):

*   thisholy.com
*   thatecho.com
*   homehide.com
*   homemeet.com
*   havethem.com

Can we do better? Like Andrew, I also stored a counter for each time a 4-letter word was either a prefix or a suffix. Tomorrow I will try using this information as a factor to my current heuristics. I think the most major improvement possible would be to distribute these requests over a few different boxes (it's definitely MapReduceable). If you have any methods for improvement, I would like to hear them as well. Leave a note in the comments section.

If there's any interest, I will post my full list (it's hosted on my home computer). There are massive possibilities to explore the 3,4 space and 4,3 space, I would love to hear from you if you begin your exploration in these spaces.
