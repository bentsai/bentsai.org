---
title: "Kinopio Bookmarklet"
date: "2021-04-14"
layout: layouts/post.njk
---

## Select all cards with this string

You can use this to select all cards with a specific string, including tags
(because that's just part of the card name).

Drag this link into your bookmarks bar:

<a href="javascript:(function()%7Blet%20searchTerm%20%3D%20window.prompt(%22Select%20all%20cards%20with%20this%20string%22%2C%20%22Search%20term%22)%3B%0Alet%20vueState%20%3D%20document.querySelector(%22%23app%22).__vue__.%24store.state%0AvueState.multipleCardsSelectedIds%20%3D%20vueState.currentSpace.cards.filter(c%20%3D%3E%20c.name.includes(searchTerm)%20).map(c%20%3D%3E%20c.id)%7D)()%3B">Select
cards</a>

Here's a demo...

![search demo](../../img/search-bookmarklet.gif)

I used https://caiorss.github.io/bookmarklet-maker/ to do some of the ancillary
things like wrapping in an anonymous function, encoding it.

Here's the code prior to the processing:

```javascript
let searchTerm = window.prompt(
  "Select all cards with this string",
  "Search term"
)
let vueState = document.querySelector("#app").__vue__.$store.state
vueState.multipleCardsSelectedIds = vueState.currentSpace.cards
  .filter(c => c.name.includes(searchTerm))
  .map(c => c.id)
```

## Next up and ideas

There a bunch of new bookmarklets I'd like to write:

- Write a
  [word count widget](https://club.kinopio.club/t/desk-accessory-widget-ideas/198/4?u=bentsai)
- Wrap the
  [descendant select and filtered connection code](https://www.bentsai.org/posts/2021-04-13-kinopio-select/)
  in a bookmarklet.
- Space statistics widget
- Select cards by regular expression
