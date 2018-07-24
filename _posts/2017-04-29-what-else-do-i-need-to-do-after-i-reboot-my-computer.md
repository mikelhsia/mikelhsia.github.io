---
layout: post
status: publish
published: true
title: What else do I need to do after I reboot my computer
date: '2017-04-29 15:39:38 +0800'
categories:
- System
tags:
- PHP
- Mac
- Nginx
- MySQL
comments: []
---
<p class="p1"><b>How to manage Nginx</b></p>
<p class="p1"><b>Nginx</b></p>
<p class="p1">sudo nginx -c /usr/local/etc/nginx/nginx.conf</p>
<p class="p1"><span class="s1">sudo nginx -s reload</span></p>
<!--More-->
<br>
<p class="p1"><b>How to manage php-fpm</b></p>
<p class="p1"><b>php-fpm (This is php-fpm, which not working since missing mcrypt)</b></p>
<p class="p1">sudo php-fpm -y /usr/local/etc/php/5.6/php-fpm.conf -c /usr/local/etc/php/5.6/php.ini</p>
<p class="p1"><b>php56-fpm</b></p>
<p class="p1"><span class="s1">sudo /usr/local/sbin/php56-fpm start -y /usr/local/etc/php/5.6/php-fpm.conf -c /usr/local/etc/php/5.6/php.ini</span></p>
<br>
<p class="p1"><b>How to manage Mysql</b></p>
<p class="p1"><b>Mysql</b></p>
<p class="p1">sudo chown -R mysql /usr/local/var/mysql</p>
<p class="p1">sudo chmod -R o+rwx /usr/local/var/mysql</p>
<p class="p1">mysql.server start</p>
