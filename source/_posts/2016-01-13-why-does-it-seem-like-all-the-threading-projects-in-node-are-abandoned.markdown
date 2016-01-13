---
layout: post
title: "Why does it seem like all the threading projects in Node are abandoned?"
date: 2014-12-20 00:04:16 -0600
comments: true
categories: 
---

I was recently looking for a threading solution in Node and, to my surprise, many of the projects have been abandoned! Looking at <a href="https://github.com/xk/node-threads-a-gogo">Threads a go go</a>, and <a href="https://github.com/audreyt/node-webworker-threads">webworker-threads</a>, for both of which the last commit was at least 6 months ago. It seems like there's no demand for a solution to running long running or blocking tasks in node (aside from fibers or child_process).

I can't even get Threads a go go to install with the latest version of Node (and haven't been able to do so for over 4 months).

Is it really the case that these tools are not necessary? If so, what solutions have people found for handling long processes?

<strong>Update:</strong> Even <a href="https://github.com/laverdet/node-fibers">fibers</a> seems to have gone a long time without an update.

<strong>Update 2:</strong> Welcome HN folks! Discussion <a href="https://news.ycombinator.com/item?id=6834179">here</a>.
