---
title: "Errors of omission"
categories:
  - Blog
---


I've long maintained that the hardest errors to find in a software application are those of omission. Omissions can be many things, but ultimately are missing data that was not noticed or changes in functionality that did not occur. Depending on your application, missing data or functionality can be annoying, costly, or worse.

## If it doesn't happen, it's not an error, right?

When determining how to test an application, you often test based on what you expect the application to do. It's a very reasonable approach, right? Given some input A, expect result B. You're happy and move on. But what about C? It doesn't always occur — should it have occurred when B occurred? How can you be sure? In fact, there are probably conditions when C should not occur. This just got complicated.

## How do you find something that's not there?

Sometimes the volume of data is overwhelming. Imagine verifying that a 40 page document isn't missing a word. That's not trivial. A previous project of mine was to ensure a six volume set of laws got printed correctly. Not only did it have to look right and contain all the new content, but we had to make sure none of the old content didn't get changed by accident.

Never mind the small fact that the law of the land needed to be represented accurately, replacing a volume within that set was very costly. It can be costly to your organization to make errors. (As an aside, corrections where done as single page replacements when possible. Stick the new over the old, and go about your business.)

## Controlled testing

The system we replaced on that project consisted of a mainframe application and lots of human input and proofreading. The proofreaders checked not only the content that changed (added, edited, or deleted), but the surrounded content as well. Although an inefficient use of human resources, it does provide a simple solution: testing against a known state.

The only way to keep your sanity when doing these large checks was to check against a known, or controlled, source. You can simulate this in your acceptance testing or even your unit or integration testing. Be sure that the source data you are verifying against is accurate, and the authoritative source.

## Only test affected functionality and data

Six volumes takes a long time to read, let alone proofread. How does one ensure that content doesn't go missing or changed by accident? Each book was broken into chapters. On average, 10% of the chapters changed each year. It was mostly safe to proof only the chapters that changed (and even then, sections within those chapters). There was a chance that a chapter or section could be omitted, but safeguards where in place to ensure they were still there. The moral of this example is to work smarter, not harder. Only test what you have to. You can test more, but never less.

## Knowing, half the battle

The key is to know when to look for errors of omission. The first step (for everything, it seems) is to admit you have a problem. Once you know to look for errors of omission, you can test for them as well. Be sure to limit what you test intelligently, and test against the authoritative  source. In time, you'll get better at spotting the circumstances in which an omission can occur.