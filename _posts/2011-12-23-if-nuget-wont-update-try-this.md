---
title: "If Nuget won't update, try this"
---


The newest version of [Nuget](http://nuget.org/), version 1.6, wouldn't update on either of my computers from within Visual Studio. I'm not certain why, but the fix is simple. Run Visual Studio as administrator, go the Extension Manager, uninstall Nuget, restart Visual Studio, and reinstall. Don't bother uninstalling from Add/Remove Programs, [it's a trap](http://knowyourmeme.com/memes/its-a-trap)!