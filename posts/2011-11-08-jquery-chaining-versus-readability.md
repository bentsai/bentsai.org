---
title: "jQuery chaining versus readability"
date: "2011-11-08"
layout: layouts/post.njk
---

As I was cleaning up my jQuery code, I came across some jQuery syntax that I
wasn't sure how to format. In my app, I have a lot of jQuery Mobile pages that
have event handlers attached to them. At the moment, I have two formats, but I
wanted to unify these formats for consistency. The first looks like this:
\[sourcecode lang="javascript"\] manOpsPage.data('sideButtonsClass',
'.ui-btn-text');

manOpsPage.bind('pagebeforeshow', function () {
$(document).bind('keydown.side-buttons', 'e', function () {
$('#label-6').click();
}); });

manOpsPage.bind('pagehide', function () { var radioButtons =
$('#manual-operations input\[type="radio"\]'); radioButtons.prop('checked', false); $('#radio-lap').prop('checked',
true); radioButtons.checkboxradio('refresh'); });\[/sourcecode\] The second uses
jQuery chaining syntax, which takes advantage of the fact that jQuery selections
return the object, so I have chained my calls to
[`bind`](http://api.jquery.com/bind/) together: \[sourcecode lang="javascript"\]
$('div\[data-role="page"\]').bind('pagebeforeshow',
function (e, ui) {
ASCTD.setupSideButtons($(this));
}).bind('pagehide', function (e, ui) {
ASCTD.removeSideButtons($(this));
}).bind('waitingForSequence', function () { if (ASCTD.uar.blocks\[0\].id === 21)
{ // We got a subtest complete sequence, so we are done. return; }
$.mobile.showPageLoadingMsg(); }).bind('sequenceStarted', function () {
\$.mobile.hidePageLoadingMsg(); });\[/sourcecode\] Initially, I was planning on
converting all the syntax to the latter formatting, since it is more compact.
But as I continued on this path, I became less and less enamored with how the
syntax looked and "felt." The compact nature actually made it less readable. And
I noticed that refactoring this code was a little harder (e.g., removing a link
in the chain), since selecting the link required a bit of precision--I had to
get go from one close paren to the next period, both of which were in the middle
of a line.

An oft-cited
[advantage of using chaining](http://tobiasahlin.com/blog/quick-guide-chaining-in-jquery/)
is that it significantly improves performance. But since I am already caching
the jQuery selection, this point wasn't relevant.

In the end, I decided to go for
[readability over condensed code](http://davidwalsh.name/javascript-short-code).
Using jQuery chaining seemed clever at first, but there turned out to be little
benefit. At this point, I'm not concerned with saving bytes, and I figure that's
what compressors and minifiers are for...

**Bonus:** Even though I won't be using chaining in this case, along the way I
did learn about the [`end()`](http://api.jquery.com/end/) method, which allows
you to
[continue chaining by reverting to the previous selection](http://www.tvidesign.co.uk/blog/improve-your-jquery-25-excellent-tips.aspx#tip10)
once you've drilled down in the chain.
