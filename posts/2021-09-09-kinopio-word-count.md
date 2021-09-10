---
title: "Word count in Kinopio (bookmarklet)"
date: "2021-09-09"
layout: layouts/post.njk
---

Prompted by [humdrum](http://tiv.today)'s
[post in Futureland about not using Kinopio for his morning pages because it lacked word count](https://futureland.tv/humdrum/entry/101835?fullscreen=1),
I hacked together this code to add word count via a bookmarklet.

```javascript
let wordCountWrapper = document.createElement("div")
wordCountWrapper.className = "button-wrap"
let wordCountButton = document.createElement("button")
wordCountButton.id = "word-count"
wordCountWrapper.appendChild(wordCountButton)
document.querySelector(".top-buttons-wrap").appendChild(wordCountWrapper)
let intervalID = setInterval(
  () =>
    (document.querySelector("#word-count").innerHTML = document
      .querySelector("#app")
      .__vue__.$store.state.currentSpace.cards.reduce(
        (acc, current) => acc + current.name.split(/\s+/).length,
        0
      )),
  1000
)
```

And again, I used https://caiorss.github.io/bookmarklet-maker/ to generate the
bookmarklet. For good hygiene, you should probably generate it yourself. But
here's also one you can use by dragging to your bookmarks:

<a href="javascript:(function()%7Blet%20wordCountWrapper%20%3D%20document.createElement(%22div%22)%3B%0AwordCountWrapper.className%20%3D%20%22button-wrap%22%3B%0Alet%20wordCountButton%20%3D%20document.createElement(%22button%22)%3B%0AwordCountButton.id%20%3D%20%22word-count%22%3B%0AwordCountWrapper.appendChild(wordCountButton)%3B%0Adocument.querySelector(%22.top-buttons-wrap%22).appendChild(wordCountWrapper)%3B%0Alet%20intervalID%20%3D%20setInterval(()%20%3D%3E%20document.querySelector(%22%23word-count%22).innerHTML%20%3D%20document.querySelector(%22%23app%22).__vue__.%24store.state.currentSpace.cards.reduce((acc%2C%20current)%20%3D%3E%20acc%20%2B%20current.name.split(%2F%5Cs%2B%2F).length%2C%200)%2C%201000)%3B%7D)()%3B">word
count</a>

In order to get this working in iOS, the easiest way is to add this bookmarklet
to Safari on Mac, and then let iCloud sync it over.

I put the word count in a button in the upper-right corner like so:

![screenshot of Kinopio with word count](https://us-east-1.linodeobjects.com/kinopio-uploads/SaLjyDgbsLQKX6hlrsrwh/image.png)
