---
title: "General Theory of Resources"
date: "2011-02-21"
layout: layouts/post.njk
---

In the process of researching about `IDisposable`, I found a [lot](http://stackoverflow.com/questions/2496311/implementing-idisposable-on-a-subclass-when-the-parent-also-implements-idisposabl) of [illuminating](http://stackoverflow.com/questions/5042155/cwhat-should-be-the-content-of-the-dispose-method-when-implementing-idisposable) [discussions](http://stackoverflow.com/questions/918614/consider-a-disposable-keyword-in-c) on Stack Overflow. It became apparent that there were [a](http://stackoverflow.com/users/65358/reed-copsey) [few](http://stackoverflow.com/users/263693/stephen-cleary) [regular](http://stackoverflow.com/users/27423/daniel-earwicker) [players](http://stackoverflow.com/users/363751/supercat) who had intelligent things to say on the topic, and I would follow their links and profiles to find more intelligent things they had to say on other topics.

One of these players is [Daniel Eerwicker](http://smellegantcode.wordpress.com), who created a "[General Theory Of Resources](http://smellegantcode.wordpress.com/2009/02/13/general-theory-of-resources/)" in a blog post that I feel obligated to describe as _epic_. It piqued my interest, since this was exactly an area I had questions about. He describes the cultural problem with the IDisposable pattern:

> But these mere technical problems are minor compared with the cultural problem that exists around this technique. These are caused by copious amounts of official or semi-official documentation which confuse it with finalizers, in apparent denial of their different areas of applicability.

I was confused by the documentation he is talking about:) At the end, he proposes his own alternative to Microsoft's IDisposable pattern that he calls "Gateways." It's a long article, but very interesting.
