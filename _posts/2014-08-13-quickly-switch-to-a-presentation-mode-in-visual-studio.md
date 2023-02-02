---
title: "Quickly switch to a \"Presentation Mode\" in Visual Studio"
tags:
  - Visual Studio
---


As I prepared to give a [presentation](http://www.meetup.com/TechnologyGrows/events/199648072/) tomorrow night, I stumbled upon a [great article](http://blogs.msdn.com/b/pstubbs/archive/2010/06/16/presentation-mode-in-visual-studio.aspx) explaining how to setup Visual Studio for a "presentation mode." Presentation Mode are the font sizes required so the folks sitting in the back row don't repeatedly say "can you zoom in a little?"

I've [written](http://jason.famularo.org/presentation-considerations) about presentations before, but failed to go into any detail about configuring your IDE of choice. Mine for tomorrow will be Visual Studio. Since it's been a while since I've presented, I didn't quite remember the required settings to change the fonts. And Visual Studio has a lot of settings:

<figure class="full">
  <a href="/assets/images/quickly-switch-to-a-presentation-mode-in-visual-studio/i8khh6mxukafma.png"><img src="/assets/images/quickly-switch-to-a-presentation-mode-in-visual-studio/i8khh6mxukafma.png"></a>
</figure>

Thankfully, I found the article I mentioned above, and saved myself a small fortune of time trying to find and toggle all the correct settings. I've perfected the following quick process for my presentations.

## 4 simple steps to a better presentation

Step 1: [Download](https://raw.githubusercontent.com/Fammy/vs-presentation-mode/master/presentationmode.vssettings) this Visual Studio settings files

Step 2: Import into Visual Studio via the Tools->Import and Export Settings menu item

* Select "Import  selected environment settings" and click "Next"
* Select "Yes, save my current settings". Do this so you can revert back after your presentation. Type in a name, I called mine "dev.vssettings", and pick a folder to store them in. Click "Next"
* Click "Browse..." and find presentationmode.vssettings. Click "Next"
* Leave all the defaults, and click "Finish"

Step 3: Give your presentation with fonts the back row can read

<figure class="full">
  <a href="/assets/images/quickly-switch-to-a-presentation-mode-in-visual-studio/2gqazflstjuceg.png"><img src="/assets/images/quickly-switch-to-a-presentation-mode-in-visual-studio/2gqazflstjuceg.png"></a>
</figure>

![Shibe](/assets/images/quickly-switch-to-a-presentation-mode-in-visual-studio/shibe.jpg){: .align-left}
Wow, such big

Step 4: Revert back to your original settings by repeating Step 2 and choosing your saved settings (you did save them, right?!)