---
title: "An .hgignore file for Visual Studio 2008 and ReSharper"
date: "2010-03-22"
layout: layouts/post.njk
---

I'm on a project using Visual Studio 2008 and ReSharper right now. Here's my Mercurial ignore file, which includes patterns for common files and directories I don't want Mercurial to track. The master copy will be at [http://gist.github.com/340254](http://gist.github.com/340254)

\[sourcecode\]# Ignore file for Visual Studio 2008

\# use glob syntax syntax: glob</code>

\# Ignore these directories bin/ CVS/ \[Dd\]ebug\*/ obj/ \[Rr\]elease\*/ \_ReSharper\*/

\# Ignore these files \[Bb\]uild\[Ll\]og.\* \*~ .\\#\* \*.bak \*.ncb \*.obj \*.pdb \*.suo \*.swp \*.user \[/sourcecode\]
