---
title: "Kinopio JSON text tricks"
date: "2020-09-18"
layout: layouts/post.njk
---

I realize this is super-niche information, but I've been lightly playing around
with the [Kinopio API](https://help.kinopio.club/api/) and the JSON it returns.
You'll need [`curl`](https://curl.haxx.se),
[`jq`](https://stedolan.github.io/jq/), and
[`rg`](https://github.com/BurntSushi/ripgrep).

Here's the shell incantation for getting a list of cards in a list sorted in
created order:

```shell
export KINOPIO_API_KEY=<enter `JSON.parse(localStorage.user).apiKey` in console>
export KINOPIO_SPACE_KEY=<grab from URL>

curl -H "Authorization: $KINOPIO_API_KEY" https://api.kinopio.club/space/$KINOPIO_SPACE_KEY | jq -r  '.cards | .[] | .createdAt + "\t" + (.name | tojson)' | sort
```

The `jq` part is the more interesting stuff:

```shell
cat space.json | jq -r  '.cards | .[] | .createdAt + "\t" + (.name | tojson)'
```

It grabs all the cards, then prints out the created time, a tab, and the escaped
card name.

This is just text now, so you can do Unix-style filtering and manipulations. For
example, list all the incomplete tasks by piping through `rg`:

```shell
cat space.json | jq -r  '.cards | .[] | .createdAt + "\t" + (.name | tojson)' | rg "\"\[\]"
```

I've formatted it to kinda look like a
[twtxt](https://twtxt.readthedocs.io/en/latest/) feed. So for example, here are
the incomplete tasks on
[the Kinopio roadmap](https://kinopio.club/-kinopio-roadmap-6TRE21gchHI7alHLuwzd5).
Since it's public, I don't need the API key:

```shell
% curl -s https://api.kinopio.club/space/6TRE21gchHI7alHLuwzd5 | jq -r  '.cards | .[] | .createdAt + "\t" + (.name | tojson)' | sort | rg "\"\[\]"
2019-12-31T16:19:09.398Z	"[] for power users - may need to prioritize features that get new people in before these"
2019-12-31T16:19:09.412Z	"[] Dark mode 🌙"
2020-01-02T02:19:46.881Z	"[] two new frames"
2020-05-25T14:59:23.876Z	"[] Better undo (Cmd z to undo Any operation, not just card delete)"
2020-06-15T15:12:20.886Z	"[] bi-directional tabs/labels that allow bottom up organization \n\nSpec: https://www.are.na/block/7674650"
2020-08-11T14:56:21.976Z	"[] marketing outreach"
```

😜
