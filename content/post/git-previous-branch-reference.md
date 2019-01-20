---
title: "Previous branch reference in Git"
date: 2019-01-27T13:45:06+03:00
tags: ["git"]
draft: false
---
Today I want to share a trick I borrowed from someone on Twitch. They started to commit something using Git, and after that used the following command: `git checkout -`. It became obvious what it does (it resembles `cd -` very much), but I was surprised to find out about it just now after years of using Git.

Switching back and forth between branches is very common in Git branching workflows, and is generally performed using the `git checkout <branchname>` command. But the `-` shorthand helps you speed up this process and it also [saves you a lot of keystrokes](https://www.youtube.com/watch?v=D_KtIHEGrmc) 👌.

The shorthand is actually is a synonym of the so-called "previous checkout syntax". Here is [an excerpt](https://git-scm.com/docs/git-checkout#git-checkout-ltbranchgt) from Git docs:

> You can use the `"@{-N}"` syntax to refer to the N-th last branch/commit checked out using "git checkout" operation. You may also specify `-` which is synonymous to `"@{-1}"`.

Another great thing is that the `-` shorthand can be used with the `rebase` and `merge` git commands, but not when deleting a branch (although `git branch -d @{-1}` works just fine).
