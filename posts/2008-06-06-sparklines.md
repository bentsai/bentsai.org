---
title: "Sparklines"
date: "2008-06-06"
layout: layouts/post.njk
---

My friend [Erik](http://carbonbox.com) sent me some biostatistical data
![](images/erik_smooth2.png) that he has been tracking over past few weeks. I
decided to see what it would look like as a
[sparkline](http://www.edwardtufte.com/bboard/q-and-a-fetch-msg?msg_id=0001OR).
There are a bunch of libraries and web services to generate these things, and I
tried to find the simplest one implemented in Python. I found
[Matthew Perry's module](http://www.perrygeo.net/wordpress/?p=64), installed
[PIL](http://www.pythonware.com/products/pil/), and I was good to go. (I made a
slight change to spark.py to expose the background color of the image as a
parameter so the graphic would match my current theme.)

More data to visualize: I've been recording my gas mileage information
![](images/mile_smooth2.png) since November, 2006. We can also note that gas
prices ![](images/gas_smooth2.png) have been steadily climbing since then (low:
$2.10, high: $4.26). The simplicity and attractiveness of these graphics make
them particularly compelling. I can think of a few places where using sparklines
would be useful...
