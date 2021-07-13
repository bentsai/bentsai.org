---
title: "Invert Selection (Kinopio)"
date: "2021-07-12"
layout: layouts/post.njk
---

I wrote another bookmarklet. This time to invert your selection in Kinopio. Say
you have a few cards you want to keep in place. Select them, then run this.
You'll get all the other cards in the space selected. Combine this with other
existing selection methods and it’s pretty powerful.

It’s nice for making room in a crowded space:

![selecting and moving cards around](https://us-east-1.linodeobjects.com/kinopio-uploads/lbmglGUsQ75ed6IkdV7Bp/Screen-Recording-2021-07-12-at-11.52.03-AM.gif)

The code is here.

```
let vueState = document.querySelector(“#app”).__vue__.$store.state;
vueState.multipleCardsSelectedIds =
    vueState.currentSpace.cards
        .filter(c => !vueState.multipleCardsSelectedIds.includes(c.id))
        .map(c => c.id)
```

You could paste that snippet into your console and run it. Or, I made a
bookmarklet. You can also drag the following link into tour bookmarks bar. This
runs JavaScript in your browser so take necessary precautions.

<a href=“javascript:(function()%7Blet%20vueState%20%3D%20document.querySelector(%22%23app%22).__vue__.%24store.state%3B%0AvueState.multipleCardsSelectedIds%20%3D%20vueState.currentSpace.cards.filter(c%20%3D%3E%20!vueState.multipleCardsSelectedIds.includes(c.id)).map(c%20%3D%3E%20c.id)%7D)()%3B”>Invert
selection</a>

On that note, I discovered that Vivaldi, my current default browser, doesn’t
support bookmarklets. I guess it makes sense since you can do pretty gnarly and
harmful things by running JavaScript willy-nilly.
