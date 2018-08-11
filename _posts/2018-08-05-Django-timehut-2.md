---
layout: post
status: publish
published: true
title: Python Django Time Hut 2
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
- Programming Python Django
tags:
comments: []
---

<!--More-->
### Building a Social Website
- Using the authentication framework
- Creating user registration views
- Extending the User model with a custome profile model
- Adding social authentication with python-social-auth

#### Creating a social website project
Auth framework consists of the django.contrib.auth application and the following two middleware classes found in the MIDDLEWARE_CLASSES setting of your project:
- **`AuthenticationMiddleware`**: Associates users with requests using sessions
- **`SessionMiddleware`**: Handles the current session across requests

The authentication framework also includes the following models:
**`User`**: A user model with basic fields; the main fields of this model are: `username`, `password`, `email`, `first_name`, `last_name`, and `is_active`.
**`Group`**: A group model to categorize users.
**`Permission`**: Flags to perform certain actions.”

#### Using Django authentication views
Django provides the following views to deal with authentication:
- `login`: Handles a log in form and logs in a user
- `logout`: Logs out a user
  - If you enable `auth.views` for both frontend user and backedn administrator, then you need to do some twist to make sure the login/logout views are separated.
- `logout_then_login`: Logs out a user and redirects him to the log-in page

Django provides the following views to handle password changes:
- `password_change`: Handles a form to change user password
- `password_change_done`: The success page shown to the user after changing his password

Django also includes the following views to allow users to reset their password:
- `password_reset`: Allows the user to reset his password. It generates a one-time use link with a token and sends it to the user's e-mail account.
- `password_reset_done`: Shows the user that the e-mail to reset his password has been sent to his e-mail account.
- `password_reset_confirm`: Lets the user set a new password.
- `password_reset_complete`: The success page shown to the user after he resets their password.”

#### User registration and user profiles

#### Extending the User model
- Extending the User model
- Using a custom User model
- Using the messageframework

#### Using a custom User model
Django also offers a way to substitute the whole User model with your own custom model. Your user class should inherit from Django's AbstractUser class, which provides the full implementation of the default user as an abstract model.

#### Using the messages framework/middleware
messages is default Django middleware, and can be imported by using:
```
from django.contrib import messages
messages.error(request, 'Something went wrong')
```
- success(): Success messages to display after an action was successful
- info(): Informational messages
- warning(): Something has not yet failed but may fail imminently
- error(): An action was not successful or something failed
- debug(): Debug messages that will be removed or ignored in a production environment

#### Building a custom authentication backend
The AUTHENTICATION_BACKENDS setting includes the list of authentication backends for your project. By default, this setting is set to the following:

`('django.contrib.auth.backends.ModelBackend',)`

The default ModelBackend authenticates users against the database using the User model of django.contrib.auth. This will suit most of your projects. However, you can create custom backends to authenticate your user against other sources like a LDAP directory or any other system.

An authentication backend is a class provides the following:
- authenticate(): Takes user credentials as parameters. Has to return `True` if the user has been successfully authenticated, or False otherwise.
- get_user(): Takes a user ID parameter and has to return a User object.
