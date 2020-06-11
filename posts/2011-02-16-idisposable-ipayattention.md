---
title: "IDisposable: IPayAttention"
date: "2011-02-16"
layout: layouts/post.njk
---

#### Executive Summary

What do I do with the `IDisposable` interface? What is it for? Doesn't .NET manage resources?

1. .NET does not manage resources.
2. If an object is `IDisposable`, you must `Dispose` it.

## A realization

Having worked in .NET for many years, I'm abashed to admit that I've only recently realized the need to manage resources. For a long time, I figured this was detail handled by the framework. After all, wasn't this the promise of managed code: increase developer productivity by providing a consistent and robust framework that abstracts away and "manages" many mundane details, particularly memory management?

Well, .NET has certainly come through on its promise on making me more productive, but I haven't fulfilled my end of the bargain of being an informed software engineer. I'd become lulled by the convenience afforded by the framework and stopped thinking about what was going on below me. Sigh, another example of [the law of leaky abstractions](http://www.joelonsoftware.com/articles/LeakyAbstractions.html). I should know better.

## More than one kind of resource

My first problem in my understanding was that I was bundling all resources under the category of "things that I don't need to worry about because .NET will take care of them for me." Obviously, I was wrong. [Joe Duffy](http://www.bluebytesoftware.com/blog/default.aspx) states the distinction pretty clearly in his post entitled [DG Update: Dispose, Finalization, and Resource Management](http://www.bluebytesoftware.com/blog/2005/04/08/DGUpdateDisposeFinalizationAndResourceManagement.aspx):

> The CLR’s garbage collector (GC) does an amazing job at managing memory allocated directly to CLR objects, but was explicitly not designed to deal with unmanaged memory and OS-managed resources.

I carelessly assumed that since my application compiled without warnings, wasn't running out of memory, or indicating otherwise that things were amiss, that everything was being taken care of. [Krzystztof Cwalina](http://blogs.msdn.com/b/kcwalina/) reiterates this point in the same article, which I will re-reiterate, since it has eluded me for years:

> Many people who hear about the Dispose pattern for the first time complain that the GC isn’t doing its job. They think it should collect resources, and that this is just like having to manage resources as you did in the unmanaged world. **The truth is that the GC was never meant to manage resources.** It was designed to manage memory and it is excellent in doing just that. \[emphasis mine\]

I am one of the "many people." **The GC manages memory but not resources.** At least I'm not alone. (By the way, these guys have a lot of smart things to say about the .NET Framework.)

## Managed and unmanaged

Another big problem I encountered while researching this topic was understanding the terms "managed" and "unmanaged." When you're working in .NET, you're almost never dealing directly with unmanaged resources such as files, handles, and streams. But, you _are_ at times dealing with objects that eventually interact with an unmanaged resource. **Even in cases when you are exclusively dealing with managed code, you're not out of the woods yet.**

For example, if you're working with Windows Forms, you'll likely be creating [`Font`](http://msdn.microsoft.com/en-us/library/system.drawing.font.aspx) and [`Bitmap`](http://msdn.microsoft.com/en-us/library/system.drawing.bitmap.aspx) objects to draw to the screen. These are both managed types; however, they ultimately manipulate GDI+ handles under the floor. How do you know whether or not this is the case for other classes where it may not be as obvious? This is where the [`IDisposable` interface](http://msdn.microsoft.com/en-us/library/system.idisposable.aspx) comes in.

## So, I should pay attention to `IDisposable`, huh?

.NET does _not_ deallocate resources deterministically. This is a problem, especially if you are using expensive resources like file handles. In order to support deterministic resource deallocation, Microsoft introduced the `IDisposable` interface. For a long time, I blissfully ignored the documentation and other hints that I need to do something with `IDisposable` objects. A comment by [Clemens Szyperski](http://research.microsoft.com/en-us/um/people/cszypers/) on the aforementioned [post](http://www.bluebytesoftware.com/blog/2005/04/08/DGUpdateDisposeFinalizationAndResourceManagement.aspx) aptly describes my attitude and goes on to present a good guideline:

> The only problem is that automatic management of memory and objects makes it difficult to ensure that resources held by objects are released deterministically (that is, early). The reliance on the GC can lead programmers to think that they don't need to worry about this anymore, which is not the case. In fact, **any object that implements `IDisposable` should be mentally tagged with a red flag and should not be allowed to fall off the scene without Dispose having been called.** \[emphasis mine\]

**The answer is yes.** And yes, I was surprised that this had never really come up. I thought of all the .NET code I've written and lamented the fallen objects whose cries had been silenced by layers of abstraction. Not really. But I did think, "man, I guess my code hasn't been that robust."

Now I'm waving the red flag so that others may not fall into the same laziness as I did. Armed with this new knowledge and some more red flags in our pockets, let's explore how to properly implement the interface. In a future post.
