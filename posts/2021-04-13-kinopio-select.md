---
title: "Kinopio Select"
date: "2021-04-13"
layout: layouts/post.njk
---

I had some
[general discussion on Futureland recently around Kinopio](https://futureland.tv/bentsai/kinopio-meta),
and also [pirijan](https://twitter.com/pketh) is starting to
[spec out a design for the feature](https://kinopio.club/-spec-card-grouping-vDI37VdZQEoCXeYSI8HeP).
This engendered some tangential thoughts around more advanced selection features
because part of the motivation for grouping is to make it easier to manipulate
and organize cards.

I
[wondered whether he could expose some functionality](https://futureland.tv/bentsai/kinopio-meta/61385)
that would allow me to implement some features in the browser:

- select cards by name
- select cards by array of `id`s
- select cards by region (x, y, width, height)

He responded with some keywords that I could search on (`veux` and `state`) and
[found how I could access the app's state](https://forum.vuejs.org/t/how-to-access-vue-from-chrome-console/3606/7),
which wonderfully allows me to programmatically select cards by pushing card
`id`s into an array! Poking around, here is what I learned:

I can get the Vue state via

```javascript
document.querySelector("#app").__vue__.$store.state
```

There's an array in there that represents what cards are selected called
`multipleCardsSelectedIds`. Finally, I learned that the space information is in
`currentSpace`. So armed with that information, I cobbled to gather some logic
to accomplish some of interesting selection functions.

**Select direct descendant cards**

There's an existing feature where you Opt-Click a card, and all the connected
cards get selected. But sometimes, you only want the cards that are directly
connected by one level.

Select the parent card in the UI. Then run this function:

```javascript
let selectDirectDescendants = () => {
  const vueState = document.querySelector("#app").__vue__.$store.state
  const parentCardId = vueState.multipleCardsSelectedIds.pop()
  vueState.multipleCardsSelectedIds = []
  vueState.multipleCardsSelectedIds = vueState.currentSpace.connections
    .filter(c => c.startCardId === parentCardId)
    .map(c => c.endCardId)
}

selectDirectDescendants()
```

![select direct descendants](../../img/selectDirectDescendants.mov)

**Select cards by filtered connection**

Another useful thing to select are cards by their connection. Currently, you can
filter by connections, and see them visually focused. But how about then select
these cards?

```javascript
let selectByFilteredConnection = () => {
  const vueState = document.querySelector("#app").__vue__.$store.state
  const connectionId = vueState.filteredConnectionTypeIds.pop()
  vueState.filteredConnectionTypeIds = []
  const cards = []
  vueState.currentSpace.connections
    .filter(c => c.connectionTypeId == connectionId)
    .forEach(c => {
      cards.push(c.startCardId)
      cards.push(c.endCardId)
    })
  vueState.multipleCardsSelectedIds = cards
}

selectByFilteredConnection()
```

![select by filtered connection](../../img/selectByFiltered.mov)

## Next steps

- Implement selecting by name and region
- Wrap these functions in a more consumable form (bookmarklet???)
