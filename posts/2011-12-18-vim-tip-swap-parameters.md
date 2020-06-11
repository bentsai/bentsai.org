---
title: "Vim Tip: Swap Parameters"
date: "2011-12-18"
layout: layouts/post.njk
---

`:map <Leader>t "qdt,dwep"qp`

See my [Stackoverflow answer](http://stackoverflow.com/q/8246046/139).

This works if the next argument uses quotes:

`:map <Leader>u "qdt,dwf"p"qp`

I think...
