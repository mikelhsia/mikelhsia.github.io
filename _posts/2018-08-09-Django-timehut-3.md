---
layout: post
status: publish
published: true
title: Python Django Time Hut 3
author:
  display_name: Michael Hsia
  login: michaelhsia
  email: mikelhsia@hotmail.com
  url: ''
author_login: michaelhsia
author_email: mikelhsia@hotmail.com
wordpress_id: 190
wordpress_url: http://127.0.0.1:1028/?p=190
date: '2017-08-09 12:57:40 +0800'
date_gmt: '2017-08-09 12:57:40 +0800'
categories:
- Programming Python Django
tags:
comments: []
---

<!--More-->
In this chapter, you will learn how to create a JavaScript bookmarklet to share content from other sites into your website, and you will implement AJAX features into your project using jQuery and Django.

This chapter will cover the following points:
- Creating many-to-many relationships
- Customizing behavior for forms
- Using jQuery with Django
- Building a jQuery bookmarklet
- Generating image thumbnails using sorl-thumbnail
- Implementing AJAX views and integrating them with jQuery
- Creating custom decorators for views
- Building AJAX pagination

### Posting content from other websites
#### Cleaning form fields
#### Overriding the save() method of a ModelForm
#### Building a bookmarklet with jQuery
#### Building detail page for image liked
#### Adding Ajax actions with jQuery
- add() passing an object that is already present in the related object set does not duplicate it and thus
- remove() passing an object that is not in the related object set does nothing
- Another many-to-many manager is clear(), which removes all objects from the related object set

`JsonResponse` class provided by Django, which returns an HTTP response with an `application/json` content type, converting the given object into a JSON output.

__Cross-Site Request Forgery in AJAX requests__
Django allows you to set a custom X-CSRFToken header in your AJAX requests with the value of the CSRF token.

In order to include the token in all requests, you need to:
1. Retrieve the CSRF token form the csrftoken cookie, which is set if CSRF protection is active
2. Send the token in the AJAX request using the X-CSRFToken header
  
#### Creating custom decorators for your views
We are going to restrict our AJAX views to allow only requests generated via AJAX. The Django Request object provides an `is_ajax()` method that checks if the request is being made with `XMLHttpRequest`, which means it is an AJAX request. This value is set in the `HTTP_X_REQUESTED_WITH` HTTP header, which is included in AJAX requests by most JavaScript libraries.

#### Adding AJAX pagination to your list views
- `empty_page`: Allows us to know if the user is in the last page and retrieves an empty page. As soon as we get an empty page we will stop sending additional AJAX requests because we will assume there are no more results.
- `block_request`: Prevents from sending additional requests while an AJAX request is in progress
