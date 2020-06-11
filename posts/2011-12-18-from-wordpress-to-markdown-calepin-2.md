---
title: "From Wordpress to Markdown (Calepin)"
date: "2011-12-18"
layout: layouts/post.njk
---

I'm considering moving my blogging activity to Calepin. Here are the steps I've taken so far to bring my content from [wordpress](http://bentsai.wordpress.com) into plaintext (markdown) files that Calepin can render.

# Export Wordpress Content

1. Tools->Export
2. All content
3. Download Export File

![](images/wp-export_001.png)

Now you have an XML file with all your content.

# Convert Wordpress to Markdown

[ExitWP](https://github.com/thomasf/exitwp) is designed to export markdown in a format that [Jekyll](https://github.com/mojombo/jekyll) understands. For example, it puts metadata into a YAML header:

\---
author: bentsai
date: '2008-06-17 17:33:23'
layout: post
slug: collaborating-with-mercurial
status: publish
title: Collaborating with Mercurial
wordpress_id: '26'
categories:

- technology
  tags:
- collaboration
- hg
- mercurial

---

The first time I ran ExitWP, I got a parse error. I deleted the offending line and got another parse error. I deleted that line, and the export was successful. It generated a directory full of `.markdown` files, with the date and slug for the filename (`2008-06-17-collaborating-with-mercurial.markdown`).

# Remaining steps

- Edit `exitwp.py` to output the [metadata in the Calepin format](http://bentsai.calepin.co/calepin-tips.html).
- Rerun the script.
- Manually edit any anomalies from the export.
- Copy images from wordpress to a public Dropbox folder.
- Re-link the images.
- Export comments

# References

- [Blogging With Octopress](http://mattgemmell.com/2011/09/12/blogging-with-octopress/)
- [Why I've Migrated to Octopress](http://felipecypriano.com/2011/09/16/why-ive-migrated-to-octopress/)
- [Switching to the Octopress Blogging Engine](http://blog.pixelingene.com/2011/09/switching-to-the-octopress-blogging-engine/)
