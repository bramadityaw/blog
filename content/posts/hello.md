+++
date = '2025-01-02'
draft = false
title = 'My First Open Source Contribution'
excerpt_separator = '<!--more-->'
+++
Hi! And welcome to my first blog post! I hope you stick around.

I made this blog using Hugo with the Tale theme, because I really like how it looks. I want to focus on the articles for this blog, and this theme suits that purpose.

Surely, nothing will go wrong. _<-- clueless_<!--more-->

Before I write anything, I decided to get a feel of using Hugo and test if the thing works or not. I made some dummy content and ran `hugo server -D` and got greeted by (more or less) this error.

```bash
no such template "_internal/google_analytics_async.html"
```

Great! Just what I wanted.

A quick internet search lead me to [this post](https://discourse.gohugo.io/t/build-error-on-v0-125-2-calling-internal-template-internal-google-analytics-async-html/49410). 

Seems like a quick fix. I just need to trim a few characters is all.

A neat thing about Hugo's themes is that they are installed in your Hugo project as git submodules. That means the source code is available to us and finding where the error happened is just a matter of `grep`ping. I deleted the '_async' fragment on the url and _voila_!

I realize I can contribute back to the theme and decided to make a pull request of my local changes. Thanks [EmielH](https://github.com/EmielH) for accepting my first ever pull request!
