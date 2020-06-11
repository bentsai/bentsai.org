---
title: "Let The Computer Do It"
date: "2011-12-07"
layout: layouts/post.njk
---

I was writing some code to restrict the input to a [NumericUpDown](http://msdn.microsoft.com/en-us/library/729xt55s.aspx) and getting a little confused by the logic. I wanted to allow any digits or the minus sign for negatives. But in order to get this behavior, I need to do something when this is _not_ true. So, rather than applying [DeMorgan's](http://en.wikipedia.org/wiki/De_Morgan%27s_laws) in my head, I wrote out how I was thinking about it, and let [ReSharper](http://www.jetbrains.com/resharper/) do it for me.

\[code lang="csharp"\]// Restrict numeric up down to integers </code> private void numericUpDown_KeyPress(object sender, KeyPressEventArgs e) { if (char.IsDigit(e.KeyChar) || e.KeyChar == '-') { } else { e.Handled = true; } }\[/code\]

After applying the \`Invert 'if'\` transformation, that logic became:

\[code lang="csharp"\]if (!char.IsDigit(e.KeyChar) && e.KeyChar != '-') { e.Handled = true; }\[/code\]

It's just a small, and trivial, example of letting the computer do what it's good at and applying yourself to do what you're good at: using tools.
