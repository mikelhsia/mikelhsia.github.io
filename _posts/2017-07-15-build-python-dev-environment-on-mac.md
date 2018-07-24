---
layout: post
status: publish
published: true
title: Mac中基于Homebrew搭建python开发环境
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 186
wordpress_url: http://127.0.0.1:1028/?p=186
date: '2017-07-15 05:57:59 +0800'
date_gmt: '2017-07-15 05:57:59 +0800'
categories:
- System
tags:
- Mac
- python
comments: []
---
<p class="title"><a href="http://www.jianshu.com/p/b26b86bff852">Mac中基于Homebrew搭建python开发环境</a></p>
<div class="show-content" data-note-content="">
<div class="image-package">
<p><img src="http://upload-images.jianshu.io/upload_images/912917-19836c0a351b7d90.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240" data-original-src="http://upload-images.jianshu.io/upload_images/912917-19836c0a351b7d90.png?imageMogr2/auto-orient/strip%7CimageView2/2" /></p>
<!--More-->
</div>
<p>转移到mac上了。这里是在lion中搭建python开发环境的简单记录。这份记录不是一份step by step.而是事后写的记录，可能有记忆遗漏。如果有错误，请指正。</p>
<hr />
<h3>1.安装homebrew的准备</h3>
<pre class="hljs bash"><code class="bash">$ sudo chown -R `whoami` /usr/<span class="hljs-built_in">local</span></code></pre>
<blockquote><p>homebrew希望在没有sudo的环境下工作（Homebrew is designed to work without using sudo.）所以首先对/usr/local/这个文件夹赋权限。（homebrew的软件是安装在这里的）</p></blockquote>
<h3>2.通过shell安装</h3>
<pre class="hljs bash"><code class="bash">$ ruby <span class="hljs-_">-e</span> <span class="hljs-string">"<span class="hljs-variable">$(curl -fsSL https://gist.github.com/raw/323731/install_homebrew.rb)</span>"</span></code></pre>
<p>3.配置环境变量：</p>
<pre class="hljs bash"><code class="bash">$ nano ~/.bash_profile</code></pre>
<p>加入以下内容：</p>
<pre class="hljs bash"><code class="bash"><span class="hljs-comment">#Setting PATH for Homebrew</span>
PATH=<span class="hljs-string">"/usr/local/bin:<span class="hljs-variable">${PATH}</span>"</span>
<span class="hljs-built_in">export</span> PATH</code></pre>
<p>Ok，这样homebrew就装好了。</p>
<h3>4.brew的简单命令</h3>
<pre class="hljs bash"><code class="bash">$ brew search <pkg_name>  <span class="hljs-comment">#查找软件包</span>
$ brew install <pkg_name>  <span class="hljs-comment">#安装软件包</span>
$ brew list <span class="hljs-comment">#列出软件包</span>
$ brew uninstall <pkg_name> <span class="hljs-comment">#卸载软件包</span>
$ brew update <span class="hljs-comment">#更新</span>
$ brew info <pkg_name> <span class="hljs-comment">#查看软件包的基本资料</span></code></pre>
<h3>5.安装python</h3>
<pre class="hljs bash"><code class="bash">$ brew install python --framework --universal
The &ndash;framework option tells it to build as a Framework, <span class="hljs-built_in">which</span> has some downstream niceties, and &ndash;universal builds a universal (32/64 bit) version.</code></pre>
<h3>6.将python加入path</h3>
<pre class="hljs bash"><code class="bash">$ nano ~/.bash_profile
<span class="hljs-built_in">export</span> PATH=/usr/<span class="hljs-built_in">local</span>/share/python:<span class="hljs-variable">$PATH</span></code></pre>
<h3>7.检查安装是否正确</h3>
<p>此时，最好重启term。如果要确认修改是否正确，可以用which python和which easy_install查看python的路径是否正确。如果返回为</p>
<p>/usr/local/bin/python<br />
和</p>
<p>/usr/local/share/python/easy_install<br />
那么，安装正确</p>
<h3>8.通过easy_install安装pip</h3>
<pre class="hljs bash"><code class="bash">$ easy_install pip</code></pre>
<h3>9.安装virtualenv 和 virtuanenvwarpper</h3>
<pre class="hljs bash"><code class="bash">$ /usr/<span class="hljs-built_in">local</span>/share/python/pip install virtualenv
$ /usr/<span class="hljs-built_in">local</span>/share/python/pip install virtualenvwrapper <span class="hljs-comment">##其实这个装不装已经无所谓了。</span></code></pre>
<h3>10.建立和项目相关的env</h3>
<p>比如，项目文件在~/projects中,那么，</p>
<pre class="hljs bash"><code class="bash">$ <span class="hljs-built_in">cd</span> ~/projects
$ virtualenv --no-site-packages project_name
The --no-site-packages flag is deprecated; it is now the default behavior.
New python executable <span class="hljs-keyword">in</span> project_name/bin/python
Installing setuptools............done.
Installing pip...............done.</code></pre>
<h3>11.启动虚拟环境</h3>
<p>首先进入刚刚建立的虚拟环境目录，比如：</p>
<pre class="hljs bash"><code class="bash">$ <span class="hljs-built_in">cd</span> project_name
$ <span class="hljs-built_in">source</span> bin/activate</code></pre>
<p>注意，此时shell提示符前多了虚拟环境的名称提示：<br />
(project_name)&hellip;.$<br />
Now,do anything you want.</p>
<h3>12.退出虚拟环境</h3>
<pre class="hljs bash"><code class="bash">$ deactivate</code></pre>
<h3>13.pip的设定</h3>
<p>如果要保证在虚拟环境中调用系统的pip,可以在~/.bash_profile里加上：</p>
<pre class="hljs bash"><code class="bash"><span class="hljs-built_in">export</span> PIP_REQUIRE_VIRTUALENV=<span class="hljs-literal">true</span></code></pre>
<p>如果要让系统的pip自动调用虚拟环境中的pip</p>
<pre class="hljs bash"><code class="bash"><span class="hljs-built_in">export</span> PIP_RESPECT_VIRTUALENV=<span class="hljs-literal">true</span></code></pre>
<h3>14.安装你需要的软件包（注意提示符）</h3>
<p>(project_name)....$ pip install pkg_name<br />
【END】</p>
</div>
