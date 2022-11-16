---
title: "Integrating TortoiseHg with Visual Studio"
categories:
  - Blog
---


If you use Visual Studio, you don't get integration with version control unless you use Team Foundation Server or install a plugin.
This is an adaptation of this fantastic [guide](http://tortoisesvn.net/visualstudio.html), originally written for TortoiseSVN. This guide also works for git (or any version control system), just change the commands.

## Creating External Tool entries

The first step to setting up the integration is to create external tool entries for the various commands you'd like to launch from Visual Studio. Using the following steps, you'll have one or more hg commands at your disposal.

1. Go to "Tools -> External Tools" menu item.
2. Click "Add".
3. Name the tool in the "Title" textbox. I've chosen "hg annotate", "hg diff", and "hg log".
4. In the "Command" textbox, put the path to TortoiseHg, typically "C:\Program Files\TortoiseHg\thg.exe"
5. Fill out the proper arguments. The $(ItemPath) variable points to the current file. It's good practice to surround  the item in quotes, as you may have spaces in your path. Here are the various agruments for the commands I use:
	1. Annotate: annotate -n $(CurLine) "$(ItemPath)"
	2. Diff: vdiff "$(ItemPath)"
	3. Log: log "$(ItemPath)"
6. Within "Initial Directory", put a path within your repository. I've chosen $(ItemDir) for simplicity. You can also use $(SolutionDir) or one of the others.
7. Check "Close on exit", or you'll end up with a pesky Command window left open.
8. Note the position of your entry in the list (8th, etc). You'll need to use it later.
9. Repeat steps 2 through 7 for the various commands, and click "OK" to save.

## Adding context menu items

While you can use the entries in External Tools as is (Tools -> hg log), it's useful to have them in the various context menus in the system.
Some of the commands are dependent on the type of file open, so open a code file before you start.

1. Go to "Tools -> Customize" menu item.
2. Click the "Commands" tab.
3. Click the "Context menu" radio button.
4. Choose an appropriate menu item from the "Context menu" dropdown:
	1. "Editor Context Menus | Code Window" adds it to the right-click menu of the code window.
	2. "Other Context Menus | Easy MDI Document Window" adds it to the right-click of the document tab.
	3. "Project and Solution Context Menus | Item" adds it to the right-click menu of the files in the Solution Explorer.
5. Click the "Add Command..." button.
6. Select "Tools" from the "Categories" listbox.
7. Now the fun part. Select "External Command x", where x is the position in the External Tools entries. You remembered to remember that, didn't you?

## Bonus

As an added bonus, this guide also works in SQL Server Management Studio.