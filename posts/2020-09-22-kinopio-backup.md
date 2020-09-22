---
title: "Kinopio backup one-liner"
date: "2020-09-22"
layout: layouts/post.njk
---

```shell
curl -H "Authorization: $KINOPIO_API_KEY" https://api.kinopio.club/user/spaces | \
jq -r ".[] | .id + \",\" + (.name | tojson)" | \
awk '{ print "curl -H \"Authorization: $KINOPIO_API_KEY\" https://api.kinopio.club/space/"$1" > "$2".json" }' FS=, OFS=, | \
xargs -0 -n1 bash -c
```
