---
title: "Day One Templates Using Launch Center Pro"
date: "2014-02-26"
layout: layouts/post.njk
---

Update (2014-07-07): [Coffee Post Followup](http://bentsai.wordpress.com/2014/03/12/coffee-log-followup/)

[Day One](http://dayoneapp.com) is a great system for journaling and note-taking. One of things [I use it for](http://dayoneapp.com/guide/uses/) is to keep track of the different coffees I buy and brew. Since this is something I track regularly, I've developed a method to pre-populate a Day One entry with a standard structure for my coffee journal. Here's what it looks like:

[![Coffee Log](http://bentsai.files.wordpress.com/2014/02/photo-feb-26-11-26-24-am.png?w=169)](http://bentsai.files.wordpress.com/2014/02/photo-feb-26-11-26-24-am.png)

## Day One Templates

Using an action to launch Day One with some pre-populated text, combined with prompts and the new list prompts, makes for an easy way to enter some structured content in your journal. Let me explain. The structure for the entry is stored in a [Launch Center Pro action](http://launchcenterpro.com/tjfjnd). Here's what that looks like:

`dayone://post?entry=%23coffee%20%23log%0A%0A%7CCoffee%7C%7C%0A%7C%3A---%7C%3A---%7C%0A%7COrigin/Name%7C[prompt:Origin/Name]%7C%0A%7CBrew%20method%7C[list:Brew Method|AeroPress|Chemex|Drip|Espresso|French Press|Pour Over|Other]%7C%0A%7CBrewer%7C[prompt:Who brewed it?]%7C%0A%7CRating%7C[list:Rating|★☆☆|★★☆|★★★]%7C%0A%7CNotes%7C[prompt:Notes]%7C`

Each field in the table is a prompt, so when I'm ready to log my coffee, I launch this action, answer brief survey, and voila!

[![](images/photo-feb-26-11-38-17-am.png)![](images/photo-feb-26-11-38-33-am.png)![](images/photo-feb-26-11-38-37-am.png)![](images/photo-feb-26-11-38-48-am.png)![](images/photo-feb-26-11-38-57-am.png)![Raw Markup](http://bentsai.files.wordpress.com/2014/02/photo-feb-26-11-38-57-am.png?w=169)](http://bentsai.files.wordpress.com/2014/02/photo-feb-26-11-38-11-am.png)

You'll notice for the brew method and rating, I've used a list prompt. This works well since the answers come from a limited set. And the final frame shows the raw markup, which renders as a tidy table in Day One. This concept can be applied for any type of entry you're creating on a regular basis that has a defined structure. The new Launch Center Pro prompts afford a nice front-end for text input. You can extend this idea for other notes you want to put into your journal, using Launch Center Pro as the mechanism for polling and input. For example, I have another action which is scheduled to launch every evening that asks me what I had for each meal of the day.
