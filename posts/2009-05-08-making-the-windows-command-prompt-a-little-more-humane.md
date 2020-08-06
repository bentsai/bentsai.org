---
title: "Making the Windows Command Prompt a little more humane"
date: "2009-05-08"
layout: layouts/post.njk
---

If you spend a lot of time in the Windows command prompt, here are some tweaks
you can make so the experience is more pleasant.

# Changing the appearance

The default font and color is rather plain. I like to change to a ClearType font
so I get anti-aliasing, and then bump up the contrast with a throw-back
monochrome theme. Under Properties | Font, Lucida Console is a good alternative.
It's probably your only alternative. If you're feeling ambitious, you can
[add to this list of fonts](http://www.watchingthenet.com/how-to-add-and-change-fonts-in-windows-command-prompt.html "How to add and change fonts in windows command prompt").

I also increase my buffer size (so I can scroll back farther) and increase the
window size (so I can see more).

\[caption id="attachment_30" align="alignnone" width="244" caption="(Properties
| Layout, Screen Buffer Size > Height: 500, Window Size > Height:
50)"\]![Properties | Layout](http://bentsai.files.wordpress.com/2009/05/properties.png?w=244 "Properties | Layout")\[/caption\]

The default prompt puts your cursor on the same line as your current working
directory. You can modify your prompt by changing the PROMPT environment
variable. I set mine to \[$p\]$\_\$g so that my cursor is on the next line, and
always on the left of my terminal. There's
[more information on Hanselman's blog](http://www.hanselman.com/blog/ABetterPROMPTForCMDEXEOrCoolPromptEnvironmentVariablesAndANiceTransparentMultiprompt.aspx),
where I lifted much of this.

Tab completion should be on by default in Windows XP. But if it's not enabled
for some reason,
[please enable it](http://technet.microsoft.com/en-us/kb/kb00244407.aspx). And,
did you know cmd.exe has a command history dialog? Hit F7 to get a list of your
recent commands:

![My command prompt with history dialog popped up](http://bentsai.files.wordpress.com/2009/05/cmd_prompt.png?w=279 "cmd_prompt")

I hope that makes your command prompt experience more enjoyable. The next thing
I'd like to get in the habit of using more is
[pushd and popd](http://www.hanselman.com/blog/PromptsAlongWithPushDAndPopD.aspx)...
