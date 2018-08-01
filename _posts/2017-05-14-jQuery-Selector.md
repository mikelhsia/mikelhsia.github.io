---
layout: post
status: publish
published: true
title: jQuery Selector
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 162
wordpress_url: http://127.0.0.1:1028/?p=162
date: '2017-05-14 14:41:51 +0800'
date_gmt: '2017-05-14 14:41:51 +0800'
categories:
- Programming
tags:
- Javascript
- jQuery
comments: []
---
<h2>更多实例</h2>
<!--More-->
<table class="reference">
<tbody>
<tr>
<th align="left" width="25%">语法</th>
<th align="left" width="65%">描述</th>
<th align="left" width="10%">实例</th>
</tr>
<tr>
<td>$("*")</td>
<td>选取所有元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_all2" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$(this)</td>
<td>选取当前 HTML 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_this" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("p.intro")</td>
<td>选取 class 为 intro 的
<p> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_pclass" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("p:first")</td>
<td>选取第一个
<p> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_pfirst" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("ul li:first")</td>
<td>选取第一个
<ul> 元素的第一个
<li> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_ullifirst" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("ul li:first-child")</td>
<td>选取每个
<ul> 元素的第一个
<li> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_ullifirstchild" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("[href]")</td>
<td>选取带有 href 属性的元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_hrefattr" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("a[target='_blank']")</td>
<td>选取所有 target 属性值等于 "_blank" 的 <a> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_hrefattrblank" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("a[target!='_blank']")</td>
<td>选取所有 target 属性值不等于 "_blank" 的 <a> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_hrefattrnotblank" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$(":button")</td>
<td>选取所有 type="button" 的 <input> 元素 和 <button> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_button2" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("tr:even")</td>
<td>选取偶数位置的<br />
<tr> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_even" target="_blank">在线实例</a></td>
</tr>
<tr>
<td>$("tr:odd")</td>
<td>选取奇数位置的<br />
<tr> 元素</td>
<td><a class="tryitbtn" style="width: 55px; padding-top: 0px; padding-bottom: 1px;" href="/try/try.php?filename=tryjquery_sel_odd" target="_blank">在线实例</a></td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>在事件中经常使用术语"触发"（或"激发"）例如：<br />
"当您按下按键时触发 keypress 事件"。</p>
<p>常见 DOM 事件：</p>
<table class="reference">
<tbody>
<tr>
<th style="width: 23%;">鼠标事件</th>
<th style="width: 25%;">键盘事件</th>
<th style="width: 22%;">表单事件</th>
<th>文档/窗口事件</th>
</tr>
<tr>
<td>click</td>
<td>keypress</td>
<td>submit</td>
<td>load</td>
</tr>
<tr>
<td>dblclick</td>
<td>keydown</td>
<td>change</td>
<td>resize</td>
</tr>
<tr>
<td>mouseenter</td>
<td>keyup</td>
<td>focus</td>
<td>scroll</td>
</tr>
<tr>
<td>mouseleave</td>
<td></td>
<td>blur</td>
<td>unload</td>
</tr>
</tbody>
</table>