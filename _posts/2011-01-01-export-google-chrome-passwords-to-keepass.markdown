---
layout: post
status: publish
published: true
title: Export Google Chrome passwords to Keepass
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
I have recently been complementing the power of [Keepass](http://keepass.info) with [Dropbox](http://www.dropbox.com), which allows me to share and access my logins and passwords anywhere with an internet connection while still storing them in a secure manner. Thanks to the [KeepassDroid](http://www.keepassdroid.com/) application, this even includes my phone.

Since I began using Keepass, I have been looking for a way to import those pesky web application passwords into Keepass. Since I have a different login and password for essentially every site I visit, managing and remembering these has been a huge problem in the past. With multiple hundreds of unique login/password combinations, doing this by hand was not an option. This morning the problem came to a head and I decided to do something about it.

Since Keepass allows importation from it's own XML format, the building blocks for an export/import were already there. I have been learning Ruby lately, so I decided I would whip up a quick script to export my Chrome passwords.

After a bit of hacking, I finished chrome2keepass this morning and you can find it at its [Github Repository](https://github.com/alanpca/chrome2keepass).
