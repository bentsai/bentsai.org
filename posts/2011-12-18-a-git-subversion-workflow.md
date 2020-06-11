---
title: "A Git Subversion Workflow"
date: "2011-12-18"
layout: layouts/post.njk
---

After you're done making changes locally...

# Get changes from Subversion

git svn fetch
git svn rebase

# Combine changesets using interactive rebase

git log --oneline
git rebase -i last_good_commit

This opens up your editor with a file listing all the available commits to rebase.

- Find changesets where you started a bigger task.
- Change `pick` to `reword` for these changesets.
- For changesets below each of these, change `pick` to `squash`. These changesets will get folded into the previous commit.
- Save the file to continue the process.

For each commit that you specified to `reword`, git will open your editor to allow you to change the commit message. Once you save and quit, you'll get another editor that let's you specify the commit message for all of the changes you are squashing. Thinking about it now, I can probably keep the commits that I changed to `reword` as `pick`, since this is redundant.

# Push changes back to Subversion

git svn dcommit
