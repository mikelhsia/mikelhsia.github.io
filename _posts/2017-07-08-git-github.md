---
layout: post
status: publish
published: true
title: Git & Github
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 184
wordpress_url: http://127.0.0.1:1028/?p=184
date: '2017-07-08 03:46:20 +0800'
date_gmt: '2017-07-08 03:46:20 +0800'
categories:
- System
tags: []
comments: []
---
本篇讲述安装git并和github连接的步骤.
<!--More-->
### 1、在ubuntu中安装git
<div class="cnblogs_code">
<pre>$ sudo apt-get install git git-core</pre>
</div>
### 2、配置本机的git
<div class="cnblogs_code">
<pre>$ git config --global user.name "abcd"
$ git config --global user.email abcd@efgh.com</pre>
</div>
### 3、生成密钥
<div class="cnblogs_code">
<pre>$ ssh-keygen -t rsa -C "abcd@efgh.com" //邮箱同上</pre>
</div>
### 4、提交密钥
<div class="cnblogs_code">
<pre>vim /home/linx/.ssh/id_rsa.pub //复制里面的密钥</pre>
</div>
<p>到github网页中登陆自己的账号，然后再account setting中，找到SSH KEY讲复制的密钥加入（需要再次输入github的密码）</p>
### 5、检验是否链接上了github
<div class="cnblogs_code">
<pre>$ ssh git@github.com
//正常情况下，回显如下
PTY allocation request failed on channel 0
Hi plinx! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.</pre>
</div>
### 6、首次推送
<div>
<div class="cnblogs_code">
<pre>$ mkdir tmp      //创建推送目录
$ cd tmp         //进入推送目录    
$ git init       //设置该目录为推送
$ touch README   //生成readme
$ git add README //加入修改列表
$ git commit -m 'first commit' //递交修改声明
$ git remote add origin git@github.com:abcd/tmp.git //为远程Git更名为origin
$ git push -u origin master //推送此次修改</pre>
</div>
<hr>
<p>然后各种问题从这里开始了，以下谈一下解决的方法：</p>
</div>
##### 问题一：
<div class="cnblogs_code">
<pre>ERROR: Repository not found.</pre>
</div>
<p>这个问题是因为在你推送的github账户中，并没有这个Repository。</p>
<p>解决方法：</p>
<p>1）检查自己的github中的Repository，检查自己创建的目录，必须要两者一致；</p>
<p>2）先git clone下github中的Repository，然后再进行更改，这样就一定一致了。</p>
##### 问题二：
<div class="cnblogs_code">
<pre>Agent admitted failure to sign using the key. 
Permission denied (publickey)</pre>
</div>
<p>这个问题是因为你的ssh key并没有加入到你想git的github账户的ssh key中，所以没有访问权限。</p>
<p>解决方法：</p>
<p>1）重新拷贝一份当前的~/.ssh/id_rsa.pub中的ssh key到github中添加;</p>
<p>2）先删除~/.ssh/in_rsa*文件，然后重新ssh-keygen一份sshkey来生成密钥，然后复制到github，接着ssh链接github来检验是否成功联通。</p>
##### 问题三：
<div class="cnblogs_code">
<pre>//出现如下提示
! [rejected] master -> master (non-fast-forward)
error: failed to push some refs to ...</pre>
</div>
<p>这个问题是因为，github中已经有了这个代码，不允许你覆盖它。</p>
<p>解决方法：</p>
1) 强制推送，一般不推荐！
<div class="cnblogs_code">
<pre>$ git push -f</pre>
</div>
2)
<div class="cnblogs_code">
<pre>$ git pull</pre>
</div>
<p>然后将出现其他提示，具体意思是说branch与merge未指定，git无法选择要推送的分支。</p>
<p>可以通过修改 .git/config文件中的下列内容</p>
<div class="cnblogs_code">
<pre>[branch "master"]
    remote = origin
    merge = refs/heads/master</pre>
</div>
<p>也可以直接命令行修改</p>
<div class="cnblogs_code">
<pre>$ git config branch.master.remote origin
$ git config branch.master.merge ref/heads/master</pre>
</div>
<p>目前了解到的也就这三个问题了。</p>
<p>之后就可以成功得推送了。</p>
<hr>
<p>接着上一篇的，从github clone下代码。</p>
### 1、先查看当前开发分支
<div class="cnblogs_code">
<pre>$ cat .git/HEAD
ref: refs/heads/master</pre>
</div>
<p>这里的master是默认分支。</p>
### 2、查看当前状态
<div class="cnblogs_code">
<pre>$ git status
# On branch master
nothing to commit (working directory clean)</pre>
</div>
<p>目前是无推送状态，即使你推送了一个未做任何改变的文件，当前状态仍未无推送状态。</p>
<p>进入README添加一句之后</p>
<div class="cnblogs_code">
<pre>$ git add README
//之后有两种方法填写推送信息
//比较简单的一种，直接写入推送信息，-m 就是 message 的意思
$ git commit -m 'message you want to write.'
//比较麻烦的一种
$ git commit
//进入GNU nano编辑器，底行有操作提示</pre>
</div>
<p>将提示</p>
<div class="cnblogs_code">
<pre>[master bc30d5d] updated the status.
 1 file changed, 1 insertion(+)</pre>
</div>
<p>然后再看一下status</p>
<div class="cnblogs_code">
<pre># On branch master
# Your branch is ahead of 'origin/master' by 1 commit.
#
nothing to commit (working directory clean)</pre>
</div>
### 3、git中有日志可以查看推送记录
<div class="cnblogs_code">
<pre>$ git log</pre>
</div>
### 4、检查不同
<div class="cnblogs_code">
<pre>$ git diff
//这项操作时要在添加推送之前执行的，否则就看不出哪里不同了</pre>
</div>
### 5、创建分支
<div class="cnblogs_code">
<pre>git branch test0.1   //创建一个test0.1分支
git checkout test0.1   //进入这个分支中来
git branch   //查看当前分支情况，所在分支前面有'*'号
git add -A     //将本次修改的所有内容都加入修改列表
git commit -m "commit all"   //提交说明
git push -u origin test0.1  //将此次修改提交到分支test0.1中去</pre>
</div>
### 6、只对项目精简了而没有增加内容
<div class="cnblogs_code">
<pre>$ git commit -a 
$ git push -u origin code_ver0.1
//分支和账户请勿对号入座
</pre>
</div>
