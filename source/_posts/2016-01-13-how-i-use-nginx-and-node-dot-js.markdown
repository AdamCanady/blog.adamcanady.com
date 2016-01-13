---
layout: post
title: "How I use Nginx and Node.js"
date: 2014-10-13 00:00:06 -0600
comments: true
categories: 
---

As I mentioned in the piece on <a href="http://blog.adamcanady.com/2013/my-web-stack/">my web stack</a>, I currently use Nginx to manage requests on a server and set up different hosts. Here's how I do it.

<a href="http://nginx.org/">Nginx</a> is great because it's extremely fast and very configurable. Here, I'll share a basic configuration that works well for me to host a few sites on the same VPS.

Basically the idea is to figure out where the request is coming from, then direct it to the correct application (I run Node apps on different ports).
<h2>Defining the server group</h2>
First off, we have to tell nginx where our Node application is running.


     upstream subdomain.domain.com {
         server 127.0.0.1:3000;
     }

<h2>Defining the server itself</h2>
Now we define the server, telling it where to listen, what to listen for, and where to direct requests. In the case of node, we want it to pass requests off via proxy to the server we defined earlier.


    server {
        listen 0.0.0.0:80;
        server_name subdomain.example.com;
        access_log /var/log/nginx/subdomain.example.com.log;

        # tell nginx to forward all requests to the proxy
        location / {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header Host $http_host;
            proxy_set_header X-NginX-Proxy true;

            proxy_pass http://subdomian.example.com/;
            proxy_redirect off;  
        }
    }


And that's all you need to direct traffic to a Node server! Though if you'd like Nginx to handle static files with it's insane speed, stick around.
<h2>Handling static files</h2>
If you want to get fancy, you can have Nginx handle static traffic instead of Node. Just place something like this below the previous location block.


    location ~* ^.+\.(jpg|jpeg|gif|png|ico|css|zip|tgz|gz|rar|bz2|pdf|txt|tar|wav|bmp|rtf|js|flv|swf|html|htm)$ {
        root /var/www/subdomain.example.com/public;
    }

<h2>Putting it all together</h2>
Now that everything is configured correctly, we need to figure out how to put it in the right place to make it effective. I'll assume you already have nginx installed on your machine. First, we'll need to create a configuration file in the <code>/etc/nginx/sites-available/</code> directory. For example, my file is located here: <code>/etc/nginx/sites-available/example.com</code>

This whole file looks like this:


    upstream subdomain.domain.com {
        server 127.0.0.1:3000;
    }

    server {
        listen 0.0.0.0:80;
        server_name subdomain.example.com;
        access_log /var/log/nginx/subdomain.example.com.log;

        # tell nginx to forward all requests to the proxy
        location / {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header Host $http_host;
            proxy_set_header X-NginX-Proxy true;

            proxy_pass http://subdomian.example.com/;
            proxy_redirect off;
        }

        location ~* ^.+\.(jpg|jpeg|gif|png|ico|css|zip|tgz|gz|rar|bz2|pdf|txt|tar|wav|bmp|rtf|js|flv|swf|html|htm)$ {
            root /var/www/subdomain.example.com/public;
        }
     }


Now that we have this site in our sites-available folder, we must tell nginx that it's enabled as well. The easiest way to do this is to create a system link to the file in the sites-available folder in our sites-enabled folder, like this: `ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com`

Finally, we'll need to restart nginx like this: `service nginx restart`
and everything should work once you route the DNS A record of your domain to this IP address and wait for the changes to propagate through DNS (usually takes an hour, but can take up to 48)
