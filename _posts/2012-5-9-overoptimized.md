---
title: "Over-optimized?"
categories:
  - Blog
---


Recently, I've been dogged by a Subversion issue (and generally dogged by Subversion — Mercurial and Git are my new friends) that stumped me on and off for a few weeks. The dreaded error was a "Checksum mismatch". Essentially, the file downloaded from the server didn't have the content expected. It had been modified.

For those interested, the post that finally led to the fix is here:

http://subversion.open.collab.net/ds/viewMessage.do?dsForumId=3&dsMessageId=450635&orderBy=createDate&orderType=desc

The cause of the problem was that to the web server that served the files had stripping out "non-essential" content from HTML and JavaScript files, namely comments. For end users, that's great. Less bytes to download? Awesome, we saved an e-tree! But for a developer working on that particular file, those comments are (arguably) valuable. And required if you want to fetch a valid copy from the server.

I was the victim of an over-optimization.

This issue got me thinking: are we on the brink of over-optimizing "all the things"? Almost all content on the internet can be optimized in some way. HTML (and any text file) can be compressed (gzip, they call it), JavaScript and CSS can be "minified" and combined into a single file. Pictures, videos, and sound files can be compressed into lower resolutions, lower bitrates, or lower quality for faster transmission or because the eye or ear can't perceive the difference. The 1080p video from iTunes is not the same as the one on a Blu-ray.

In addition to these file-level optimizations, there is caching. Almost every point between the source and the destination has the opportunity to cache the content. What guarantees that we get the correct version of the correct file? Nothing, sadly.

Optimizations can fall into two basic categories: those done safely (lossless) and those done with a risk (lossy).

The risks of lossy optimizations are obvious: content is lost, changed, or whatever term you'd like to use to soften the effect. It may not matter most of the time, but someone or something at some point is going to depend on the full content. In this case, it was my sanity for 6 hours last week.

The risks of lossless optimizations are less-obvious. There is always the risk that the conversion did lose data, thus truly being lossy. But I'm finding the challenges and risks are more upfront, in the actual creation, and not the consumption, of the content.

I've been working with [Rejuicer](http://rejuice.me/), a pretty slick JavaScript and CSS minification tool. It's pretty easy to setup, and for basic organizations of files, a no-brainer. Soon after diving in, subtle issues crept up. Remember the "cascading" part of Cascading Style Sheets? If Rejuicer servers your files in an order you don't expect, the content has changed. It's now lossy. The same can happen with JavaScript.

The lesson to learn here is if you are depending on someone else for your optimizations, be sure you understand how they work. If you are consuming content, be aware that optimizations are likely being applied.