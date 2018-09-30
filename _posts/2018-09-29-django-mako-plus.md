---
layout: post
title:  "Django-Mako-Plus?"
date:   2018-09-29 22:15:00
author: Mitchell Sotto
categories: Web-Application Python
---
For my Enterprise Application Develompment class (Fall 2017), we used a Python MVC library called Django-Mako-Plus (DMP) to build a full scale e-commerce site with item listings, a shopping cart, and the ability to pay using Stripe. 

DMP uses migrations and Models to work with the database through it's ORM (Object Relational Mapping). We connected to a PostgreSQL database and used the django-polymorphic library to allow 3 different types of products tables (bulk, individual, resale) to inherit from a main "Products" table with general information for all of it's child tables.

I haven't kept up with the upgrades to Django-Mako-Plus for the past year, so the code needs some fixing to bring up the site. The code repo on Github is private so that future students of the class cannot copy it, but feel free to message me if you want to take a look at the code (sottochoro@gmail.com).


![Django Image](/assets/django.png){:target="_blank"}
