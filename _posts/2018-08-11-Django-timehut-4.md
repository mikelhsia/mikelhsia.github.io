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
#### Using the contenttypes framework
ContentType model
- `app_label`: The name of the application the model belongs to. This is automatically taken from the app_label attribute of the model Meta options. For example, our Image model belongs to the application images.
model: The name of the model class.
- `name`: The human-readable name of the model. This is automatically taken from the verbose_name attribute of the model Meta options

#### Adding generic relations to your models
#### Avoiding duplicate actions in the activity stream
#### Adding user actions to the activity stream
- A user bookmarks an image
- A user likes/unlikes an image
- A user creates an account
- A user follows/unfollows another user
#### Displaying the activity stream
#### Optimizing QuerySets that involve related objects
- Using `select_related`: We are using user__profile to join the profile table too in one single SQL query. If you call select_related() without passing any arguments to it, it will retrieve objects from all ForeignKey relationships. Always limit select_related() to the relationships that will be accessed afterwards.
- Using `prefetch_related`: select_related() cannot work for many-to-many or many-to-one relationships (ManyToMany or reverse ForeignKey fields). Django offers a different queryset method called prefetch_related that works for many-to-many and many-to-one relations in addition to the relations supported by select_related(). The prefetch_related() method performs a separate lookup for each relationship and joins the results using Python. This method also supports prefetching of GenericRelation and GenericForeignKey.
#### Creating templates for actions

### Using signals for denormalizing counts
`Denormalization` is making data redundant in a way that it optimizes read performance. You could improve your queries by denormalizing counts. The drawback is that we have to keep the redundant data updated.
#### Working with signals (Django signal dispatcher)
Django provides several signals for models located at `django.db.models.signals`. Some of these signals are:
- `pre_save` and `post_save`: Sent before or after calling the `save()` method of a model
- `pre_delete` and `post_delete`: Sent before or after calling the `delete()` method of a model or queryset
- `m2m_changed`: Sent when a `ManyToManyField` on a model is changed

#### Defining application configuration classes

### Using Redis for storing item views
