---
title: "Word 2007 and em-spaces"
tags:
  - MS Word
  - Bug
---


Developing custom solutions for Word 2007 over the last year, I've run across some bugs that are particularly nasty relating to em spaces. What's an em space? It's a typographical character that is the width of an "M" (em) in a proportional font. There's also an em dashes (—) and en ("N") spaces and dashes. The en characters are the width of an "N", which is typically half the width of an em.

My client has a long history of using these characters in their publications, and naturally wanted to continue using them when we moved the process to Word. But soon after, we started to notice a few bugs.

The first was a copy and paste issue. When copying and pasting content with an em space between two instances of Word (i.e. you have two winword.exe processes running), the content around the em space switches upon paste. For example "First half[em space]second half" became "second half[em space]First half". This is not good, and the users were on the road to losing faith in our effort.

A team member figured out how to recreate the issue and I had the pleasure of submitting the bug to Microsoft. Many months later and the patch is finally available. It'll be rolled into the next service pack, but if you need relief before then, install the hotfix in [kb962872](http://support.microsoft.com/kb/962872/).

The second issue was the font of the em space character itself. When inserting into a document (via typing, pasting, or programmatically), the font was changing to Cambria Math. This font was physically a different size than the one we were using, and became apparent to users. Again I went through the same bug submission process, and [kb970942](http://support.microsoft.com/kb/970942) was recently released and fixes this issue.

I'm convinced Word severely mishandles this character and has more issues relating to it. Hopefully others don't have nearly as difficult a time as I dealing with em spaces.