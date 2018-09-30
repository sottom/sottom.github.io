---
layout: post
title:  "A New Startup - Rails/React Shopify App"
date:   2018-09-29 17:15:00
author: Mitchell Sotto
categories: Web-Application Ruby-on-Rails JavaScript
---
When a local e-commerce startup approached a friend of mine about their issues predicting monthly inventory for their Shopify store, he responded by creating a team of three people to create an app to help them solve their problem. With my friend as the manager, another teammate as a data analyst, and myself as the full-stack developer, we have formed our own startup called AcceleratingIT. We are currently creating an integrated Shopify app that will use Holt Winters Triple Exponential Smoothing to predict the startup's needed inventory based on previous sales data.

### System Architecture
I decided to use a microservice architecture where the frontend and backend are completely seperated and only communicate asynchronously through AJAX calls. This is useful because we can hook up our React frontend to any backend that we need (for instance, if we find that a Python/Django Backend better suits our forecasting needs).

The backend is currently a Ruby on Rails API connected to a PostgreSQL database hosted on Heroku, and the frontend is a React app served by a Node server hosted on Heroku.

We are using Plotly for our graphs.

### Problems & Solutions
The biggest problem we have faced so far has been integrating our app into the admin dashboard on Shopify. After trying several outdated SDKs (Sinatra, Rails, Node) over a few weeks, I decided to build my own Rails backend from scratch, and our app is finally integrated in the admin dashboard!

We are currently figuring out what data we need to query from Shopify so that we can accurately do our forecasting. We are not sure if we want the frontend or the backend to do the bulk of the processing, but we are leaning towards the backend. After we do the processing, we just need to hook the JSON data up to our graph, and we will have a nice MVP for our startup friends.
