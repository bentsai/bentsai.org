---
title: "Tip: Kill TSVNCache.exe to speed up Visual Studio startup times"
date: "2009-06-12"
layout: layouts/post.njk
---

When Visual Studio 2005 took over 3 minutes to start up, I figured that was just
the price to pay for using a feature-filled/bloated IDE. After all, our working
copy has some 20,000 files, and I'm running [ViEmu](http://www.viemu.com/) and
[Resharper](http://www.jetbrains.com/resharper/) add-ins. And I was willing to
pay that price - I just had to "plan" my water/coffee breaks around when I
wanted to start and stop Visual Studio.

Well, my boss decided to investigate, and eventually determined that the culprit
was the TSVNCache.exe process. TortoiseSVN runs this program in the background
to keep all of your nice icon overlays up to date. It's no secret that this
process is a memory and disk I/O hog. I had already upgraded to the newest
version, which claimed to make performance improvements. One strategy is to
[limit the folders it watches](http://yoopergeek.blogspot.com/2007/09/tortoisesvns-noisy-tsvncacheexe.html).
Another is to
[lower its priority](http://svn.haxx.se/tsvnusers/archive-2008-12/0091.shtml).
Even with these tweaks, it was still taking Visual Studio a long time to startup
and exit.

Finally, we looked at the
[TortoiseSVN settings](http://tortoisesvn.net/docs/release/TortoiseSVN_en/tsvn-dug-settings.html#tsvn-dug-settings-overlay)
and saw that we could essentially disable TSVNCache.exe from running at all.
This was under

> TortoiseSVN > Settings > Icon Overlays > Status cache

There are two options that will kill TSVNCache:

1. Shell
2. None

I decided to go with "Shell" since it still gives you real-time status. The
disadvantage is that status is not recursive, so folders containing modified
files will not show the modified overlay.

The results after disabling TSVNCache.exe were astounding. It only takes a
minute for Visual Studio and all of my add-ins to load, and less than 5 seconds
for it to shutdown!

![Speed improvement](http://bentsai.files.wordpress.com/2009/06/image.png?w=300 "Speed improvement")
