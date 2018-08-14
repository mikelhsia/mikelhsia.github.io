---
layout: post
status: publish
published: true
title: Python Django Time Hut 4
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 190
wordpress_url: http://127.0.0.1:1028/?p=190
date: '2017-08-11 12:57:40 +0800'
date_gmt: '2017-08-11 12:57:40 +0800'
categories:
- Programming Python Django
tags:
comments: []
---

<!--More-->
## Tracking User Actions
- Creating many-to-many relationships with an intermediary model
- Building AJAX views
- Creating an activity stream application
- Adding generic relations to models
- Optimizing QuerySets for related objects
- Using signals for denormalizing counts
- Storing item views in Redis

### Building a follower system
#### Creating many-to-many relationships with an intermediary model
`User.add_to_class('following', models.ManyToManyField('self', through=Contact, related_name='followers', symmetrical=False))`
We can't alter the User class directly because it belongs to the django.contrib.auth application
We are going to take a slightly different approach, by adding this field dynamically to the user model (Monkey-patch)
- tell Django to use our custom intermediary model for the relationship by adding through=Contact to the ManyToManyField.
------------------------------
Keep in mind that in most cases, it is preferable to add fields to the Profile model we created before, instead of monkey-patching the User model. Django also allows you to use custom user models.
------------------------------
Django forces the relationship to be symmetrical. In this case, we are setting symmetrical=False to define a non-symmetric relation. This is, if I follow you, it doesn't mean you automatically follow me.

### Creating list and detail views for user profiles
### Building an Ajax view to follow users
