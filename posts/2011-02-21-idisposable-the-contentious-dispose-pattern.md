---
title: "IDisposable: The contentious Dispose pattern"
date: "2011-02-21"
layout: layouts/post.njk
---

## Yucky stuff

I convinced myself that [I needed to take some action with the IDisposable interface](http://bentsai.wordpress.com/2011/02/16/idisposable-ipayattention/ "IDisposable: IPayAttention"), so I started to do some research on best practices. The first place I looked was the MSDN documentation, where I found the "official" pattern:

\[sourcecode language="csharp"\] public class Base: IDisposable { private bool disposed = false;

//Implement IDisposable. public void Dispose() { Dispose(true); GC.SuppressFinalize(this); }

protected virtual void Dispose(bool disposing) { if (!disposed) { if (disposing) { // Free other state (managed objects). } // Free your own state (unmanaged objects). // Set large fields to null. disposed = true; } }

// Use C# destructor syntax for finalization code. ~Base() { // Simply call Dispose(false). Dispose (false); } } \[/sourcecode\]

The first thing I noticed was that it doesn't look very elegant. This surprised me because, in general, the .NET framework is very elegant and well-crafted. What's this business with calling `GC.SuppressFinalize`, the `disposing` flag, and the scary C# finalizer with C++ destructor syntax? (I will hereon refer to them as "yucky stuff.") There must be a better way, or there's something I'm not understanding here. And I didn't want to go blindly apply this pattern everywhere before understanding it some more. This prompted more digging.

## What Your Mother Never Told You About Resource Deallocation

Stephen Cleary wrote [an excellent article](http://www.codeproject.com/KB/dotnet/idisposable.aspx) that covers the problems with IDisposable and also proposes some of his own best practices that simplify the pattern significantly. I highly recommend reading the entire article. He validates my reaction that IDisposable objects are cumbersome to use, and that the Microsoft-endorsed pattern is needlessly complex.

The main issue is that the pattern is designed for the general case that handles both explicit and implicit resource cleanup. But I believe most .NET developers are normally concerned only with explicit cleanup, and so **most of the yucky stuff becomes extraneous.**

As I learned, if you design your classes properly, you can simplify the pattern significantly:

\[sourcecode language="csharp"\] public sealed class BetterWay : IDisposable { Font coolFont; public BetterWay() { coolFont = new Font("Comic Sans", 12); }

public void Dispose() { coolFont.Dispose(); } } \[/sourcecode\]

What happened to all the yucky stuffs? Stephen Cleary's "Disposable Design Principle" makes them go away:

- For each unmanaged resource, create exactly one `IDisposable` class that is responsible for freeing it. This wrapper class is considered a managed resource. He calls these **Level 0** types.
- Never derive from such a wrapper.
- Create other managed `IDisposable` types that own managed resources and/or derive from a type that owns managed resources. These are **Level 1** types.
- Never create a type that owns both managed and unmanaged resources.

**Level 0** types only deal with unmanaged resources. **Level 1** types only deal with managed resources, and thus, implementing IDisposable for **Level 1** types is simple. Since most .NET developers live in **Level 1**\-land, they can use this pattern and be happier. Regarding this implementation, Stephen Cleary notes:

- `Dispose` is safe to be called multiple times because it is safe to call `IDisposable.Dispose` multiple times, and that's all it does.
- Level 1 type should not have finalizers; they wouldn't be able to do anything anyway, since managed code cannot be accessed.
- It is not necessary to call `GC.KeepAlive(this)` at the end of `Dispose`. Even though it is possible for the garbage collector to collect this object while `Dispose` is still running, this is not dangerous since all the resources being disposed are managed, and neither this type nor any derived types have finalizers.
- Calling `GC.SuppressFinalize(this)` is likewise unnecessary because neither this type nor any derived types have finalizers.

He also covers this implementation, which he calls "[The Second Rule Of Implementing IDisposable](http://nitoprograms.blogspot.com/2009/08/second-rule-of-implementing-idisposable.html)" on [his blog](http://nitoprograms.blogspot.com/). (Implementing IDisposable for **Level 0** types is harder; you should read the rest of the article and refer to "[The Third Rule of Implementing IDisposable](http://nitoprograms.blogspot.com/2009/08/third-rule-of-implementing-idisposable.html).")

## Feeling good about it

Stephen Cleary's best practices were looking more attractive, but I needed more evidence to feel comfortable about deviating from the Microsoft-sanctioned way. As I searched more, I found others who supported my desire to use a different pattern. This [Stack Overflow answer and follow-up comments](http://stackoverflow.com/questions/1136210/am-i-implementing-idisposable-correctly/1136252#1136252) debate this very topic. Jon Skeet, as usual, does [a good job of explaining the issue](http://stackoverflow.com/questions/574019/calling-null-on-a-class-vs-dispose/574659#574659), and states that "if you seal your classes, it makes life a lot easier: the pattern of overriding `Dispose` to call a new virtual `Dispose(bool)` method etc is only relevant when your class is designed for inheritance." I found [another post](http://codecrafter.blogspot.com/2010/01/revisiting-idisposable.html) that was similar in spirit. And even [a proposal for changing C#](http://smellegantcode.wordpress.com/2007/11/30/a-new-use-for-the-c-using-keyword/), prompted by the difficulty of the official pattern.

Now that I understand things a lot better, I'll be using this new pattern when designing my classes. Less yucky stuff.
