---
title: "Mnemonics for shift and unshift Javascript array methods"
date: 2019-08-22T10:38:56+03:00
tags: ["javascript", "mnemonics"]
---

I've always had trouble distinguishing between the `shift` and `unshift` Javascript array methods. I know that one adds elements to the beginning of an array, and the other removes an element, also from the beginning. But which one does what? It seems that I am not the only one [who](https://stackoverflow.com/questions/19107752/javascript-shift-unshift-mnemonics) is [confused](https://www.reddit.com/r/javascript/comments/86tniv/cant_keep_arrayshift_vs_arrayunshift_straight_nsfw/). The `push` and `pop` methods are just obvious to me.

I got inspired by a tutorial from the [Execute Program](https://www.executeprogram.com/). Here is their take on this:

> `shift` and `unshift` have somewhat confusing names. Here is one way to remember them. `shift` "shifts" all of the elements down by one. Index 2 becomes index 1; index 1 becomes index 0; etc. `unshift` does the opposite.

It is very clever to think about these methods in terms of the changes in existing elements' indices. But it didn't completely click with me. How can I remember that `shift` decrements the indices and `unshift` increments them?

For this, I chose to think of `unshift` as [upshift](https://en.wiktionary.org/wiki/upshift) (a shift to a higher gear).

Now it becomes clear that `unshift` (aka *upshift*) (adding elements to the beginning) will "shift" the existing array element's indices **up**, but `shift` (removing an element from the beginning) - **down**.

*Update:* It occurred to me that you can also think of the "shift" of array's length instead of element indices. 👍
