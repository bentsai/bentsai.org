---
title: "How to hide multiplayer avatars in Kinopio"
date: "2021-07-30"
layout: layouts/post.njk
---

Especially in large multiplayer sessions, you may want to hide others' avatars
to focus. Here's some code to do that:

```js
var ss = document.createElement("style")
ss.type = "text/css"
ss.innerText = ".user-label { display: none }"
document.head.appendChild(ss)
```

To show the avatars again, remove that noe:

```js
ss.parentNode.removeChild(ss)
```
