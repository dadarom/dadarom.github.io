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



[Lei]:    http://dadarom.github.io  "Lei"
