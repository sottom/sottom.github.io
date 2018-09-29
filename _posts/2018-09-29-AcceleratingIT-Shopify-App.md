---
layout: post
title:  "AcceleratingIT - Startups Rock"
date:   2018-09-29 22:15:00
author: Mitchell Sotto
categories: ruby-on-rails react
---
A local e-commerce startup with a store on Shopify is struggling to predict how much inventory they will need each month. 

They approached my friend and we made a team of three people to create a shopify integration app that will use Holt Winters Triple Exponential Smoothing to predict their needed inventory based on previous sell data. 

One teammate is a our data analyst, another is our manager of sorts, and I am the developer of both the frontend and the backend. We've decided to call ourselves AcceleratingIT.

##### System Architecture
I decided to use a microservice architecture where the frontend and backend are completely seperated and only communicate asynchronously through AJAX calls. This is useful because we can hook up our React frontend to any backend that we need (for instance, if we find that a Python/Django Backend better suits our forecasting needs).

The backend is currently a Ruby on Rails API connected to a PostgreSQL database hosted on Heroku, and the frontend is a React app served by a Node server hosted on Heroku.

We are using _________ for our graphs.

### Problems
The biggest problem we faced so far has been integrating our app into the admin dashboard on Shopify. After trying several outdated SDKs (Sinatra, Rails, Node) over a few weeks, I decided to build my own Rails backend from scratch, and our app is finally integrated in the admin dashboard!

We are currently figuring out what data we need to query from Shopify so that we can accurately do our forecasting. We are not sure if we want the frontend or the backend to do the bulk of the processing, but we are leaning towards the backend. After we do the processing, we just need to hook the JSON data up to our graph, and we will have a nice MVP for our startup friends
