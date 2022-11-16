---
title: "The importance of releasing"
categories:
  - Blog
---


An "old" adage in development is "release early, release often". This is a form of iterative development which allows for lack of functionality initially, and additional function in short releases afterwards. It's helpful, because it gets your site in front of real people, quickly.

I recently tried this approach with [machine2date](http://machine2date.apphb.com/) and [SharedBetween.Us](http://sharedbetweenus.apphb.com/)

machine2date is a site that focuses on one thing, converting "computery" dates into dates people recognize. If you do JSON or XML in your development, dates like "\/Date(1240718400000)\/" don't mean much to anyone but a Unix time programmer (it's ticks since January 1st, 1970 at midnight.)

SharedBetween.Us started out as something that was much simpler than what it is today. It's a simple task list that can be easily shared between users. It was originally "SharedLists", but the domain was taken, so I lazily renamed it to its current name.

Both of these sites are easy to make changes to and deploy quickly. A lot of the friction in deploying is managing releases and doing the physical deployment. The combination of [git](http://git-scm.com/) and [AppHarbor](https://appharbor.com/) makes setting up a new site stupid-easy. In 15 minutes, you can likely do all of the following:

1. Create an AppHarbor application
2. Buy a domain name
3. Setup DNS to point to AppHarbor
4. <code>git init</code> (in the root of the application or webpage you'd like to deploy)
5. <code>git add .</code>
6. <code>git commit -m "your comment here"</code>
7. <code>git remote add appharbor http://username@your.appharbor.url…</code> (Your URL is easily viewed on the AppHarbor application page after your complete step 1)
8. <code>git push appharbor master</code>

That's it. To update the site, you may need 3 minutes. Just do the following:

1. Make update to application or webpage. Trivial changes or spelling corrections no longer need to wait for a "full release".
2. <code>git add .</code>
3. <code>git commit -m "your comment here"</code>
4. <code>git push appharbor master</code>

AppHarbor explains it all [here](http://support.appharbor.com/kb/getting-started/deploying-your-first-application-using-git). There's not an excuse to do an initial release. Or a simple update.