---
title: "Tech debt → maintenance load"
date: "2022-08-19T16:37:28-0400"
layout: layouts/post.njk
---

I came across this
[incredible series about technical debt](https://chelseatroy.com/2021/01/14/quantifying-technical-debt/)
by [Chelsea Troy](https://chelseatroy.com/). (Her site is a treasure trove of
articles on topics I care about and I'll probably spend some time reading and
reflecting on them.)

In the first part of the series, she introduces a concept called **maintenance
load** to think about technical debt. That is,

> how much effort your development team spends to keep the existing features
> running the same as before

Maintenance load is a function of

- the age of the project
- the practices used to build it

She then gives some example scenarios where let's say you have a 10 y/o code
base (✓) where devs wrote some tests (✓), some cursory documentation but not
everything is documented (✓), and occasionally something got rethought or
removed (✓). In a code base like this, 4-5 devs are _just_ on maintenance 🤔.

I feel seen 😅.

My ears perked because not only does this largely apply, but my team just began
to pilot a scheme I devised where we split our team into a _new feature_ team
and a _maintenance_ team. A big motivation was to allow some developers to focus
on building and avoid context switching. So in some ways, we have made explicit
the maintenance load on our team.

I still have yet to digest parts
[two](https://chelseatroy.com/2021/01/18/avoiding-technical-debt/) and
[three](https://chelseatroy.com/2021/01/21/reducing-technical-debt/) where she
describes how to avoid and reduce technical debt, but it feels good to
acknowledge and understand the issue more clearly.
