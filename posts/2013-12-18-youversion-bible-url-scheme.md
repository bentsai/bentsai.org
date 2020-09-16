---
title: "YouVersion Bible URL Scheme"
date: "2013-12-18"
layout: layouts/post.njk
---

After some asking and poking around, I finally figured out how to specify a
range using the YouVersion Bible app's URL scheme.

## Open a range of verses

```bash
youversion://bible?reference=PHP.4.4+PHP.4.5+PHP.4.6+PHP.4.7
```

The Bible book names are specified using their
[standard OSIS abbreviations](http://crosswire.org/wiki/OSIS_Book_Abbreviations).

The only tricky part here was that I was expecting the arguments to be the start
and end verses. But, it's actually an enumeration of the verses you want.

And for reference, here are the other available endpoints.

## Open to a specific verse

```bash
youversion://bible?reference=JHN.3.16
```

## Open bookmarks

```bash
youversion://bookmarks
```

## Open reading plans

```bash
youversion://reading_plans
```

Take note that this URL scheme is _undocumented_, meaning it may change with a
future update of the app.
