---
title: "How to retrieve an off-screen window"
date: "2012-01-19"
layout: layouts/post.njk
---

Currently, I'm working on a bug fix for the case when you've closed our
application on a secondary monitor, then disable that monitor (e.g. when
undocking a laptop), and then start up the app again. The problem is, we try to
restore the window position, and it ends up off-screen and completely hidden
from the user.

This happens occasionally with apps that don't behave politely. As a workaround,
you can retrieve the window like this:

Alt-Space M , then use the mouse to move the window.

What this does is open the command window and select the Move option. The arrow
key then allows the mouse to take over the move.
