---
title: "Let the computer do the logic"
date: "2011-12-18"
layout: layouts/post.njk
---

I was writing some code to restrict the input to a NumericUpDown and getting a
little confused by the logic. I wanted to allow any digits or the minus sign for
negatives. But in order to get this behavior, I need to do something when this
is _not_ true. So, rather than applying
[DeMorgan's](http://en.wikipedia.org/wiki/De_Morgan's_laws) in my head, I wrote
out how I was thinking about it, and let
[ReSharper](http://www.jetbrains.com/resharper/) do it for me.

// Restrict numeric up down to integers private void
numericUpDown_KeyPress(object sender, KeyPressEventArgs e) { if
(char.IsDigit(e.KeyChar) || e.KeyChar \== '-') {

    }
    else
    {
        e.Handled \= true;
    }

}

After apply the "Invert 'if'" transformation, that became:

if (!char.IsDigit(e.KeyChar) && e.KeyChar != '-') { e.Handled \= true; }

It's just a small, and trivial, example of letting the computer do what it's
good at and applying yourself to do what you're good at--using tools.
