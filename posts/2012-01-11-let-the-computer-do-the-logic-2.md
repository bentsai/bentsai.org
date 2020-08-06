---
title: "Let the computer do the logic"
date: "2012-01-11"
layout: layouts/post.njk
---

I was writing some code to restrict the input to a NumericUpDown and getting a
little confused by the logic. I wanted to allow any digits or the minus sign for
negatives. But in order to get this behavior, I need to do something when this
is not true. So, rather than applying DeMorgan's in my head, I wrote out how I
was thinking about it, and let ReSharper do it for me.

:::csharp // Restrict numeric up down to integers private void
numericUpDown_KeyPress(object sender, KeyPressEventArgs e) { if
(char.IsDigit(e.KeyChar) || e.KeyChar == '-') {

} else { e.Handled = true; } }

After apply the "Invert 'if'" transformation, that became:

:::csharp if (!char.IsDigit(e.KeyChar) && e.KeyChar != '-') { e.Handled = true;
}

It's just a small, and trivial, example of letting the computer do what it's
good at and applying yourself to do what you're good at--using tools.
