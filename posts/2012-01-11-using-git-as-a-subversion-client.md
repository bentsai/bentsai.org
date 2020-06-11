---
title: "Using Git as a Subversion Client"
date: "2012-01-11"
layout: layouts/post.njk
---

Let's say you're working with a team that's using Subversion for version control. The repository has a long history, and you only want some of it. And only one branch. Windows-centric. Here's a guide to setting up a workflow for using Git as a Subversion client.

Installing Git

Git for Windows Git Extensions

Setting Up The Repository

Initializing Git

git svn init

This creates a .git directory inside of the destination directory which tells Git where to get stuff from, but we haven't actually fetched anything from Subversion yet. If you look at the config file inside, you'll see something like:

\[core\] repositoryformatversion = 0 filemode = false bare = false logallrefupdates = true symlinks = false ignorecase = true hideDotFiles = dotGitOnly \[svn-remote "svn"\] url = fetch = :refs/remotes/git-svn

Fetch from Subversion

Now let's get the data, but not all of it. Decide which Subversion revision you want to start at, and then:

cd git svn fetch -r :HEAD

This will begin pulling the Subversion repository, starting at the revision you specified. You'll see log messages fly by, indicating files that are being added. Then you may notice some business about compressing and writing objects. This process could take a really long time, depending on how much history you are pulling. Don't be surprised if it's hours.

Making Changes Locally

Make changes. Commit. Repeat.

Pushing Changes Back To Subversion

Updating with any current changes

git svn fetch

Cleaning up commits

git svn rebase -i

Committing to Subversion

git svn dcommit
