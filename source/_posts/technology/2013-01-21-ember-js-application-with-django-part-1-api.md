---
layout: post
title: Ember.js Application with Django (Part 1 - API)
date: '2013-01-21T00:50:00+05:30'
tags: [django, ember.js, django-tastypie]
category: technology
comments: true
tumblr_url: http://sandeep-n.tumblr.com/post/22917999992/ember-js-application-with-django-part-1-api
---
I’ve been reading about Ember.js from the past few days, and got quite fascinated by it. The Emberjs documentation itself is good enough to set you on the right track.

So, today I decided to write a piece of code with it using Django as the backend. The application that we’ll be writing is a simple contact manager.
<!--more-->
Assumption: You are familiar with django but a newbie to ember.js, so I'll skip the basic steps of configuring a django app.

##Creating the bare-bone backend

We’ll start by creating a RESTful API in django which will act as a backend for CRUD operations performed from ember. I’ll use django-tastypie for exposing the API.

Create the project:

I am using Django 1.4, but the below code should work fine with 1.3 too.

    # Install Django and tastypie
    pip install django
    pip install django-tastypie

    # Create a new project
    django-admin.py startproject ember_django
    cd ember_django

    # Create a new app
    python manage.py startapp contacts
    Add to installed apps: INSTALLED_APPS += ['tastypie', 'contacts']


###The 'Contact' Model
Create a model class for each contact. This will reside in contacts/models.py.

    ``` Python
    # contacts/models.py
    from django.db import models
    class Contact(models.Model):
        name = models.CharField(max_length=512)
        phone = models.CharField(max_length=512)
        email = models.EmailField(max_length=1024)

        def unicode(self):
            return self.name
    ```

Nothing fancy here. This is just a normal django model with three fields to store information about a contact. After creating the model, we need to create the database tables by executing: `python manage.py syncdb`

###Exposing via API

Create a tastypie resource class to expose the above contact model. This will reside in contacts/api.py

    ``` Python
    # contacts/api.py
    from tastypie.resources import ModelResource
    from tastypie.authorization import Authorization
    from contacts.models import Contact

    class ContactResource(ModelResource):
        class Meta:
            queryset = Contact.objects.all()
            resource_name = ‘contact’
            authorization= Authorization()
    ```

The last line in the above code makes this resource to have world writeable permissions. This is NOT a good practice for an API to be exposed over internet. But it is good enough for us in a development environment.

###Hooking the API resource in the URLconf

    ``` Python
    # contacts/urls.py
    from django.conf.urls.defaults import *
    from tastypie.api import Api 
    from contacts.api import ContactResource

    API_VERSION = "v1"
    api = Api(api_name=API_VERSION)
    api.register(ContactResource())

    urlpatterns = patterns("",
        (r'^', include(api.urls)),
    )
    ```

Add the below lines at the end of the root urls.py:

    ``` Python
    # ember_django/urls.py
    urlpatterns += patterns("",
        url(r'^api/', include('contacts.urls')),
    )
    ```

Now, do a `syncdb`, fire up the django dev sever, and Voila!! We have a working API interface to the Contact model.
To verify, try out the urls http://127.0.0.1:8000/api/v1/contact/schema/?format=json and http://127.0.0.1:8000/api/v1/contact/?format=json
