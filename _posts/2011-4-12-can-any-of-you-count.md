---
title: "Can Any() of you Count()?"
tags:
  - C#
  - .NET
  - LINQ
---


LINQ, which stands for Language Integrated Query, isn't new anymore. It was introduced in .NET 3.5, which saw its release in November 2007. At this point, I feel it should be a core skill for any seasoned .NET developer.

But every now and then, I see LINQ that makes me cringe. Before you write a line of LINQ, you should understand that it has deferred execution. That means it's not executed as soon as it is called. Instead, the query waits as long as possible before returning results.

My personal philosophy is to take advantage of that delayed execution. The following line, when called needlessly, causes that cringing feeling I spoke of earlier:

	var results = (from o inobjects
		where o.something == "something"
		select o).ToList();

The ToList() forces LINQ to loop through all the items in that enumerable. That's all fine if it will always be executed, but what if the next line throws an exception? You've just looped through a possibly large collection for no reason. Perhaps this is a better example of a possible pitfall:

	var results = from o inobjects
		where o.something == "something"
		select o;

	if(results.Count() > 0)
	{
	  // Do something
	}

Oh my eyes! Not so bad you say? Let's consider what .Count() does. Unlike IList.Count, the .Count() extension method in LINQ doesn't know what the size of the enumeration is yet. It has to iterate over each and every item. The cost of counting is very expensive. When combined with Count() > 0, you can see that you have to count all the items just to see if you have any. What's the smart developer to do?

The Any() extension method is exactly what we want. It iterates the bare minimum number of times to determine if there are items. Logically, if (enumeration.Any()) is the same as if (enumeration.Count() > 0). But the cost of .Count() is a order of a magnitude higher.

While I am on a LINQ tirade, let's discuss .First(), my least favorite LINQ extension method. Often times, I come across the following code:

	var myThing = (from t in things
		where t.something == "something"
		select t).First(); // Or .FirstOrDefault()

Why does this concern me? It assumes any results after the first one are insignificant. What if two things match "something"? Did you expect that? What do you want to do with the second result? Apparently nothing.

For a resolution, I suggest using .Single() or .SingleOrDefault(). These extension methods are clear in their intent. I expect one (or zero or one for .SingleOrDefault()) items to come back. Any more, and an exception is thrown. I've avoided hard-to-find bugs by using .Single() instead of .First().

Please continue to use LINQ in your applications. But think of the implications of your next query. You may not save humanity, but you will save my sanity.