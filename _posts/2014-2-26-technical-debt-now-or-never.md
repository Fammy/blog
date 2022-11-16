---
title: "Technical debt: now or never"
categories:
  - Blog
---


I started a new project at work a few months ago. Literally, a new project, as in File -> New Project. It was very liberating (and scary) to not worry about the company's main code base that was 10+ years old. While in decent shape, nothing that old is going to be without problems. I call those problems [technical debt](http://en.wikipedia.org/wiki/Technical_debt). (You also don't get all the niceties and helpers that someone else has spent 10 years perfecting, but I digress).

Like any project, my new project started accruing technical debt. I was faced with the decision that every project is: pay back the debt or build shippable (and thus profitable) features. Most projects choose the latter. That's probably the right decision in some cases. But being scared that one day the new project would be the old project, I couldn't live with the decisions made weeks earlier. They didn't sit right with me.

The other developer and I decided to fix them. It was now or never. Once we got out of the "build a thing that compiles and does the first thing" and into production, there wasn't going to be a lot of time to circle back around. We'd be any other project at that point. Always enhancing, always maintaining. As we found the nasty regions in the code, we tore them out and replaced them with something better.

Technical debt is said to accrue interest. The longer it sits around, the more code that gets piled on top of it that makes it harder to change and fix. That's one reason why we were able to pay so much back. The cost to do so was not yet high.

I'm not saying you can't go back and pay back your technical debt at some point in the future. I think you should. Business needs in general don't allow development teams the time they need to fix everything. We sometimes settle for what's the worst code, or what's easiest to fix. Slow and steady in those cases.

If you get a chance to pay back your debts, do so. The sooner you pay them back, the easier it'll be. And you'll feel a lot better about the code you leave behind.