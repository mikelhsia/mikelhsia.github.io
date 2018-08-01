---
layout: post
status: publish
published: true
title: Python Django Setup
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 190
wordpress_url: http://127.0.0.1:1028/?p=190
date: '2017-07-15 12:57:40 +0800'
date_gmt: '2017-07-15 12:57:40 +0800'
categories:
- Programming
tags:
comments: []
---
<!--More-->
### 在settings.py中配置
```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',   # 数据库引擎
        'NAME': 'mydb',       # 你要存储数据的库名，事先要创建之
        'USER': 'root',         # 数据库用户名
        'PASSWORD': '1234',     # 密码
        'HOST': 'localhost',    # 主机
        'PORT': '3306',         # 数据库使用的端口
    }
}
```

### 数据库迁移
python3不支持MySQLdb，可用pymysql代替。cmd安装pymysql：pip install pymysql。
在项目文件夹下的_init_.py添加如下代码即可。

```
import pymysql
pymysql.install_as_MySQLdb()
```

然后在Terminal中执行数据库迁移命令：
```
python manage.py makemigrations
python manage.py migrate
```


To dump the data tables creation into SQL. The exact output depends on the database you are using
```
python3 manage.py sqlmigrate timehutBlog 0001
```


### Creating an administration site for your models
#### Creating a superuser
```
python3 manage.py createsuperuser
```
Then access http://127.0.0.1:8000/admin/
