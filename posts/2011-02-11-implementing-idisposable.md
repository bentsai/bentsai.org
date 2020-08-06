---
title: "Implementing IDisposable?"
date: "2011-02-11"
layout: layouts/post.njk
---

Implementing
[IDisposable](<http://msdn.microsoft.com/en-us/library/system.idisposable(v=VS.90).aspx>)
is not straightforward. There is an
"[official](<http://msdn.microsoft.com/en-us/library/b1yfkh5e(v=VS.90).aspx>)"
way to do it:

\[sourcecode language="csharp" collapse="true"\] public class Base: IDisposable
{ private bool disposed = false;

//Implement IDisposable. public void Dispose() { Dispose(true);
GC.SuppressFinalize(this); }

protected virtual void Dispose(bool disposing) { if (!disposed) { if (disposing)
{ // Free other state (managed objects). } // Free your own state (unmanaged
objects). // Set large fields to null. disposed = true; } }

// Use C# destructor syntax for finalization code. ~Base() { // Simply call
Dispose(false). Dispose (false); } }

// Design pattern for a derived class. public class Derived: Base { private bool
disposed = false;

protected override void Dispose(bool disposing) { if (!disposed) { if
(disposing) { // Release managed resources. } // Release unmanaged resources. //
Set large fields to null. // Call Dispose on your base class. disposed = true; }
base.Dispose(disposing); } // The derived class does not have a Finalize method
// or a Dispose method without parameters because it inherits // them from the
base class. } \[/sourcecode\]

But it
[may not be the best practice](http://nitoprograms.blogspot.com/2009/08/how-to-implement-idisposable-and.html)
anymore. Stephen Cleary wrote an awesome
[Code Project article](http://www.codeproject.com/KB/dotnet/IDisposable.aspx)
and has a few
[blog](http://nitoprograms.blogspot.com/2009/08/first-rule-of-implementing-idisposable.html)
[posts](http://nitoprograms.blogspot.com/2009/08/second-rule-of-implementing-idisposable.html)
[about](http://nitoprograms.blogspot.com/2009/08/third-rule-of-implementing-idisposable.html)
[this](http://nitoprograms.blogspot.com/2010/02/how-to-implement-idisposable-and.html).
He says that Microsoft doesn't even adhere to the old pattern, starting in .NET
2.0. I have more learning to do.
