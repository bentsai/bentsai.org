---
title: "Kinopio → Markdown"
date: "2021-03-12"
layout: layouts/post.njk
---

The idea: write a script to convert Kinopio JSON to Markdown. Add some front
matter. Then put that Markdown into my eleventy-based blog.

The super basic script is just get the text of the cards, sorted by y position.
Like so:

```
curl -s https://api.kinopio.club/space/HASZ8HDbGXn-1jkG-Zud8
| jq -r '.cards
| sort_by(.y)
| .[] | .name + "\n"'
```

The flow should be giving the script a URL, and it would spit out a
eleventy-compatible markdown file. Title can be space title, and date can be
last updated field.

[*time passes*]

I worked on this some more, and here's what I have so far:

![](https://us-east-1.linodeobjects.com/kinopio-uploads/flkpTifu-ysMqYL4V7pKV/k2md.sh.png)

This was generated from
[this Kinopio space](https://kinopio.club/kinopio-markdown-HASZ8HDbGXn-1jkG-Zud8).

### Next steps

- Enable combining two cards in a single paragraph
- Share code on GH
- Reimplement in JavaScript so I can more easily work with connections and other
  attributes
- Automate creating the file and publishing blog
