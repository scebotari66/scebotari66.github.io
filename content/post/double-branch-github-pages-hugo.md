---
title: "Setup a double branch model for GitHub Pages and Hugo"
date: 2017-10-19T16:03:32+03:00
tags: ["blogging", "hugo", "git"]
draft: false
---

I've mentioned in my ["Hello World"](/post/hello-world/) post that I've followed Roman Coedo's comprehensive [guide](http://rcoedo.com/post/hugo-static-site-generator/) for setting up this website. One key element of the setup described in his article is the two branch model: `master` for the generated content that [will be served](https://help.github.com/articles/user-organization-and-project-pages/) by GitHub Pages, and `source` - for keeping the Hugo source content under version control.

The approach for setting up branches described there is the following:

    $ git clone git@github.com:<username>/<username>.github.io.git
    $ cp -r public/* <username>.github.io/
    $ cd <username>.github.io
    $ git add --all
    $ git commit -m 'First commit'
    $ git push
    $ cd <username>.github.io
    $ git checkout -b source
    $ rm -rf * # Be careful!
    $ cp -r ~/myblog/* .
    $ git add --all
    $ git commit -m 'First source commit'
    $ git push --set-upstream origin source

This gets the job done, but I started thinking about an alternative approach that will get rid of all that *remove-and-copy* action. I came up with a slightly different version that uses the [git worktree](https://git-scm.com/docs/git-worktree) feature. This feature basically allows you to create a branch in a directory other than root.

Here is my *worktree* approach:

    $ echo "<username>.github.io" >> README.md
    $ git reset
    $ git add README.md
    $ git commit -m "Initial commit"
    $ git branch -m master source #1
    $ rm -Rf public/
    $ git worktree add -b master public/ #2
    $ git remote add origin git@github.com:<username>/<username>.github.io.git
    $ git push origin --all
    $ git branch -d master #3
    $ echo "public/" >> .gitignore
    $ git add --all
    $ git commit -m "Ignore the public folder"
    $ git push --set-upstream origin source

The key commands are marked, so you can see that at command `#1` the *master* branch is renamed to *source*; at command `#2` a new *master* branch is created inside the *public/* folder; at command `#3` the local *master* branch is removed, as it will be automatically updated by Travis CI.

Some notes on regarding this approach:

 - you should start with an empty remote repository (do not add a `README` or `.gitignore` file when creating it on GitHub);
 - nothing will be committed to the `master` branch because Travis will eventually do this job.

I'm almost sure there is a better way to do this, but I'm happy with what I did end up.
