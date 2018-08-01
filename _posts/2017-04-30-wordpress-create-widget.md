---
layout: post
status: publish
published: true
title: Wordpress create widget
date: '2017-04-30 14:19:17 +0800'
categories:
- Wordpress
tags:
- WordPress
comments: []
---
- 什么是 WordPress 动作挂钩
- 什么是 WordPress 过滤钩子（Filter）
- 参考文章
  - <a href="https://www.wpdaxue.com/creating-context-sensitive-sidebar-navigation.html">
在 WordPress 中创建上下文相关的侧栏页面导航</a>
  - <a href="https://www.wpdaxue.com/creat-your-first-wordpress-widget.html">创建你的第一个WordPress小工具</a>
<!--More-->
<h4>get_pages 函数</h4>
<p>http://www.wordpress.la/codex-%E5%B8%B8%E7%94%A8%E5%87%BD%E6%95%B0-get_pages().html</p>
<br>
<h2>Differences between action and filter</h2>
<table border="2">
<tbody>
<tr>
<th width="30%">
<h2 id="什么是 WordPress 动作挂钩">什么是 WordPress 动作挂钩</h2>
</th>
<th width="30%">
<h2 id="什么是 WordPress 过滤钩子（Filter）">什么是 WordPress 过滤钩子（Filter）</h2>
</th>
</tr>
<tr>
<td>在 <a href="http://codex.wordpress.org/Plugin_API#Actions">Codex</a> （ WordPress 法典）中，给出的定义如下：<em>动作挂钩由</em><em> WordPress </em><em>中的特定事件激活，例如：发布一篇文章、更改主题，或者是显示管理控制界面（</em><em>&nbsp;</em><a href="http://codex.wordpress.org/Administration_Screens"><em>administration screen</em></a><em>）。动作挂钩是在插件（或主题）中定义的自定义</em><em>PHP</em><em>函数，即被设定为回应某些特定事件。</em></p>
<p>所以，从本质上来说，动作挂钩由某个 WordPress 事件激活，可以在事件之前或之后运行。动作挂钩只是WordPress的两种挂钩之一，另一个则是我们之前讲到的过滤挂钩（Filters）&mdash;&mdash;如果想了解更多有关 WordPress 过滤挂钩的内容，请参阅《50个 WordPress 过滤挂钩》一文。</p>
<h2 id="在WordPress中使用动作挂钩">在WordPress中使用动作挂钩</h2>
<p>定义动作挂钩只是最简单的一步，幸运的是，学会如何创建和使用动作挂钩也是非常简单的。首先，让我们来看看怎样将相关函数挂载到动作挂钩上，怎样创建新的动作挂钩，清除现有的挂钩和其他在 WordPress core中与动作挂钩相关的函数。</td>
<td>在 <a href="http://codex.wordpress.org/Plugin_API#Filters" target="_blank">WordPress 官方开发文档</a>里面，过滤钩子（filter）是这样定义的：</p>
<blockquote><p><b>过滤钩子</b>是一类函数，WordPress执行传递和处理数据的过程中，在针对这些数据做出某些动作之前的特定点运行(例如将数据写入数据库或将其传递到浏览器页面)。过滤钩子处于数据库与浏览器中间(当WordPress正在产生页面的时候)，处于浏览器与数据库之间(当WordPress添加新的数据到数据库的时候)；WordPress中的多数输入与输出都经过至少一个过滤钩子。WordPress默认已经做了一些过滤钩子，你的插件可以添加它自己的过滤钩子。</p></blockquote>
<h2 id="在 WordPress中使用过滤钩子">在 WordPress中使用过滤钩子</h2>
<p>正如我说的那样，使用 WordPress 过滤钩子是非常容易的，我们只需要了解一些过滤钩子的最基本的功能。（说实在点，最困难的部分其实是学习所有的过滤钩子，但是正如你想的那样，你一次性不可能学习每一个过滤钩子&mdash;&mdash;当你需要哪个过滤钩子的时候，再学习它。）</p>
<p>在这部分，我们要做如下四件事：</p>
<ol>
<li>创建一个过滤函数</li>
<li>挂载到一个过滤钩子</li>
<li>从过滤钩子上移除一个函数</li>
<li>创建自己的过滤钩子</li>
</ol>
</td>
</tr>
</tbody>
</table>