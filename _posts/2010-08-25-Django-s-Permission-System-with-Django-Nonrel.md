---
layout: post
title: Django's Permission System with Django-Nonrel
categories: [old]
permalink: /writing/Django-s-Permission-System-with-Django-Nonrel/
---

**Update:** The backend code was moved from *djangotoolbox* to a separate app:
[django-permission-backend-nonrel](https://github.com/django-nonrel/django-permission-backend-nonrel) . Use 
``'permission_backend_nonrel.backends.NonrelPermissionBackend'`` instead of 
``'djangotoolbox.auth.backends.NonrelPermissionBackend'`` and add 
``'permission_backend_nonrel'`` to your *INSTALLED_APPS*.

Support for Django's permission system was merged with [djangotoolbox](https://github.com/django-nonrel/django-permission-backend-nonrel)
a few days ago. An authentication backend that supports user and group permissions 
was added to
*djangotoolbox/auth/backends.py*. 

How To Use 
------------
Replace the default Django authentication backend with the one shipped with 
*permission_backend_nonrel*: 

<div class="highlight">
    <pre>
        <span class="n">settings</span><span class="o">.</span><span class="n">py</span><span class="p">:</span>
        <span class="n">AUTHENTICATION_BACKENDS</span> <span class="o">=</span> <span class="p">(</span>
        <span class="s">'permission_backend_nonrel.backends.NonrelPermissionBackend',</span>
        <span class="p">)</span>
    </pre>
</div>

Then you have to make sure that *'permission_backend_nonrel* is added to your 
*INSTALLED_APPS* in order to turn on admin support for editing groups and 
permissions of users. It's important to put *'permission_backend_nonrel* 
after *djangotoolbox*, because *'permission_backend_nonrel.admin* replaces 
*djangotoolbox*'s User admin site. Permission and groups can be assigned and 
modified via Django's admin interface: 

Now you should be able to use all the standard Django permission methods and decorators, like *user.has_perm('foo')* and so on. 
