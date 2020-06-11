---
title: "Calepin Tips"
date: "2011-12-18"
layout: layouts/post.njk
---

While I wait for [@calepinapp](http://twitter.com/calepinapp) to put up a ["Pro Tips" page](https://twitter.com/#!/calepinapp/status/144546525803061248), I've put together my own. I'm using it as a reference as I write posts and will add to it as I use the various features.

**Update**: [Jökull](http://twitter.com/jokull) (Calepin dev) has put up a [Calepin Guide](http://jokull.calepin.co/calepin-guide.html).

# Metadata

Title: Calepin Tips
Date: 2011-12-09 13:32
Status: draft
Tags: tips, tech
Category: calepin
Slug: calepin-tips

# Markdown

Calepin uses [python-markdown](http://www.freewisdom.org/projects/python-markdown/Features).

# Syntax highlighting

The [CodeHilite](http://freewisdom.org/projects/python-markdown/CodeHilite) extension will try to detect the language. You can also specify it using a special colon syntax or shebang:

:::python
name = raw_input('What is your name?\\n')
print 'Hi, %s.' % (name)

name \= raw_input('What is your name?\\n')
print 'Hi, %s.' % (name)

# HTML

Raw HTML passes through, so you can [embed a tweet](https://dev.twitter.com/docs/embedded-tweets) by pasting the HTML directly:

<blockquote class="twitter-tweet"><p>@<a href="https://twitter.com/bentsai">bentsai</a> Pro Tips page is a great idea. It's in the works in fact. Use this time format: "2011-11-20 12:01"</p>— Calepin (@calepinapp) <a href="https://twitter.com/calepinapp/status/144546525803061248">December7, 2011</a></blockquote>
