---
layout: post
status: publish
published: true
title: Export Google Chrome passwords to Keepass
author:
  display_name: alanp
  login: admin
  email: github@laudicina.net
  url: ''
author_login: admin
author_email: github@laudicina.net
wordpress_id: 211
wordpress_url: http://alanp.ca/blog/?p=211
date: '2011-01-01 14:52:29 -0500'
date_gmt: '2011-01-01 18:52:29 -0500'
categories:
- Software
tags:
- chrome
- chromium
- keepass
- keepassx
- keepassdroid
- google chrome
- google chromium
- ruby
comments:
- id: 2376
  author: Palla Ramarao
  author_email: rama.geek@gmail.com
  author_url: http://www.techlikes.com
  date: '2012-05-13 08:34:00 -0400'
  date_gmt: '2012-05-13 12:34:00 -0400'
  content: |-
    I found this article on the web which does the same, but using a tool and can be used for any browser.

    http:&#47;&#47;www.howtogeek.com&#47;70801&#47;how-to-import-your-saved-browser-passwords-into-keepass&#47;&nbsp;
- id: 2464
  author: Rick Dicaire
  author_email: kritek@gmail.com
  author_url: ''
  date: '2012-08-05 13:51:00 -0400'
  date_gmt: '2012-08-05 17:51:00 -0400'
  content: While I was able to export Chrome passwords, KeePass 1.23 Portable doesn't
    appear to import the resultant XML file. No error messages. Using the VariousImport
    plugin. Any ideas on what to check?
- id: 2465
  author: Jared Forsyth
  author_email: jared@jaredforsyth.com
  author_url: http://jaredforsyth.com/
  date: '2013-04-19 13:27:00 -0400'
  date_gmt: '2013-04-19 17:27:00 -0400'
  content: ":( didn't work for me..."
---
<p>I have recently been complementing the power of <a href="http:&#47;&#47;keepass.info">Keepass<&#47;a> with <a href="http:&#47;&#47;www.dropbox.com">Dropbox<&#47;a>, which allows me to share and access my logins and passwords anywhere with an internet connection while still storing them in a secure manner. &nbsp;Thanks to the&nbsp;<a href="http:&#47;&#47;www.keepassdroid.com&#47;">KeepassDroid<&#47;a> application, this even includes my phone.</p>
<p>Since I began using Keepass, I have been looking for a way to import those pesky web application passwords into Keepass. &nbsp;Since I have a different login and password for essentially every site I visit, managing and remembering these has been a huge problem in the past. With multiple hundreds of unique login&#47;password combinations, doing this by hand was not an option. &nbsp;This morning the problem came to a head and I decided to do something about it.</p>
<p>Since Keepass allows importation from it's own XML format, the building blocks for an export&#47;import were already there. I have been learning Ruby lately, so I decided I would whip up a quick script to export my Chrome passwords.</p>
<p>After a bit of hacking, I finished chrome2keepass this morning and you can find it at its <a href="https:&#47;&#47;github.com&#47;alanpca&#47;chrome2keepass">Github Repository<&#47;a>.</p>
