---
layout: post
status: publish
published: true
title: Python Django Online Shop Setup
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 190
wordpress_url: http://127.0.0.1:1028/?p=190
date: '2017-08-18 12:57:40 +0800'
date_gmt: '2017-08-18 12:57:40 +0800'
categories:
- Programming Python Django
tags:
comments: []
---

<!--More-->
# Building e-commerce shop
- Building Category and Product 
- Building Catalog views

## Building Django Session
You can set a variable in the session like this:
`request.session['foo'] = 'bar'`
Retrieve a session key:
`request.session.get('foo')`
Delete a key you stored in the session:
`del request.session['foo']”`

Django stores sessions in the database using the Session model of the `django.contrib.sessions` application.

Django offers the following options for storing session data:
- *Database sessions*: Session data is stored in the database. This is the default session engine.
- *File-based sessions*: Session data is stored in the file system.
- *Cached sessions*: Session data is stored in a cache backend. You can specify cache backends using the `CACHES` setting. Storing session data in a cache system offers best performance.
- *Cached database sessions*: Session data is stored in a write-through cache and database. Reads only use the database if the data is not already in the cache.
- *Cookie-based sessions*: Session data is stored in the cookies that are sent to the browser.”

You can customize sessions with other settings. Here are some of the important session related settings:
- **SESSION_COOKIE_AGE**: This is the duration of session cookies in seconds. The default value is 1209600 (2 weeks).
- **SESSION_COOKIE_DOMAIN**: This domain is used for session cookies. Set this to .mydomain.com to enable cross-domain cookies.
- **SESSION_COOKIE_SECURE**: This is a boolean indicating that the cookie should only be sent if the connection is an HTTPS connection.
- **SESSION_EXPIRE_AT_BROWSER_CLOSE**: This is a boolean indicating that the session has to expire when the browser is closed.
- **SESSION_SAVE_EVERY_REQUEST**: This is a boolean that, if True, will save the session to the database on every request. The session expiration is also updated each time.”

## Building shopping cart by using session
- When a cart is needed, we check if a custom session key is set. If no cart is set in the session, we create a new cart and save it in the cart session key.
- For successive requests, we perform the same check and get the cart items from the cart session key. We retrieve the cart items from the session and their related Product objects from the database.


## Context processors
Context processor is a Python function that takes the `request` object as an argument and returns a dictionarty that gets added to the request context and available to ***all*** the templates rendered using `RequestContext`
- `django.template.context_processors.debug`: This sets the Boolean debug and sql_queries variables in the context representing the list of SQL queries executed in the request
- `django.template.context_processors.request`: This sets the request variable in the context
- `django.contrib.auth.context_processors.auth`: This sets the user variable in the request
- `django.contrib.messages.context_processors.messages`: This sets a messages variable in the context containing all messages that have been sent using the messages framework.
Django also enables `django.template.context_processors.csrf` to avoid cross-site request forgery attacks. This context processor is not present in the settings, but it is always enabled and cannot be turned off for security reasons.

