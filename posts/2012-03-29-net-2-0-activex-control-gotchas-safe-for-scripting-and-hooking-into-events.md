---
title:
  ".NET 2.0 ActiveX Control Gotchas (Safe for Scripting and Hooking into Events)"
date: "2012-03-29"
layout: layouts/post.njk
---

I was trying to figure out how to prevent IE from blocking an ActiveX control I
was working on. In .NET, it seems like the easiest way is to implement the
[IObjectSafety](<http://msdn.microsoft.com/en-us/library/aa768224(v=VS.85).aspx>)
interface. There were a few examples I found for doing this, but none of them
made it clear that the Guid for the interface mattered, except this one.
