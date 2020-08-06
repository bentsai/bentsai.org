---
title: "Cleanup/delete all .svn folders"
date: "2009-06-25"
layout: layouts/post.njk
---

I recently needed to recursively delete all of the .svn folders in a directory
because I was copying them into an existing working copy (and who knows what
would happen if you mixed in .svn folders from a different branch?). The google
helped me find
[this cmd.exe one-liner](http://blog.snakehit.be/2007/08/29/svn-recursively-delete-svn-folders/),
and I'm simply reposting it here for reference:

`FOR /F "tokens=*" %G IN ('DIR /B /AD /S *.svn*') DO RMDIR /S /Q "%G"`

This is assuming you're sitting at the root folder where you want to recurse
from.
