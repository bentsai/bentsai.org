---
title: 'disposing: "You keep using that word. I do not think it means what you think it means."'
date: "2011-02-11"
layout: layouts/post.njk
---

Something notable that I _have_ learned so far is that the `disposing` boolean parameter for the `IDisposable.Dispose(bool disposing)` override does **not** answer the question: "Are we in the process of disposing?" Rather, it indicates how the method was called:

> Dispose(bool disposing) executes in two distinct scenarios. If disposing equals true, the method has been called directly or indirectly by a user's code. Managed and unmanaged resources can be disposed. If disposing equals false, the method has been called by the  runtime from inside the finalizer and you should not reference other objects. Only unmanaged resources can be disposed.
