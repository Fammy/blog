---
title: "Finding unused CSS with Google Chrome"
---


With the advent of [jQuery](http://jquery.com/) and its [selector engine](http://sizzlejs.com/), I've gotten a lot better at writing accurate stylesheets. But I'm never 100% sure if all of my CSS rules actually point to something. This [tweet](https://twitter.com/#!/ryan/status/63367737765933056) reminded me of my lack of CSS skills. And a few days later I stumbled upon a gem in Google Chrome.

1. Open the "Developer Tools" in Google Chrome by hitting "Control-Shift-I" (Windows, your OS may vary). You can also find it in the wrench menu under "Tools".
2. Navigate to the "Audits" tab.
3. Optionally, uncheck "Network Utilization". It's not need for the CSS auditing.
4. Select "Audit Present State" and click "Run".

After following those steps, the results will display on the same tab. One of the results may be "Remove unused CSS rules". If it's not there, you are the best CSS artist in the world. For the rest of us, expand the tree.

You'll get stats (my home page doesn't use 91% of its CSS — a case for not having monolithic stylesheets) as well as a list of files or inline CSS that can be optimized. Expanding each item will show you the culprits.

I also suggest reading the other results of the audit. They're good too.