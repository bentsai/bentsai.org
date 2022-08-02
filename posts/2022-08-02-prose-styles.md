---
title: "Styling Prose"
date: "2022-08-02"
layout: layouts/post.njk
---

I started using [prose.sh](https://prose.sh/) as a mirror for my blog. Prose is a cool project
within the [Pico](pico.sh) ecosystem that lets you blog with an ssh-based workflow. Their vibe
is to promote the smol web. Cool!

They recently [implemented custom CSS](https://todo.sr.ht/~erock/pico.sh/35), based partially on
my request in their IRC. So with that, I've made a few visual tweaks to my blog which you're seeing
now.

I'm happy about bumping up the font size on the headings, an unironic use of Times New Roman with
some tightening on the letter spacing.

The live file is [here](https://ben.prose.sh/_styles.css), while the current state on publish is:

```css
header {
  margin: 2rem auto;
}
header > .text-2xl {
  font-family: "Times New Roman", "Droid Serif", Times, "Source Serif Pro", serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  font-size: 2.5rem;
  color: #393939;
  letter-spacing: -2.5px;
  line-height: 2.25rem;
  text-align: center;
  padding-top: 1rem;
}

#blog header > .text-2xl {
  font-size: 4rem;
}

header > p.font-bold {
  font-weight: normal;
  font-style: italic;
  letter-spacing: -1px;
  opacity: .8;
  text-align: center;
  padding-top: .5rem;
}

code, kbd, samp, pre {
  font-size: 0.9rem;
}

.post-date {
  font-family: monospace;
  font-style: normal;
  opacity: .8;
  padding-top: .2rem;
  letter-spacing: -1px;
  width: 108px;
}
```
