---
title: "Bible at your fingertips with Raycast"
date: "2022-06-16T13:57:01-0400"
layout: layouts/post.njk
---

[Raycast](raycast.com) is an extremely slick launcher for macOS.  It's become a must-install and handedly replaced Alfred for me. [In the past week, they released](https://www.raycast.com/changelog#1.36.0) the last thing I was missing from Alfred—that is, customizable date snippets.

Combining this launcher with [bible fetch](https://github.com/covode/bible-fetch) gives me a powerful way to retrieve any Bible passage on command, ready to be pasted into an app.

`⌘-Space`, `bible<Tab>Ro 5:6-8<Enter>`

![](/img/bible-fetch-raycast.png)

`⌘-V`

> You see, at just the right time, when we were still powerless, Christ died for the ungodly. Very rarely will anyone die for a righteous person, though for a good person someone might possibly dare to die. But God demonstrates his own love for us in this: While we were still sinners, Christ died for us.

This smooths out the workflow of having to visit Biblegateway, searching for the passage, turning off verse numbers, selecting the text, invoking copy.

Here's the [Raycast script command](https://raycastapp.notion.site/Script-Commands-771ff9351bc54ee88fa9c585b7782e22) I wrote that wraps the call to bible fetch and includes some metadata that Raycast uses:

```bash
#!/bin/bash

# Required parameters:
# @raycast.schemaVersion 1
# @raycast.title bible
# @raycast.mode silent

# Optional parameters:
# @raycast.icon 📙
# @raycast.argument1 { "type": "text", "placeholder": "reference" }
# @raycast.packageName Bible Fetch

# Documentation:
# @raycast.description Get passage
# @raycast.author Ben Tsai
# @raycast.authorURL bentsai.org

~/Code/bible-fetch/bible "$1" | pbcopy
echo "Bible passage copied"
```