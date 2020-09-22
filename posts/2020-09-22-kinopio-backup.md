---
title: "Kinopio backup one-liner"
date: "2020-09-22"
layout: layouts/post.njk
---

I've been using Kinopio for
[all](https://kinopio.club/weekly-planner-with-examples--juvzn8qrBfW4nvqH6IGKD)
[sorts](https://kinopio.club/magic-quadrant-7GZrOrOw2diOUc5Njb98z) of
[things](https://kinopio.club/-backgrounds-images-XGLHAgCu2nmMMMoxKpD2Q), so
it's important to me I don't lose any of my work.

Kinopio's got an API which enables me to program this. I decided to write a
shell script because I didn't want to introduce any other languages to this
(Python or JavaScript would have been my other choices), hoping to keep this
accessible and not making folks deal with setting up their environment. I'm not
sure how well I've achieved this, but I did end up using `awk` for the first
time, so a small win there.

Here it is, allow me to explain:

```shell
KINOPIO_API_KEY=<your key> \
curl -H "Authorization: $KINOPIO_API_KEY" https://api.kinopio.club/user/spaces | \
jq -r ".[] | .id + \",\" + (.name | tojson)" | \
awk -v key="$KINOPIO_API_KEY" '{ print "curl -H \"Authorization: "key"\" https://api.kinopio.club/space/"$1" > "$2".json" }' FS=, OFS=, | \
xargs -0 -n1 bash -c
```

- The first line sets the Kinopio API key as a temporary environment variable.
  Find the key by running `JSON.parse(localStorage.user).apiKey` in the console
  while logged in to Kinopio.
- The first `curl` command gets all of your spaces.
- The `jq` line processes and filters the spaces JSON into comma-delimited
  strings (one Kinopio space per line) with the space ID and name
  (`YE-kaoG5T6Xetw2Jdiyfi,"[post] Joining Kinopio Club"`). I kept the name in
  quotes so later I don't have to escape it for spaces.
- I use `awk` to parse the `<id>,<name>` and construct the `curl` command for
  getting the space (which is the backup JSON). This redirects the output into a
  JSON file with the name of the space.
- Finally, `xargs` enables me to do this for each space.

It took me many hours to figure this out. I got stuck for a while when I had
gotten the list of spaces and their ids, but I didn't know how to take that
output to create the final command. I was trying to manipulate stdin, then
thought I should use variables instead. I don't remember my search terms, but I
eventually stumbled on using `awk` to write the new command, which is the
insight I needed to finish the job.

I've got a private GitHub repo where I've added this as an
[Action](https://github.com/features/actions), so now every hour, this runs and
commits any changes to the repo.

Sometimes I'm getting a 401 from the Kinopio API, so I may have to tweak the
timing. I wonder if I'm being throttled :)
