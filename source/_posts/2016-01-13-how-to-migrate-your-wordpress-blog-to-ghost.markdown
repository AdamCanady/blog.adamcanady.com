---
layout: post
title: "How to migrate your WordPress blog to Ghost"
date: 2014-12-20 00:05:06 -0600
comments: true
categories: 
---

It's very straightforward to migrate your WordPress blog to a Ghost blog. First, we'll start off by exporting everything out of WP, then we'll set up Ghost, import everything, and finally tweak the setup so our old URLs are supported.

### Get data out of WordPress

1. Install the Disqus plugin and export your comments to Disqus.
2. Install the Ghost plugin and obtain a .json file containing all of your post content and metadata.

### Set up Ghost

1. Provision a Ghost installation. Since Ghost is an early-stage project, it's easiest to start from a pre-setup image, like the one offered by [DigitalOcean](http://www.digitalocean.com).
2. Log into Ghost by navigating to http://your-ip/ghost and creating an account. More info on this process [here](https://www.digitalocean.com/community/articles/how-to-use-the-digitalocean-ghost-application).

### Move everything over

1. Import your .json export from WordPress into Ghost by navigating to http://your-ip/ghost/debug and clicking import. Keep in mind, this will overwrite your login information with the root user used in WordPress.
2. Add Ghost to your theme by adding `<div id="disqus_thread"></div>` to your theme's post.hbs anywhere after `{{content}}`. This will vary by theme.

### Customize previous URLs
This is probably the trickiest part of the migration. Since Ghost is in very early development. We'll need to add a redirection that follows our previous scheme. For me, I added the following code to line core/server.js in line 371 after the block containing the `// ### Frontend routes`:

    server.get(/^\/(2013\/?).*/, 
        function redirect(req, res) {  
            res.redirect(301, req.url.substr(5));
        }
    );
    
Your mileage may vary - mine was easier because all of my posts in WordPress were preceded by `/2013/blog-permalink`.

Shoutout to these posts for help transferring my blog:

* [Adding Disqus to Ghost - Gilbert Pellegrom](http://ghost.pellegrom.me/adding-disqus-comments-to-ghost/)
* [URL Redirection in Ghost - Alex Jegtnes](http://jegtnes.co.uk/how-to-implement-url-redirection-in-ghost-0-3/)
* [Using Ghost with DigitalOcean - DigitalOcean](https://www.digitalocean.com/community/articles/how-to-use-the-digitalocean-ghost-application)
