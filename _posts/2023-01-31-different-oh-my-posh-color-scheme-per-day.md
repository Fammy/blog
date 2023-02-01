---
title: Different Oh My Posh color scheme per day
tags:
  - Oh My Posh
  - Terminal
---

## Briefly: what is Oh My Posh

[Oh My Posh](https://ohmyposh.dev/) describes itself as "a prompt theme engine for any shell." Basically, your prompt, or the line that shows up in your terminal/console/shell/etc that you type commands into, is very customizable. Instead of just showing your current path, or maybe your username and path, you can leverage Oh My Posh (and many other engines like it) to make things both colorful and informative.

I've chosen Oh My Posh over others because of its flexiblity, features and it gives me a consistent prompt on Windows, Mac, and Linux.

## Themes!

Oh My Posh has [many themes](https://ohmyposh.dev/docs/themes) showcasing a variety of  colors and [segments](https://ohmyposh.dev/docs/segments/path) (the parts of your prompt, such as path, git status, battery level, and so forth).

I personally started by copying the [Paradox theme](https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/paradox.omp.json) and customizing it. Recently, I decided to re-color my theme based on the Highway color scheme on the [Gogh website](https://gogh-co.github.io/Gogh/). Gogh has many great color schemes and I kept experimenting and thought: what if I used multiple colors schemes and rotated per day...

## Different color scheme per day (or hour/minute/second)

Using the [Go templates](https://ohmyposh.dev/docs/configuration/templates) within Oh My Posh themes, we can have a bit of logic and [choose a color palette dynamically](https://ohmyposh.dev/docs/configuration/colors#palettes).


Here's the logic related to palettes that choose a different palette each day. I've included 6 that rotate.

{% highlight javascript linenos %}
{
 "palettes": {
    "template": "{%raw%}{{ $factor := mod (now.YearDay | int) 6 }}{{ if eq $factor 0 }}theme1{{ else if eq $factor 1 }}theme2{{ else if eq $factor 2 }}theme3{{ else if eq $factor 3 }}theme4{{ else if eq $factor 4 }}theme5{{else}}theme6{{ end }}{%endraw%}",
    "list": {
      "theme1": {},
      "theme2": {},
      "theme3": {},
      "theme4": {},
      "theme5": {},
      "theme6": {}
    }
  }
}
{% endhighlight %}

Throughout the day, your prompt will now change like this:

[![colorschemes](/assets/images/different-oh-my-posh-color-scheme-per-day/windows-color-schemes.png){: .align-center}](/assets/images/different-oh-my-posh-color-scheme-per-day/windows-color-schemes.png)

Or if Linux is your thing:

[![colorschemes](/assets/images/different-oh-my-posh-color-scheme-per-day/ubuntu-color-schemes.png){: .align-center}](/assets/images/different-oh-my-posh-color-scheme-per-day/ubuntu-color-schemes.png)

(Note: the background color is set in my terminal. I don't believe you can control that directly in Oh My Posh)

The trick is to use [palette references](https://ohmyposh.dev/docs/configuration/colors#palette), which will let you style changes the bare the colors in one place and have them show up throughout the theme. Check out the source to my theme in the last section.

## Blast mode

Every day not often enough for you? Change `now.YearDay` to `now.Hour`, or for the impatient `now.Minute` (or even `now.Second`).

Example:

{% highlight javascript linenos %}
"template": "{%raw%}{{ $factor := mod (now.Minute | int) 6 }}{{ if eq $factor 0 }}theme1{{ else if eq $factor 1 }}theme2{{ else if eq $factor 2 }}theme3{{ else if eq $factor 3 }}theme4{{ else if eq $factor 4 }}theme5{{else}}theme6{{ end }}{%endraw%}"
{% endhighlight %}

## It's 5 o'clock somewhere

Perhaps you want something a little something to remind you it's after 5pm and problably time to wrap up your day. Here's the logic to change your prompt after 5pm.

{% highlight javascript linenos %}
"template": "{%raw%}{{ if gt (now.Hour | int) 17 }}day_theme{{ else }}night_theme{{ end }}{%endraw%}"
{% endhighlight %}

## My theme

My full theme can be found as a [gist on GitHub](https://gist.github.com/Fammy/cfc685f7cbd3dabfb0d41ca7729ea530) and is embedded below. The palette logic is at the bottom.

If you have any questions, feel free to reach out to me.

<script src="https://gist.github.com/Fammy/cfc685f7cbd3dabfb0d41ca7729ea530.js"></script>