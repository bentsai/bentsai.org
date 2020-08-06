---
title: "Getting Vim Pathogen to work"
date: "2012-06-27"
layout: layouts/post.njk
---

After much stumbling around, I finally figured out why installing
[mru.vim](http://www.vim.org/scripts/script.php?script_id=521) into
[Pathogen](https://github.com/tpope/vim-pathogen) wasn't working for me. It was
[this small comment](https://github.com/tpope/vim-pathogen/issues/57#issuecomment-4521914)
that finally got me to realize the problem:

> Yes, the root of each set of runtime files must sit in `bundle`.

I had created a directory in my bundle directory called mru, and inside of that
I put `mru.vim`. The problem is, since this is a plugin, it needs to go into a
`plugin` folder inside of there.
