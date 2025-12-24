---
layout: post
title: '[BibDesk] APA template'
categories:
- Spencer ex San Diego
---

I'm sure that somewhere, someone like me is hopelessly googling around looking for a way to get BibDesk to be able to drag-n-drop APA-formatted reference list entries. Hopefully Google will point you here, because I FIGURED IT OUT \*flex\*

Here's the magic words:

<$publications>

<$authors.abbreviatedNormalizedName.@componentsJoinedByCommaAndAmpersand/> <$fields.Year.parenthesizedStringIfNotEmpty/>. <$fields.Title.uppercaseFirst.stringByAppendingFullStopAndSpaceIfNotEmpty/>*<$fields.Journal.stringByAppendingCommaAndSpaceIfNotEmpty/><$fields.Volume/>* <$fields.Number.parenthesizedStringIfNotEmpty/>, <$fields.Pages.stringByAppendingFullStopIfNotEmpty/></$publications>

Copy-paste this into Ye Olde Text Editor and save it as an RTF. Whatever font and font-size you save this RTF in is what font and font size comes out.

Go into the Templates pane of the BibDesk preferences window. Hit the + button to create a new one and call it something good. "Double-click to choose file" and select the RTF you just made.

Then click "Show All" to go back to the main preferences window, and go to your Citations pane. Change the "Default format:" dropdown to Template, and pick the new template you just made in the next dropdown. (If you want to keep the behavior of dragging out stuff like \cite{key1}, you might want to do this in the "format when holding Option key" section instead.)

If you want to tinker with any of the fine details (for instance, I like to separate my volume and issue numbers with a space), you can manually edit the file in your favorite text editor. If you want to make large adjustments, try opening it in BibDesk's built-in template editor.
