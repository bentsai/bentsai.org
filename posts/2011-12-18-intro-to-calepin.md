---
title: "Intro to Calepin"
date: "2011-12-18"
layout: layouts/post.njk
---

A
[recent post on onethingwell.org](http://onethingwell.org/post/13206828349/calepin)
pointed me to a new web service called [Calepin](http://calepin.co). It's a
static blog generator that uses Markdown-formatted files from your Dropbox. The
concept is powerful because it takes the formidable and future-proof plain text
file, provides the glue to existing infrastructure, and reduces self-publishing
to the click of a button. The service is powered by
[Pelican](http://pelican.readthedocs.org), which has blog features like
categories, tags, feeds and themes. Currently, there is comments support via
[disqus](http://www.disqus.com). On the roadmap is theming and CNAME support,
and the developer [@calepinapp](http://twitter.com/calepinapp) has been actively
fixing and implementing things since release.

Once you have things set up, the basic workflow looks like:

- Create a Markdown (**.md**) file containing date and title metadata
- Hit Publish at [Calepin](http://calepin.co)

Although easy self-publishing is hardly a novel idea, this implementation is
really intriguing to me for two reasons. The first is that posts are stored as
plain text files on your local machine. This means you have full control over
your own content, and you'll never have to worry about having your posts tied up
in a third-party service. The second is that it uses Dropbox as its backend.
Since Dropbox is
[the cloud's file storage](http://lifehacker.com/5861951/most-popular-online-file-storage-and-syncing-service-dropbox)
[darling](http://www.forbes.com/sites/victoriabarret/2011/10/18/dropbox-the-inside-story-of-techs-hottest-startup/),
it's a good bet that it will stick around for a while, and there are plenty of
apps and services that interface with it—meaning, I can update my blog from any
Dropbox-enabled device. Calepin gains the benefit of the whole Dropbox
ecosystem.

One potential killer combination is using [ifttt](http://ifttt.com) to trigger
Dropbox actions that propagate to Calepin. If ifttt ever gets a feature to
create a Dropbox file from text it receives, then that opens up even more
possibilities to updating a Calepin-powered blog: using SMS, chat, email, phone
call, etc. All of this without having any explicit support on their end, since
the work is all done on the ifttt side.

In my quest for a low-friction, universal journal, I'm one step closer.
