---
layout: post
title: Why I moved my blog to Jekyll
---

I recently migrated this blog from WordPress to [Jekyll](https://jekyllrb.com/).

Wait. Why would anyone exchange a comfortable CMS for static site generator? 

Why not WordPress?
------------------

I only ever used most basic features of WordPress.

I’ve never really needed user registration or other “advanced” features. I’ve never been a fan of comment sections on blogs either. It always felt like most comments were either bots or people trying to acquire backlinks for their websites (this might not be true for more popular blogs, but it certainly was true for mine). At some point, I got tired of moderating dozens of spamy comments every month and decided to turn them off completely. WordPress is a very powerful tool, but it has its drawbacks. And as in my case most features were left unused, I started to look for a simpler, lower maintenance alternative.

Static site generators
----------------------

Jekyll is a static site generator - it generates “static” HTML files containing content you provided. It allows you to write blog posts in [markdown language](https://guides.github.com/features/mastering-markdown/) and it takes care of everything else.

This has many benefits: static sites load faster, and can be hosted on [GitHub pages](https://pages.github.com/) \- there are no hosting fees and it supports custom domains (that are very easy to set up). I used an extremely cheap hosting plan before, and Github pages turned out to be faster, more reliable.

Wordpress installation can never be as secure as a static site. A lot of effort is devoted to keeping Wordpress free from security vulnerabilities, but the most popular CMS on the internet is a very attractive target. With a static site, there are no security updates that have to be installed. No maintenance necessary.

With Jekyll, SEO optimisation is quite [painless](https://blog.webjeda.com/optimize-jekyll-seo/) and there’s a great support for code snippets (syntax colouring, line numbers) out-of-the-box.

It’s not all sunshine and rainbows
----------------------------------

Wordpress just works. It provides you with an online editor and all you’ll ever need to manage your website is a web browser.

Jeklly is not that easy to set up (Quick Start guide is a little misleading) and I can’t imagine a non-technical person using it without feeling overwhelmed.

There is no way to schedule posts.

There is no server-side, so you will need to use external services to enable features like comments or contact forms (if you need them).

Publishing is not as simple as pressing a button.

The only WordPress feature I really miss is post-scheduling, but it can be automated (fun side project idea!) and I don’t publish enough to be affected by this anyway. Simplicity, speed and availability of free hosting compensate for the setup overhead, and despite Jekyll’s shortcomings I’m very pleased with the change and I would recommend that you try it if you’re tired of dealing with Wordpress.
