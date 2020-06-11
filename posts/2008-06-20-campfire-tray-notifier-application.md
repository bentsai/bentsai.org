---
title: "Campfire tray notifier application"
date: "2008-06-20"
layout: layouts/post.njk
---

At work, we use [Campfire](http://campfirenow.com/) for intra-office communication. It's been a real boon for keeping everyone up to speed one what's happening, especially since many of us are separated geographically. It's also great because we can properly manage our attention--if I'm in the zone, I'll choose to ignore campfire, and at a later time I can catch up on the logs.

When we were first starting off incorporating Campfire into our process, though, the challenge was the social problem of getting everyone to learn a new habit of checking in on the chat and be there. The value of business chat is in the participation. Some of us needed Campfire to behave a little more like a desktop app that could provide invasive notifications to remind us to visit the web page.

For Mac, there is [Pyro](http://www.karppinen.fi/pyro/), which you can hook into Growl. But, since we were all on PC's, that wasn't viable. So, I turned to [AutoIt](http://www.autoitscript.com/autoit3/) and wrote a script that watches for changes in the web page title and pops up a balloon notification when there's a new message. Recently, I got an email from someone requesting this, so I'm posting it here.

Here is the AutoIt script: \[sourcecode\]Opt("WinTitleMatchMode", 2) Opt("WinWaitDelay", 500) $isBalloon = 0 $last_title = "" Do $title = WinGetTitle("Campfire: ") If WinGetTitle("") == $title Then $last\_title = $title ContinueLoop EndIf If StringInStr($title, "(") AND $title &lt;&gt; $last\_title Then $last_title = $title $parts = StringSplit($title, " ", 1) If ($isBalloon = 0) Then $isBalloon = 1 TrayTip("New Campfire message!", "There are unread messages in the " &amp; $parts\[3\] &amp; " chatroom.", 10) EndIf Else \$isBalloon = 0 EndIf Until 0 \[/sourcecode\]

After downloading and installing AutoIt, you'll be able to run this script (paste this into a text file and give it a "au3" extension). You can also turn it into an exe using Aut2Exe and drop a shortcut into your Windows Startup folder so it will be there on bootup.

This script only works for IE (6 & 7, I think) because of how the web page title is formatted. That was sufficient for our needs, but I don't think it would be hard to modify. I haven't had a chance to test this, but here's the code.
