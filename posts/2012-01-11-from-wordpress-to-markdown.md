---
title: "From Wordpress to Markdown"
date: "2012-01-11"
layout: layouts/post.njk
---

I'm considering moving my blogging activity to Calepin. Here are the steps I've
taken so far to bring my content from wordpress into plaintext (markdown) files
that Calepin can render.

Export Wordpress Content

Tools->Export All content Download Export File

Now you have an XML file with all your content.

Convert Wordpress to Markdown

ExitWP is designed to export markdown in a format that Jekyll understands. For
example, it puts metadata into a YAML header:

\--- author: bentsai date: '2008-06-17 17:33:23' layout: post slug:
collaborating-with-mercurial status: publish title: Collaborating with Mercurial
wordpress_id: '26' categories: - technology tags: - collaboration - hg -
mercurial ---

The first time I ran ExitWP, I got a parse error. I deleted the offending line
and got another parse error. I deleted that line, and the export was successful.
It generated a directory full of .markdown files, with the date and slug for the
filename (2008-06-17-collaborating-with-mercurial.markdown).

Remaining steps

Edit exitwp.py to output the metadata in the Calepin format. Rerun the script.
Manually edit any anomalies from the export. Copy images from wordpress to a
public Dropbox folder. Re-link the images. Export comments

References

Blogging With Octopress Why I've Migrated to Octopress Switching to the
Octopress Blogging Engine
