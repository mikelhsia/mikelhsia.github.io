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
#### Connecting existing mysql DB
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

1. Changing DATABASE setting in `settings.py`
2. Use `python3 manage.py inspectdb > models.py` to generate Mysql schema
3. Modify models.py schema
4. `python3 manage.py migrate`



### Creating an administration site for your models
#### Creating a superuser
```
python3 manage.py createsuperuser
```
Then access http://127.0.0.1:8000/admin/

### Sharing posts by e-mail
1. Create a form for users to fill in their name and e-mail, the e-mail recipient, and optional comments
  - Form: Allows you to build standard forms
  - ModelForm: Allows you to build forms to create or update model instances
  ```
  Note
  Forms can reside anywhere in your Django project but the convention is to place them inside a forms.py file for each application.
  ```
2. Create a view in the `views.py` file that handles the posted data and sends the e-mail
  - external SMTP server by adding the following settings in the settings.py file of your project:
  ```
  EMAIL_HOST: The SMTP server host. Default localhost.
  EMAIL_PORT: The SMTP port Default 25.
  EMAIL_HOST_USER: Username for the SMTP server.
  EMAIL_HOST_PASSWORD: Password for the SMTP server.
  EMAIL_USE_TLS: Whether to use a TLS secure connection.
  EMAIL_USE_SSL: Whether to use an implicit TLS secure connection.”
  ```
3. Add an URL pattern for the new view in the `urls.py` file of the blog application
4. Create a template to display the form


### Create comment system
1. Create models.py
2. Create form
  - Remember that Django has two base classes to build forms: Form and ModelForm.
3. Handling ModelForms in views
  - save() is available for ModelForm but not for Form instance, since they are not linked to any model
4. Adding comments to the collection detail template
  - Display the total number of comments for the post
  - Display the list of comments
  - Display a form for users tp add a new comment

### Extending Your Blog Application
- Creating custom template tags and filters
- Adding a sitemap and a post feed
- Building a search enging with Solr and Haystack

#### Creating custom template tags and filters
1. Creating custom template tags
  - `simple_tag`: Processes the data and returns a string
  - `inclusion_tag`: Processes the data and returns a rendered template
  - `assignment_tag`: Processes the data and sets a variable in the context (`assignment_tag` is depricated in Django 2.0)
  '''
  Template tags must live inside Django applications
  '''
2. Creating custom template filters

#### Adding a sitemap to your site
in sitemap.py
```
from django.contrib.sitemaps import Sitemap
```

in urls.py
```
from django.contrib.sitemaps.views import sitemap
from blog.sitemaps import PostSitemap
...
...
urlpatterns = [
...
...
path('sitemap.xml', sitemap, {'sitemaps': sitemaps}, name='django.contrib.sitemaps.views.sitemap')
]
```

#### Adding a RSS feed
in feeds.py
```
from django.contrib.syndication.views import Feed
...
...
```