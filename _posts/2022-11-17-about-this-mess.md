---
title: "About this mess"
tags:
  - Blogging
---

## Here we go again

Every so many years I look at my blog or [personal website](https://famularo.org) and get that urge to tinker with it and try something new. And that time was recently, as I've moved my blog from [Svbtle](svbtle.com) to [Jekyll](https://jekyllrb.com/) hosted on [GitHub Pages](https://pages.github.com/). It all started when I tried to update Svbtle to use the newer Google Analytics setup, but found it was not supported. From that problem, I got [squirreled](https://www.youtube.com/watch?v=B-_oeTTQIH4) and ended up moving to a new blog host.
<!--more-->

## Why Jekyll?

Jekyll may not be the hot new thing, and as I get older—I mean more experienced—I realize that the latest thing isn't always best in the long term. Instead of basing things on a tech, I'm basing them on a format: [Markdown](https://en.wikipedia.org/wiki/Markdown).

Svbtle already used Markdown, so that part was (mostly) painless. I did end up using [svbtle-jekyll](https://github.com/bwhaley/svbtle-jekyll), a small Python tool that extracts Svbtle posts and puts them in Jeykll format (from what I can tell is [kramdown](https://kramdown.gettalong.org/) + a header). svbtle-jekyll required a few tweaks to get it to read the HTML correctly (it is 7 years old—it almost worked out-of-the-box!)

Now that my blog posts are in Markdown and stored in a [git repo I own](http://github.com/Fammy/blog), it should be easy to move them elsewhere if—and when—I decide to move to a new platform.

Jekyll also made it easy to keep the same URLs for my posts so I don't have to mess with [HTTP 301](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/301) redirects.

## Theming

In looking for Jekyll themes, I quickly found [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes), which is a very popular—if not most popular—theme for Jekyll. Once I made it through setup and dependencies, I was off and running. So now I am running on a static website that is free to host and doesn't look half bad.

## What's next?

Am I going to (re)commit to blogging more? No, but I'll try. At a minimum something new will come along in a few years and I may be tempted to switch to that. 😉