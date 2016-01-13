---
layout: post
title: "My web stack"
date: 2014-9-12 23:58:38 -0600
comments: true
categories: 
---

<p>This summer, I've had the great pleasure of learning how to use some of the most amazing technology. As someone still relatively new to software development (~4-5 years of informal experience, 2 years on the job), I don't consider myself a senior developer, however, I have learned quite a bit about how to lay out projects and what tools will be the most effective.</p>

<p>My background was mostly in WordPress and PHP based web applications until recently, though I've taken to starting new projects with the stack described here for many reasons, the most important of which is to quickly turn ideas into MVPs, which allows me to save time on development.</p>

<p>Without further ado, my (current) web stack:</p>

<ul>
<li><strong><a href="http://www.mongodb.org/">MongoDB</a></strong> -  Previously a long-time MySQL user, I found Mongo to be much more flexible, which was perfect for rapidly changing MVPs, allowing me to manipulate schemas and clone from development to production for launch with ease.</li>
<li><strong><a href="http://expressjs.com/">Express</a></strong>  -  Makes writing routes and serving up static files super easy in Node</li>
<li><strong><a href="http://nodejs.org/">Node</a></strong> - Something I just discovered this summer, but that has been around for a whopping <a href="https://en.wikipedia.org/wiki/Node_js">4 years</a>, it's been great to learn how to use this and work with a new (to me, coming from PHP) paradigm of web server programming</li>
<li><strong><a href="http://angularjs.org/">Angular</a></strong> - Though I'm still new to this one, I've seen its power and grace firsthand and have included it in a couple of my prototypes and plan to keep using it for future SPA (single page application) projects.</li>
</ul>

<p>This is also known as the MEAN stack, and the folks at <a href="http://mean.io/">MEAN.io</a> have set up a nice base package that automatically hooks everything up for you, including authentication and the templating engine, <a href="http://jade-lang.com/">Jade</a>, which I'll write another post on sometime.</p>

<p>Additionally, I take advantage of the following for many of my projects (I'll probably write better descriptions about these sometime):</p>

<ul>
<li><a href="http://getbootstrap.com/">Twitter Bootstrap</a> (for super fast, good looking web interfaces)</li>
<li><a href="http://mongoosejs.com/">Mongoose</a> (for interacting with MongoDB in Node)</li>
<li><a href="http://nginx.org/">Nginx</a> as webserver base to route requests from domain to Node.js instance.</li>
</ul>

<p>I'll write about my dev environment more in some coming posts, but feel free to tell me about yours in the comments!</p>
