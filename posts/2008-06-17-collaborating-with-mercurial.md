---
title: "Collaborating with Mercurial"
date: "2008-06-17"
layout: layouts/post.njk
---

Now that you've got Mercurial running on your local machine, what if you want to collaborate with someone else? The easiest way to do this is to run "hg serve", which starts a local http server that allows others to browse your repository, view changelogs, clone your repository and pull your changes. This is deemed an ["informal" method of sharing](http://hgbook.red-bean.com/hgbookch6.html#x10-1220006.4) because it provides unauthenticated read-only access to your repository. You wouldn't use this to share your code with the public, but it works great within company walls if you're trying to work with a coworker on something.

Again, it's very simple and you'll have it running in less than a second. Inside your repository, do:

`hg serve`

By default, you won't see any output. You can verify things are working by navigating to `http://localhost:8000/`.

Now that you're sharing your repository, Charlie can point his browser to `http://[your machine name]:8000/` and browse your changelogs, files, tags. If he wants to start making changes, then he would:

`hg clone http://[your machine name]:8000/ destination_directory`

This will print out some status messages about what it's doing. Now Charlie has a repository one his machine that he can start working with. If I make subsequent changes, Charlie can pull them into his repository by doing:

`hg pull http://[your machine name]:8000/`

And vice versa, if Charlie commited some changes, he would run `hg serve` and I would pull from his computer.

This is merely an introduction to doing some lightweight collaboration. In this scheme, since the "hg serve" provides read-only access, we are using a "pull only" model. This may not be practical depending on your project, but again, this is a quick and easy way of sharing and collaborating on code.
