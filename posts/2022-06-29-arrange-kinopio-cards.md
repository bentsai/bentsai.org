---
title: "Arrange Kinopio cards"
date: "2022-06-29T14:31:32-0400"
layout: layouts/post.njk
---

I wrote a little [deno](https://deno.land) script that arranges cards in a
Kinopio space in reverse-chronological order. This is a bud of an idea where I
could use Kinopio as a log with the most recent stuff on top. And this is all
automatically done.

For future:

- Abstract secrets
- Put in repository
- Experiment with grid layout
- Comment cards are excluded
- Comment cards that are connected move relatively with the card it is connected
  to. This way I can annotate.

```javascript
const jsonResponse = await fetch("https://api.kinopio.club/space/<space ID>")
const spaceJson = await jsonResponse.json()
// console.log(spaceJson);

const cards = spaceJson.cards
const sortedCards = cards.sort((a: any, b: any) => a.createdAt < b.createdAt)

console.log(sortedCards)

const patchCard = async (card: any) => {
  const headers = new Headers({
    "Content-Type": "application/json",
    "Cache-Control": "must-revalidate, no-store, no-cache, private",
    Authorization: "<API KEY>",
  })
  try {
    const response = await fetch("https://api.kinopio.club/card", {
      method: "PATCH",
      headers,
      body: JSON.stringify(card),
    })
    await response.json()
  } catch (error) {
    console.error(error)
  }
}

let currentY = 200
const PADDING = 24
for (const card of sortedCards) {
  console.log(card.id, card.y, currentY)
  if (card.x !== 100 || card.y !== currentY) {
    patchCard({ ...card, x: 100, y: currentY })
  }
  currentY += card.height + PADDING
}
```

Also here: https://gist.github.com/bentsai/5014dd575358e7e56d85146aac86a018
