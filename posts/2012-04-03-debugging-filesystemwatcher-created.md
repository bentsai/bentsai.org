---
title: "Debugging FileSystemWatcher.Created"
date: "2012-04-03"
layout: layouts/post.njk
---

Today's debugging adventure involved an ActiveX control that uses `FileSystemWatcher` to watch for files to be copied into a folder and then spits out some log messages onto the page. The behavior I was seeing was that sometimes when I copied a valid file into the watched folder, Internet Explorer would crash. After putting in additional logging, I found that the code was throwing an IOException. Searching for how to really open a file read-only, I [learned about the `FileShare` parameter](http://aautar.digital-radiation.com/blog/?p=1292).

This didn't fix my problem, though. After some more fuddling around and talking to coworkers, I realized that the problem may be more related to the FileSystemWatcher.Created event. It gets raised when the file first gets created, and if you try to access it before it's done, you'll get an IOException. The best solution I could find is to [simply catch that exception, sleep, and try again](http://bloggingabout.net/blogs/jschreuder/archive/2006/07/06/12886.aspx). I wrote some code like this:

```
    public static bool IsLockAvailable(string filePath)
    {
        try
        {
            using (File.Open(filePath, FileMode.Open, FileAccess.Read, FileShare.ReadWrite))
            {
                return true;
            }
        }
        catch (IOException)
        {
            return false;
        }
    }

    public static void WaitForLockOnFile(string filePath)
    {
        if (File.Exists(filePath))
        {
            while (!IsLockAvailable((filePath)))
            {
                Thread.Sleep(50);
            }
        }
    }
```

And called `WaitForLockOnFile()` before trying to do anything with the file in my `Created` handler.
