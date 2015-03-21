---
layout: post
status: publish
published: true
title: Announcing Viral Landing Page
author_login: admin
author_email: github@laudicina.net
wordpress_id: 217
wordpress_url: http://alanp.ca/blog/?p=217
date: '2011-03-02 01:17:03 -0500'
date_gmt: '2011-03-02 05:17:03 -0500'
categories:
- Software
- Startups
tags:
- viral landing page open source bsd license
comments:
- id: 2183
  author: Neda
  author_email: neda_golshan@hotmail.com
  author_url: ''
  date: '2011-08-05 12:23:00 -0400'
  date_gmt: '2011-08-05 12:23:00 -0400'
  content: |-
    Hi,
    I have read through githib about this source code. But I am not a ruby programmer. Can you give me some assistant to use thsi code as my landing page. I reviewed launchrock and that looks great. I do appreciate your assistance! GREAT DAY! :)
---
I have been working on a few projects which require a landing page over the past couple of months, and this has come to the forefront of my thoughts more recently. As a Startup Weekend alumnus, I was pretty excited to see that [launchrock](http://www.launchrock.com) was fully launched and gaining quite a bit of traction. One problem, though, is that I would have to sign up for each project and then promote the links. I don't like to post too many links on my [Twitter](http://twitter.com/alanpca) and/or Facebook accounts, so I decided against this. If you're not familiar with the concept, here is an excerpt from the description on the Github repo:

> When a user submits their e-mail address, it will immediately be recorded to the
local database. The user will then be shown "sharing" icons from Facebook and
Twitter. Each successful click or referral will be recorded to the database for
that user. This makes it easier for you to allow earlier access to people who are
driving traffic to your site.

The next route was to implement something similar, which I did over the past couple of days. The result is [viral-landing-page](https://github.com/alanpca/viral-landing-page) (very original name, I know), which can be found in my [Github repositories](https://github.com/alanpca) immediately. Viral-landing-page was written in Ruby on Rail because, well, I love the framework. For Javascript, I chose jQuery for similar reasons.

Viral-landing-page far from polished, but it should be good enough to begin using immediately. I chose to license it under the [BSD open source license](https://github.com/alanpca/viral-landing-page/blob/master/LICENSE), which is quite permissive. While it isn't required, I'd like to know who is using this software (and early access to your startup =D). You can comment on this blog post, or contact me via any other methods. I will be actively adding features (maybe an admin viewer) as I use the project more and more for my own needs. Feel free to fork and push back any changes!
