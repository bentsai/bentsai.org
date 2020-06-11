---
title: "Download a local NuGet repository using Nuget"
date: "2012-07-18"
layout: layouts/post.njk
---

I was setting up a development environment on a remote server today, and due to the security constraints on the machine, I wasn't able to reach the official [NuGet](http://nuget.org/) feed. After some searching, I found the [Nuget.Downloader package](http://nuget.org/packages/Nuget.Downloader), which allows you to download all of NuGet locally!

Because NuGet allows you to specify a local folder as a source, all I had to do was

- run the `Download-Packages -top 100` command (to get the top 100 most popular packages)
- copy the folder up to my server
- point NuGet package manager to that folder
