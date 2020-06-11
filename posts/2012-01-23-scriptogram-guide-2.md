---
title: "Scriptogram Guide"
date: "2012-01-23"
layout: layouts/post.njk
---

# Styling

## Header

The selector for the `h1` in the header is `body > h1`. Here is how I accomplished adding my avatar:

```
/* Title */
body > h1 {
  padding-left: 48px;
  height: 40px;
  background-image: url(http://dl.dropbox.com/u/2474799/njw.jpg);
  background-repeat: no-repeat;
  background-size: 40px;
}
```

# Drafting a post

- Create a new file in `posts` entitled "DRAFT-slug.md"
- Set the metadata to be:

\---
Published: false
Title: Post Title

---

- Once you're ready to publish, change the metadata to be (remove `Published` field and add `Date`:

\---
Date: 2012-01-11
Title: Post Title

---

# Markdown particulars

## HTML

```
<blockquote class="twitter-tweet" data-in-reply-to="156382260231290880"><p>@<a href="https://twitter.com/bentsai">bentsai</a> cheers!</p>&mdash; scriptogr.am (@scriptogram) <a href="https://twitter.com/scriptogram/status/156382577819791360" data-datetime="2012-01-09T14:31:26+00:00">January 9, 2012</a></blockquote>
<script src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
```

<blockquote class="twitter-tweet"><p>@<a href="https://twitter.com/bentsai">bentsai</a> cheers!</p>— scriptogr.am (@scriptogram) <a href="https://twitter.com/scriptogram/status/156382577819791360">January 9, 2012</a></blockquote>

## Footnotes

```
I'm intending on writing a guide for Scriptogram[^1].

[^1]: But for now, I'm just testing out footnotes.
```

I'm intending on writing a guide for Scriptogram[1](1).

---

2. But for now, I'm just testing out footnotes. [↩](1)
