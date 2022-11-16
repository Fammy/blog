---
title: "Patching vs. merging"
categories:
  - Blog
---


One of those "fun" activities developers look forward to is merging code from one branch to another. The scenario I personal use most is merging changes from the trunk back to the branch that is about to be released.

For the last few releases I've deviated from my normal usage of the built-in merging capabilities of (Tortoise)SVN. Instead, I've made a patch of my changes just before I've checked them in (to either trunk or the branch, wherever I'm working). I then apply the patch to the other.

The upside is it's a lot easier and generates less mess. Perhaps I merge to infrequently and forget the "best" way, or run into troubles because SVN is, well, SVN. The downside is I lose the context of the merge. Nothing ties to the commits together (arguably, I could commit at the top-level of the repository, but I'm not currently setup to do that).

Is this good, bad, or just preference? I'm not sure, but I'm a fan of anything that removes development friction.