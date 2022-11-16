---
title: "Why you have to get a paper document signed to update the database"
categories:
  - Blog
---


A term I've used to describe various IT organizations in the past is "maturity". A more mature IT shop will have a standards, practices, and other safe guards to ensure that production, testing, and development environments are functioning at all times. A less mature IT shop will just "wing-it", doing whatever it takes at that particular moment to put out the fire at hand. They've yet to see many of the various problems that can occur.

One thing I've noticed at the "mature" organizations is the need for a signed piece of paper requesting a change to the database. For an outsider (I was a consultant in a former life), this seems absurd on the surface. Why do I need to sign a piece of paper? We work with computers! If you take a step back you'll see the bigger picture. It's a safe guard. The extra steps make multiple people put thought into what is about to happen, including the developer, DBA, and project manager. But how did we get there? Let's start at the less mature organization and work our way up. Please note these are generalizations.

## Starting point: Anything goes

Initially, the IT organization may exist of only a single or few developers. In this case, the sole developer may or may not have a development database that gets updated. Once this hopefully-existent database is tested with the new code changes, it's deployed directly to the production database. The deployment is done through the path of least resistance: copying the website directly from the developer's computer and using the GUI tool that came with the database to make the database changes manually.

## Point 2: We have a problem

The above procedure works fine for a while, but the developer makes a simple mistake. He or she was working late on a Friday and forgot to add the new column to one of the tables. Production isn't working on Monday and the owner of the small company is angry no orders were taken over the weekend. (Feel free to insert your own story here about what whom this IT organization supports.) The developer vows to "get things right" from now on and makes an informal step of writing a SQL script to apply the changes. The other developer (my, how we have grown!) reviews it prior to release and tests it on his local database. The problem is generally resolved. Small refinements are made throughout the next few deployments.

## Point 3: Sizable concerns

The business is successful and the development team is now four or five strong. They've even convinced the management team to hire a tester. Things are great. The developers and tester often talk about "how we can do deployments better" and "how we did it at my last company". A few processes are discussed, implemented, and enjoy relative success. Deployments are no longer scary! But something unexpected happens on evening after a deployment. The database server runs out of disk space. No one is a proper DBA, so it takes hours to figure out and recover. Unfortunately it's now six in the morning. The Monday morning retrospective is going to be painful.

## Point 4: A team effort

It's now years later. The business is more than just successful. IT is an official division, and has its own suite in the office complex. Things are rocking. Deployments are scheduled for Friday evenings. Hotfixes go out as needed, but in a controlled fashion. A project manager has been hired to coordinate all the various sub-projects that have sprung up. Gant charts line cubicle walls, a library of project document templates exists on the shared drive, and in the corner of the suite, alone, sits a sole database administrator. He's pretty good and handles a lot of the infrastructure requests as well (and has had no luck getting that network engineer position approved he's been lobbying for).

A divide has occurred between and within the teams. There's the dev team, the test team, the analysis and management team, and the DBA "team". A single guy makes a team, it seems. The DBA is tired of the developers and their unoptimized queries and DDL changes. He's tried lobbying for some sort of change, but the dev team "just runs everything" anyway. And besides, the project manager only cares about deadlines and budgets. You spend how much on database licenses but can't hire a second DBA? One more screw up by the dev team and he's going to threaten to quit.

## Point 5: Maturity

A few years later and IT has all the kinks "worked out". The teams know and fulfill their roles. Standards have been in place for a few years, and systems written years ago are now up for a rewrite. A particularly tricky replacement of some of the original systems — how are those things still working — goes live this weekend. A document has been produced that illustrates the roles each team member plays. The current system goes offline at seven in the morning on Saturday and the new one should be online by noon.

The big day is finally here. One of the managers has brought bagels and orange juice, although no one knows why he keeps bringing the salmon spread. It almost never gets opened, let alone touched. The first step is to ensure the nightly backup of the database was successful. After a few minutes, the green light is given and the development team lead gives the go ahead to the infrastructure team to apply the deployment package. In the meantime, the database team starts the database migration.

Then something goes wrong. Horribly wrong. Wrong enough to make any other problem the company has had look weak in comparison. Every contingency was discussed and planned for. The migration was run multiple times against a clone of prod. How could this happen?

After much discussion, much chastising, and many long hours, the development team lead explains to the rest of IT that one of his team members made a slight change to the migration on Friday. There was a new scenario in the last production refresh that didn't migrate correctly. Perhaps if it didn't take a week to get a refresh they would have caught it sooner. A meeting had been held on Thursday to discuss options, and project manager agreeing with the need for the change, but not really understanding it, approves the change.

The database team instantly objects. "We weren't involved". The development team lead explains, "we didn't think you needed to be. It was a simple change. Low risk." QA wonders why they weren't in the loop at all. The blaming goes on for a week and the manager finally has enough. Starting next release, a new policy goes into effect. Each change made to the database must be reviewed, approved, and tested by the database team. Everyone reluctantly agrees.

## Epilogue

It's months later. The dev team hates the "paperwork". Submitting the SQL scripts to the database team is pointless. They either approve them without looking or reject them based on some misunderstanding. Meanwhile, the database team is sick of all the complaining, as well as the paperwork. The dev team submits script after script. There has to be a better way.

## Recap

This story is absurd, and only partially based in the reality of my career. Hopefully it illustrates an important point. Ludicrous decisions don't get made overnight. There are usually years of justification behind them. At the time they are made, they seem like the right decision. No one willingly chooses to have signed paperwork. It's a series of mistakes over years that leads to this result.

I only ask you be pragmatic when making these decisions.