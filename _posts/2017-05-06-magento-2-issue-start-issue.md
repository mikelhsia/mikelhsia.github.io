---
layout: post
status: publish
published: true
title: Magento 2 Issue that bother's me
date: '2017-05-06 07:20:20 +0800'
categories:
- Magento 2
tags:
- PHP
comments: []
---
<!--More-->
<h3>php:</h3>
<p>mcrypt&nbsp;-&nbsp;<span class="s1">Notice: Use of undefined constant MCRYPT_BLOWFISH - assumed '</span><span class="s2">MCRYPT_BLOWFISH</span><span class="s1">'</span></p>
<p>intl -&nbsp;<a href="http://stackoverflow.com/questions/6242378/fatal-error-class-intldateformatter-not-found">Fatal error: Class 'IntlDateFormatter' not found</a></p>
<p>And which php to find out whether you use the right php file or not. I installed mcrypt and intl in php56, but I used brew default php</p>
<p>&nbsp;</p>
<h3>URL redirect error:</h3>
<p>Css and javascript style missing because the nginx setting to port 1028, but still trying to get CSS and javascript from port 1025</p>
<p>Solution: Found out that even though the nginx setting is correct, but in the very beginning while I installing Magento 2, I set 1025 as default Store url, and then I configured both Magento 2 and Wordpress on the same &nbsp;nginx file, and change Magento 2 port 1028 and never noticed since. That's why I could access my Magento 2 store but tried to retrieve CSS and Javascript and images from other port.</p>
<p>&nbsp;</p>
