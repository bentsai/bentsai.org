---
title: "Public Jrnl"
date: "2022-08-09T17:09:25-0400"
layout: layouts/post.njk
---

I've connected together a few tools so I can quickly publish thoughts to a
website.

## Jrnl

[Jrnl](https://jrnl.sh) is a slick CLI tool for journaling. It stores data in a
single text file.

## Lists

Another tool in the [picosphere](https://pico.sh), [Lists](https://lists.sh)
lets you easily publish a list-oriented text file to the web.

## Raycast

This is how I input my thoughts. I have a simple extension that calls `jrnl`,
then pipes the output into lists.sh:

```
#!/bin/bash

# Required parameters:
# @raycast.schemaVersion 1
# @raycast.title jrnl-public
# @raycast.mode silent

# Optional parameters:
# @raycast.icon 📖
# @raycast.argument1 { "type": "text", "placeholder": "Entry" }
# @raycast.packageName JrnlPackage

# Documentation:
# @raycast.description Add a jrnl entry to public journal
# @raycast.author Ben Tsai
# @raycast.authorURL bentsai.org

jrnl public "$1"
jrnl public --short | tac | ssh lists.sh Jrnl.txt
```

## Result

A reverse-chronological list of items almost instantly published from my
fingertips:

https://ben.lists.sh/Jrnl
