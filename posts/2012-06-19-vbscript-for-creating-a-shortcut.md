---
title: "VBScript for creating a shortcut"
date: "2012-06-19"
layout: layouts/post.njk
---

I wrote some VBScript for the first time in my life. Here's a script that
creates a shortcut on the desktop, based heavily on the
[answers here](http://stackoverflow.com/q/346107/139). It's pretty rough, but
does the job for now:

```
set objWSHShell = CreateObject("WScript.Shell")

' First argument is the name of the shortcut
' Argument 2 is path to target
sScriptDir = Replace(WScript.ScriptFullName, WScript.ScriptName, "")
sShortcut = objWSHShell.ExpandEnvironmentStrings(WScript.Arguments.Item(0))
sDesktop = objWSHShell.SpecialFolders("Desktop")
sTargetPath = objWSHShell.ExpandEnvironmentStrings(WScript.Arguments.Item(1))
set fso = CreateObject("Scripting.FileSystemObject")
sTargetDir = fso.GetParentFolderName(sTargetPath)

set objSC = objWSHShell.CreateShortcut(sDesktop & "\" & sShortcut)
objSC.TargetPath = sTargetPath
objSC.IconLocation = sScriptDir & "Slick_icon.ico"
objSC.WorkingDirectory = sTargetDir
objSC.Save
```
