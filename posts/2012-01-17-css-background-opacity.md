---
title: "CSS background opacity"
date: "2012-01-17"
layout: layouts/post.njk
---

How to adjust the opacity of the background of a div without affecting child
elements:

.alpha60 { /\* Fallback for web browsers that doesn't support RGBa \*/
background: rgb(0, 0, 0); /\* RGBa with 0.6 opacity \*/ background: rgba(0, 0,
0, 0.6); }
