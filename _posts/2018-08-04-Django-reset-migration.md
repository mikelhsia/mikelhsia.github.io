---
layout: post
status: publish
published: true
title: Python Django Reset Migration
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 190
wordpress_url: http://127.0.0.1:1028/?p=190
date: '2017-08-04 12:57:40 +0800'
date_gmt: '2017-08-04 12:57:40 +0800'
categories:
- Programming
tags:
comments: []
---
Django开发—如何重置migration

情景一：不需要原有的数据库数据
删除数据库所有的表
删除项目的migration模块中的所有 文件，除了`init.py`文件
<!--More-->
执行脚本 
```
python manage.py makemigrations 
python manage.py migrate
```

情景2：不想要删除现有的数据库，只是想重新建立 migration 文件
首先要保证,目前的migration文件和数据库是同步的，通过执行
```
python manage.py makemigrations 
```
如果看到 这样的提示: `No changes detected`，则可以继续接下来的步骤

通过执行
```
python manage.py showmigrations 
```
结果，可以看到当前项目，所有的app及对应的已经生效的migration文件如
```
git_hook
 [X] 0001_initial
guardian
 [X] 0001_initial
kombu_transport_django
 [X] 0001_initial
message
 (no migrations)
order
 [X] 0001_initial
pay
 [X] 0001_initial
 [x] 0002_add_model
sessions
 [X] 0001_initial
```

通过执行
```
$ python manage.py migrate –fake pay zero
```
这里的 pay就是你要重置的app 
之后再执行 python manage.pu showmigrations，你会发现 文件前的 [x] 变成了[ ]

现在，你可以删除pay 这个 app下的migrations模块中 除 init.py 之外的所有文件。

之后，执行
```
$ python manage.py makemigrations
```
程序会再次为这个app 生成 `0001_initial.py` 之类的文件

最重要的一步来了, 执行

python manage.py migrate –fake-inital

–fake-inital 会在数据库中的 migrations表中记录当前这个app 执行到 0001_initial.py ，但是它不会真的执行该文件中的 代码。 
这样就做到了，既不对现有的数据库改动，而又可以重置 migraion 文件，妈妈再也不用在 migration模块中看到一推文件了。