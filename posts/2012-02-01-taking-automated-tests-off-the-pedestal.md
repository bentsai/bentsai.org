---
title: "Taking Automated Tests Off The Pedestal"
date: "2012-02-01"
layout: layouts/post.njk
---

Michael Feathers of
["Legacy Code"](http://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052/ref=tmm_pap_title_0)
fame explaining a balanced approach to automated tests:

> Many projects have a very large number of automated tests. And, that's good.
> It's better than not having them. On the other hand, many teams feel like
> these tests are a yoke around their necks. Their build time keeps increasing.
> They spend more and more time dealing with test management, and at the end of
> the day, they know that things are getting worse.

This has been my experience at times. The tests that we have in place do not
seem to catch new bugs, and adding more tests feels like just extending the
build time and feedback loop.

> I'm sure that at this point, you might think that I'm making an argument
> against automated testing. I'm not. I'm merely pointing out that at the end of
> the day, quality is a development responsibility and it has a lot to do with
> diligence.

I think you have to continuously improve and ask, "is this actually helping?"
It's not just good enough to _have_ a process. It's gotta work. The goal is not
to have a huge number of tests. Rather, it's to improve quality. And what this
article points out is that sometimes things that worked before don't work
anymore.
