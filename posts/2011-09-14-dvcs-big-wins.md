---
title: "DVCS Big Wins"
date: "2011-09-14"
layout: layouts/post.njk
---

Our company recently started to have these learning sessions where a team member will share something relevant with everyone else. I like to call them LOLs (lunches of learning.) I gave a presentation today about distributed version control systems. I talked about two key differences that DVCS's, specifically Mercurial, have from centralized systems, such as Subversion. The first difference, ostensibly, is that with centralized VCS's, there is one repository with your "golden" sources, and each developer checks out a working copy:

[![](http://bentsai.files.wordpress.com/2011/09/centralized.png?w=300 "Structure of Centralized VCS")](http://bentsai.files.wordpress.com/2011/09/centralized.png)

On the other hand, in the distributed world, each developer gets their own repository:

[![](http://bentsai.files.wordpress.com/2011/09/distributed.png?w=300 "Structure for Distributed VCS")](http://bentsai.files.wordpress.com/2011/09/distributed.png)

The implications of this are **HUGE**.

First of all, giving developers their own repository effectively decouples the act of checking in your changes from the act of polluting the rest of the team with those changes. This **eliminates the fear of the commit** and encourages you to experiment while coming up with solutions, all the while keeping track your changes along the way. You no longer have to make sure tests pass or even that it builds. No longer are you manually copying around files or mentally juggling your undo buffer. It is freeing. This is such a paradigm shift that I am still learning and disciplining myself to commit more frequently.

The other implication of having a local repository is that **every operation is fast** and, well, local. You can easily travel through time, which becomes incredibly noticeable when you are trying to track down which change broke things. If for whatever reason the central repository is unavailable (e.g. the server is down, you can't connect via VPN, you're on a plane without WiFi), you are completely unhindered from checking in changes and working with your full history. By reducing the latency and "friction," the tool gets out of the way and facilitates getting work done.
