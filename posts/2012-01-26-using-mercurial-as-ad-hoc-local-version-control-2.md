---
title: "Using Mercurial as ad-hoc local version control"
date: "2012-01-26"
layout: layouts/post.njk
---

Let's assume you're working at a company using Perforce or Subversion as source
control, and you're tasked to fix a bug on the main branch of development. You'd
prefer not to commit anything into the repository that breaks, lest the build
master (who may be yourself) get on your case and you're additionally tasked to
buy donuts for the group.

If the bug/change you're trying to make is anything beyond the most trivial
task, it would be great to have your sources under version control so you have
the freedom to try things and backtrack—you know, one of the basic ideas behind
version control. So, now you're stuck. There's too much overhead to create a
whole new branch just for this one fix. Do you resort to renaming files and
folders and moving back and forth on your editor's undo buffer? C'mon now,
behave.

When the tools aren't working for you, find a new tool! Enter
[Mercurial](http://www.selenic.com/mercurial/wiki/). I won't get into the
interminable debate between Mercurial and [Git](http://git.or.cz/) and other
DVCS's. Suffice it to say that they are all the NBT, and distributed VCS are a
superset of centralized ones. I've chosen Mercurial for pragmatic reasons: 1)
works well on Windows and 2) is implemented primarily in
[Python](http://www.python.org/).

The basic idea is, you can use Mercurial on top of your current, centralized
version control system. This way, you get all of your local sources under
version control independent of what the rest of your company uses. It's a simple
idea, but it frees you from worrying about how to manage changes you're making
in your local area. Another situation I frequently find this useful in is when
I'm writing a one-off script that I'm not sure if I want to commit to the
repository. But, the script is complex enough that I'll need to iterate a few
times. Wouldn't it be great to have it under version control? Here's how:

# Install Mercurial

I'm on Windows, so I just go for the
[Windows binary package](http://mercurial.berkwood.com/) where Python and
everything is all wrapped up for you. You can also install it with cygwin, if
that's your bag. Make sure C:\\Mercurial (or wherever you installed it) is in
your path.

Now, you're good to go. The executable name is "hg" (get it?) and if you type
that without any arguments at command prompt, you will see a list of basic
commands. All the concepts of version control that you're familiar with are all
there. Let's walk through an example of putting your sources under version
control and making some changes.

# Create a new repository

The first thing you'll do is create a new repository from your current sources.
Let's say you're working on on a project in C:\\projects\\GoogleKiller. Navigate
to that directory, and type:

```
> hg init
```

That command should return silently. It generated a .hg folder in that directory
where the metadata is stored. You've just created a repository. You can now do:

```
> hg status
? GoogleKiller.py
? GoogleKillerTests.py
? README.TXT
```

This tells you that mercurial sees three files, but none of them are tracked. To
start tracking them, simply:

```
> hg add
adding GoogleKiller.py
adding GoogleKillerTests.py
adding README.TXT
```

Without specifying any files to "hg add", you've added all the files in the
directory. Now, the last step to getting these sources in the repository is:

```
hg commit -m "Initial checkin!"
```

The -m argument is the log message for the checkin. You can track the history of
commits with the log command:

```
> hg log
changeset:   0:8c047c4da9a4
tag:         tip
user:        bentsai@example.com
date:        Fri May 30 17:32:17 2008 -0400
summary:     Initial checkin!
```

Now you're ready to roll with local version control:)

# Start coding

The commandline help for mercurial is pretty good. The basic commands you'll
care about are:

- `hg status` (to see what files have been modified)
- `hg diff` (which prints out a unified diff of what's changed)
- `hg revert` (for backing out of changes) To get more details on these
  commands, just type "hg help ". There are other tweaks you can make to the
  usage (the \[documentation\](http://hgbook .red-bean.com/hgbook.html) is
  good), but that's the general idea. Now you're free to get on with coding!

The process for getting up and running is pretty low on friction, which is why I
like it. This doesn't even begin to touch the real boon of DVCS's—actually
collaborating with others. But this technique takes advantage of Mercurial's
speed, easy-of-use, and unobtrusiveness for a rapid solution to a fairly common
problem.

**Update (June 1, 2008):** I should note that using Mercurial for version
control isn't limited to code. Any situation you're keen on rolling back
changes, this could work. Before I found out about Mercurial, I thought about
using Subversion for such a purpose. But the pain was setting up a server - with
Mercurial, there is no centralized server to setup. The only thing Mercurial
does is add an ".hg" folder in the root. Once you have it installed on your
computer, you've got localized
[Time Machine](http://www.apple.com/macosx/features/timemachine.html)\-like
powers at your fingertips.

**Update (June 2, 2008):** Here's someone who's
[using Mercurial specifically with Perforce](http://www.dehora.net/journal/2008/01/05/using-mercurial-with-perforce/)
and described his workflow more extensively than I have.
