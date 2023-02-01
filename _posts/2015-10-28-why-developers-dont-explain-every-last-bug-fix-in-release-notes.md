---
title: "Why developers don't explain every last bug fix in release notes"
---


I've seen a lot of frustration by smartphone users when app release notes are vague about what's actually being updated. We've all seen the dreaded "bug fixes and performance enhancements". We fall in love with our apps, love to see updates, but developers aren't spending the time to explain every last nuanced update. What's up with that? Power users thrive on this information. So why don't developers detail the entire set of changes?

As a power user, I feel this frustration too. I really do want to know what is being updated. There may be a particular annoying bug that I'm waiting to get fixed. Maybe it's a new feature that I might not know about otherwise. But as a developer, I have a second set of concerns that sometimes conflicts with what users want. So here's why developers don't (always) explain every last bug fix in release notes:

## Time

Often, release notes are an afterthought, something that's done quickly as an app approaches release. Developers, or someone on the team, is given the assignment to write release notes. The team wants to see what updates in the store just as much as you do, and equally as soon. Release notes are an (important) task that gets ignored until it has to be done. And when time is short, shortcuts get taken.

## Embarrassment

No software is perfect. No app is bug free. Developers are not coding ninjas (regardless of what recruiters think). The developer may feel that certain bugs reflect poorly on their skills. Writing quality software is difficult, and everyone makes mistakes. Sometimes those mistakes are extremely dumb and best swept under the rug, right?

## Security

Some fixes are security related. It's not always wise to announce all the security problems your app had. Users may not update, and installing old versions of apps is not hard. If you announce your security problems, you potentially make it easier to exploit the app.

I'm not saying this is the correct way to handle security issues. I'm saying this way of thinking easily enters your mind. No one wants their app to be "hacked" or exploited.

## Limited space

Did you know that Google only allows for 500 characters in the release notes field? That's stupid short. And it's also not enough to list all the bug fixes that occur in a single app release. More important features will get the majority of the space in the release notes and bug fixes get lumped together, if mentioned at all.

Apple is more generous and gives 4000 characters. That's almost enough space to write four [Javascript demos](http://js1k.com/2014-dragons/demos).

## Laziness

Stop me if you've heard this before: developers are lazy. We work hard at being lazy. It's an overused trope, but has some truth. The last thing a developer wants to do is write release notes. Most of us like writing software. When preparing a set of release notes, it can be very time consuming to review every last issue that was fixed. It's just easier to say "yo, we fixed some bugs" and actually go and fix some more bugs.

## The middle ground

I'm not saying I agree with all the reasons above. I think there is a middle ground. Something between the spartan "bug fixes and performance enhancements" and a full copy of the commit log.

My personal strategy is to put the following in the release notes.

* New features
* Major enhancements and changes
* Significant bug fixes, especially if users have been reporting the issue

Users, I understand your frustration. I want to see good release notes. Hopefully it gets better. Especially frustrating are especially terse notes:

```
Bug fixes
```

(Google, I'm looking at you again ಠ_ಠ)