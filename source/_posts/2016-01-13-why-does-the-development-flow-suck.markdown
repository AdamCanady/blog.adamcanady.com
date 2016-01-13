---
layout: post
title: "Why does the development flow suck?"
date: 2014-12-15 00:03:07 -0600
comments: true
categories: 
---

After writing about my idea for an <a title="Integrated Design-Development Environment (IDDE)" href="http://blog.adamcanady.com/2013/integrated-design-development-environment/">Integrated Design-Development Environment</a>, it occurred to me that there's a lot of unnecessary hassle in all stages of development and deployment of web applications. It takes hours to get a development environment set up before you can even start working on a specific piece of code. Then, when launch-time arrives, it takes at least as long to get everything in line to launch the thing. While it's not exactly a fair comparison, I could go to one of several dozen hosting companies and launch a WordPress instance for about $5/month. Then, the only remaining step is to actually log in and write content.

Many people are "full-stack" developers, meaning they'd handle everything from launching a VM, configuring a web server, installing dependencies, to putting together the application's backend and frontend. Not to mention some marketing and content creation on top including SEO, social media, and email campaigns.

All that is great, and there's something to be said for knowing everything about your application from top to bottom (or bottom to top, in this case), but it just doesn't have to be that complicated 99% of the time. For the select few who absolutely need to create custom directives in nginx to save nanoseconds on requests - this article is not targeted at you. This is for the people who want to use a well-known stack to rapidly prototype an idea they had for a web app.

We already have have awesome tools like <a href="https://www.docker.io/">Docker</a> and <a href="http://www.vagrantup.com/">Vagrant</a> to ease the transition between development and deployment. Just today, I read about <a href="http://jumpstarter.io/">Jumpstarter</a>, a company that is trying to make a difference in this space. While their efforts are promising, I have yet to see their services in motion. Moreover, they're currently only focused on PHP based webapps like Joomla, WordPress, and Drupal.

Even with these tools, there's still undoubtedly a lot of room for improvement in the field of "the flow" (as Jumpstarter refers to it). For a new "full-service" technology to succeed in this area, I think these steps are crucial:
<ol>
    <li>Focus on a particular flow that is popular enough that it is used by many, but new / unpopular enough that not many people have optimized it yet.</li>
    <li>Develop a set of web-based tools that makes it easy to collaboratively:
<ul>
    <li><strong>Design the application</strong> - wireframes, drawings, etc.</li>
    <li><strong>Develop and test</strong> - possibly even a hosted test that would allow you to send functional prototypes to testers, clients, colleagues, etc.</li>
    <li><strong>Deploy.</strong> One click to a live VM - either the user's via SSH or partner with a service like Linode, AWS, or DigitalOcean)</li>
    <li><strong>Manage versions</strong> - integrate with issue tracking</li>
</ul>
</li>
    <li>Promote, iterate the tools based on feedback
<ul>
    <li>Maybe they want a desktop-based environment or mobile admin tools</li>
</ul>
</li>
    <li>Create educational tools that would literally walk someone through creating an application using your flow</li>
    <li>Add ability to import current (already deployed) projects into 'the flow' - or even just parts of applications, like development and version control so people could take advantage of the tools in a modular fashion.</li>
</ol>
That last point is crucial. If you can show people that they can import their current, super messy projects into your environment, that opens up a whole new world of customers.
