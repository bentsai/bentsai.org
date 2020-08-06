---
title: "My first Pythonista script"
date: "2013-01-07"
layout: layouts/post.njk
---

_**Update:** I figured out how to specify ranges and
[open YouVersion Bible app to more than a single verse](http://bentsai.wordpress.com/2013/12/18/youversion-bible-url-scheme/ "YouVersion Bible URL Scheme")._

I recently purchased [omz:software](http://omz-software.com)'s
[Pythonista](http://omz-software.com/Pythonista), which is a Python programming
environment for iOS. Thanks to Viticci's excellent piece about how it
[changed his iOS workflow](http://www.macstories.net/stories/automating-ios-how-pythonista-changed-my-workflow/),
I saw how well-designed and powerful the program is. I've dabbled with Python on
and off throughout my career and I'm always wanting to improve. This puts Python
in my pocket, and after using it for a few hours, I can say Pythonista is worth
the \$5 entry fee.

The first script I decided to write is something I've wanted to have available
on all of the computers I use—it's a script that essentially linkifies bible
references to make accessing them more convenient. In this iOS implementation of
it, the workflow is that you:

- Copy the bible reference to the clipboard.
- Launch a home screen shortcut.
- Get navigated to the verse/passage in your bible reader.

The first iteration of this has some severe limitations, but it does work.
[Here is the script on Gist](https://gist.github.com/bentsai/4471849#file-biblerefs-py).

The main limitations right now are that 1) it doesn't work on ranges. You have
to specify a single verse, or an entire chapter. And 2), you must use the full
book name. An abbreviation, such as _Gen_ for _Genesis_ will not work. These
limitations present some interesting challenges that will give me the
opportunity to improve my Python chops. I'd like to be able to support the
various ways that bible passages can be represented, and I'm sure there are many
edge cases which I haven't considered. There is a
[bible reference parser](https://github.com/openbibleinfo/Bible-Passage-Reference-Parser/)
project on Github written in Coffeescript which is well-documented that I've
referred to a couple times and will continue to do so.

The bible reader app I use right now is YouVersion, which does have an
undocumented URL scheme. It also has its own limitations: I haven't figured out
how to pull up ranges, and
[it may not be possible yet](https://twitter.com/bdmontz/status/288085216927547392).
So until that happens, I also won't have a complete working implementation.
