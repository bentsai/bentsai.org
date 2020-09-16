---
title: "Keyboard hacks in macOS Sierra"
date: "2016-10-24"
layout: layouts/post.njk
---

I upgraded to macOS Sierra today on my work laptop. I hit a few minor niggles
related to some keyboard hacks I had in place. The first was working around the
fact that [Karabiner](https://pqrs.org/osx/karabiner/) no longer works in
Sierra, which is well
[documented by Brett Terpstra](http://brettterpstra.com/2016/09/29/a-better-hyper-key-hack-for-sierra/)
here. I don't rely too much on the "Hyper" key, so actually the main thing I
cared about was remapping Caps Lock to Escape. This, by the way, has been a
game-changer.

I uninstalled Karabiner and [Seil](https://pqrs.org/osx/karabiner/seil.html.en),
which I had previously installed to accomplish my hacks (although I was never
clear what Seil was for).

The second issue was related. I type on
a [Das Keyboard Model S Ultimate](http://shop.daskeyboard.com/collections/products/products/das-keyboard-ultimate-model-s).
Before the upgrade, I swapped the option and command keys because it is natively
a PC keyboard. This stopped working in Sierra. Despite setting the modifier keys
to be swapped, the behavior did not change. So, I used
[Karabiner-Elements](https://github.com/tekezo/Karabiner-Elements) to accomplish
the swap:

![Karabiner-Elements Preferences dialog](../../img/karabiner-elements-preferences.png)
