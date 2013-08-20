---
layout: default
title: Djangoappengine-helpers - Setup Reloaded
excerpt: djangoappengine-helpers now provides a real Django authentication backend. So far the Backend only implements the authentication() method. It doesn't accept any arguments and uses the Google App Engine API to authenticate a user. All other backend methods are inherited from ModelBackend. 


---

Djangoappengine-helpers -<br/> Setup Reloaded
=========================================

**Update:** Djangoappengine-helpers dead, but the authentication backend
was moved to a seperate project, [django-gaeauth](https://github.com/fhahn/django-gaeauth).

djangoappengine-helpers now provides a real Django authentication backend.
So far the Backend only implements the authentication() method. It doesn't 
accept any arguments and uses the Google App Engine API to authenticate a user.
All other backend methods are inherited from ModelBackend. 

Setup 

 * download the code from bitbucket.org 
 * put the code to your common-apps directory (the module g_helpers has to be
   importable from inside your Django app)
 * Add the authentication backend to your settings.py : 
   AUTHENTICATION_BACKENDS = ('g_helpers.auth.backends.GoogleAccountBackend',)
 * add login/logut urls : (r'^accounts/', include('g_helpers.auth.urls')),
   to your root urlconf 

 -> the login url for example will look like: */accounts/login/*, *g_helpers.auth.urls* are named and support reversing, so you can include *g_helpers.auth.urls* for */fooBar* instead of */accounts* The setup was tested with djangoappengine and django-norel on Google App Engine.

<div class="post-footer">Posted on Aug. 13, 2010 </div>
