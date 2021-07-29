---
title: "How to anonymize a Kinopio space"
date: "2021-07-29"
layout: layouts/post.njk
---

This is useful for sharing screenshots of Kinopio spaces with sensitive
information. It replaces all letters with asterisks. In the JavaScript console,
execute this code:

```js
document
  .querySelectorAll(".card-content .name > span")
  .forEach(name => (name.textContent = name.textContent.replace(/[^\s]/g, "*")))
```
