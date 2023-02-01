---
title: "Lessons learned from changing blogging software and moving to a new host"
---


I recently decided to move my personal website to [AppHarbor](https://appharbor.com/). (If you are a .NET developer and haven't had a chance to check out AppHarbor, stop reading this and click on the link. Seriously. They are awesome.) The hardest part was moving my WordPress-based blog, which is based on the [PHP](http://www.php.net/) scripting language. Don't get me wrong, [WordPress](http://wordpress.org/) has been pretty awesome, is widely supported, and did everything I needed, and more. I ran across [Phalanger](http://www.php-compiler.net/), which is PHP for .NET. In a few simple steps, I was able to install it and get my existing WordPress blog running on it. It was awesome. Decidedly less awesome was trying to get it to run on AppHarbor.

In the end, I decided to abandon the idea of running PHP on .NET. I'm pretty sure I figured out most of the hurdles that would have prevented it from running on AppHarbor, but it wasn't worth the hassle and fragility of the whole thing. Instead, I decided to find a .NET blogging engine, and settled on – wait for it – [BlogEngine.NET](http://www.dotnetblogengine.net/). It seems to do most of what I need, and seemed easy to install. In the process of changing blogging software (and domains, from [www.famularo.org](http://www.famularo.org/) to blog.famularo.org), I learned the following.

## 301 Redirects are essential

A secondary goal was to keep highly ranked, useful posts (both of them) both highly ranked and properly linked to the Google result. The answer is pretty simple: sending an [HTTP status code of 301](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes#3xx_Redirection) at the former URLs. I accomplished this by creating a new section in my web.config under the system.webServer element. Here's an example of one such entry:

	<configuration>
		<system.webServer>
			<rewrite>
				<rules>
					<rule name="rule1">
						<match url="(.*)(finding-unused-css-with-google-chrome)(.*)" ignoreCase="true" />
						<action type="Redirect" url="http://blog.famularo.org/post/2011/05/03/Finding-unused-CSS-with-Google-Chrome.aspx" redirectType="Permanent" />
					</rule>
				</rules>
			</rewrite>
	<- The rest of your web.config -->

Since the ASP.NET engine fires before PHP, IIS successfully redirects to the new site. I didn't try to get fancy and create a single regex for all nine posts. Instead I hand crafted each one, and added a default for all other traffic to /blog.

I was already using Feedburner and updated it to point to the new RSS feed. I shouldn't lose my (four) subscribers. A loss of even one would be catastrophic, statistically.

## Load-balanced "cloud" hosting has some hidden surprises

This issue was the only one to surprise me along the way. Everything thing else went according to plan, even if some learning was included (a bonus!). I tested everything locally, including the remote connection to the database. All that was left was to deploy and enable the 301 redirects. As soon as I deployed, about 20% of the links included some (seemingly) random port. I used IIS Express to test, and instantly though I'd cached some sort of URL in the database or app_data. After searching, I read an article on the AppHarbor support form. The load balancer does "weird" things to URLs, namely when asking for the absolute URL of a server, it gives you the absolute URL, including port. After downloading the source code for BlogEngine.NET, I found the problem. And decided to fix it.

## < 10 Posts? Just copy and paste

If I was a prolific writer, I would have had a huge problem importing data into the new system. Instead, I just copied and pasted each post. Two caveats: formatting and images. Formatting didn't come across in all instances. I also changed some H2 tags to H3 to be more consistent with BlogEngine (H2 is the post title, and I strive to be semantically correct). Images also weren't playing nice with the rich text editor (upon saving). I solved this by changing BlogEngine to store files in the database. In retrospect, this is a smart decision for any cloud-hosted application. Your files need to be in a common location (because you ideally only want one logically set), either in a cloud database or in a cloud file share (like [Amazon S3](http://aws.amazon.com/s3/)).

## Open Source saves the day

I had two problems with BlogEngine.NET. The first is described above, under the load balancing topic. The second was with Diqcus, the popular commenting system. My (four) discuss comments didn't appear to migrate, even though I picked the super-useful "follow 301 redirects" option. Disqus seemingly had the right data in the admin dashboard, but it wasn't showing on the site. After reviewing Disqus' documentation, I realized the JavaScript on the blog calling the API to get the comments wasn't sending all the "recommend" information. That's probably the nice way of saying "required". In the end, I decided to do the same thing that I did with URL issue. Fix the source code.

Open source is great for this. I have the source, I can read and change as needed. I plan on sending my changes back to the project, as someone else will likely need them.

## Summary

The migration had a few bumps, but after hacking some code (always fun, no sarcasm intended), I was able to get the result I wanted. And I will get to save $9 a month in web hosting costs, at least until the blog gets popular. At the current rate, that'll be the year 2113. Only 102 years to go!