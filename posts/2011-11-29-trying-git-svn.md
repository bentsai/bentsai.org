---
title: "Trying Git SVN"
date: "2011-11-29"
layout: layouts/post.njk
---

I've been experimenting with a Mercurial-to-Subversion workflow using
[hgsubversion](https://bitbucket.org/durin42/hgsubversion/wiki/Home). In brief,
I have our Subversion repository checked out using that tool, and I work in a
clone of that Hg repository. It works, but there are two main negatives.

The first is a consequence of the tool rewriting history. The tool works great
at keeping you in sync with Subversion as you are fixing bugs (each Subversion
checkin corresponds to a Mercurial changeset with the correct author and date as
you would expect). But once you push your changes from Mercurial to Subversion,
any clones from your bridge repository are now invalid. I knew this full well
going into it. This would normally be fine for a workflow where I made an
hgsubversion clone for each piece of concurrent development I want to do.

The problem is that, since our Subversion repository is so big (working copy is
2.5 GB and we use it for non-code assets), cloning it takes really a long time
(about 7 minutes), which leads me to the second negative. It's slow. I still get
the benefits of fast local commits, but overall, using TortoiseHg and the
command-line tools drag just enough that it's left me unsatisfied and in search
of a better solution.

So, I'm in the process of checking out our repository using Git, per
[the instructions here](http://andy.delcambre.com/2008/03/04/git-svn-workflow.html).
I tried to just check out our "integration" branch, which is all I care about,
but even though I pointed Git to that URL, it appears to be getting the whole
kit and kaboodle. It's been hours now since I started, but I'm hoping this is
just the up-front cost I need to pay. Git is supposed to be _really_ fast, so
we'll see...
