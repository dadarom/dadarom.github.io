---
layout: post
title: Git problems
description: collect git problems
categories: git problems
---

##1. Permission denied (publickey).

git push,and then error upside.
`ssh -vT git@github.com`发现是.ssh用的是默认的`~/.ssh`.

[Error: Permission denied (publickey)](https://help.github.com/articles/error-permission-denied-publickey/)

~~~
eval "$(ssh-agent -s)"
ssh-add ~/dadarom/.ssh/id_rsa
~~~

##2 info: the default branch

The default branch is considered the “base” branch in your repository, against which all pull requests and code commits are automatically made, unless you specify a different branch.

[Setting the default branch]:(https://help.github.com/articles/setting-the-default-branch/)

git pages: build master branch,so commit it and trigger its rebuild.


[Lei]:    http://dadarom.github.io  "Lei"
