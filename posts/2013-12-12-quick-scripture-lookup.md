---
title: "Quick Scripture Lookup"
date: "2013-12-12"
layout: layouts/post.njk
---

Usually when I'm doing Bible study, but reading through material that's not the
actual Bible, I encounter lots of Scripture references that I want to take note
of and look up for reading later. I made this process a little easier with a
series of Drafts actions and Pythonista scripts.

## The User Experience

Launch [Drafts](http://agiletortoise.com/drafts/), and type in your bible
passage:

`2 Timothy 1:6-7`

Fire off an action to [Pythonista](http://omz-software.com/pythonista/). The
Pythonista script will package up the passage query into a ESV API web service
call. This call comes back with
[the Bible passage in plaintext.](http://www.esvapi.org/v2/rest/passageQuery?key=IP&passage=Gen+1&include-headings=false&output-format=plain-text) Call
back into Drafts, passing along that output, and fire off a final action, which
appends the result to a text file in Dropbox. Now you've got the Bible passage
for reference almost instantly after writing it down:

```text
###### 2013-12-12-10-22-22

2 Timothy 1:6-7 : For this reason I remind you to fan into flame the gift of
God, which is in you through the laying on of my hands, for God gave us a spirit
not of fear but of power and love and self-control.
```

Details and scripts forthcoming...
