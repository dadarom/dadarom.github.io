---
layout: post
title: Hadoop Open-Source Reading
description: source code reading 
categories: open-source hadoop
---

## Common

### auth

`filter` `handler` `token`

### conf

`Configured` `ConfServlet` 

`ReconfigurableBase` `ReconfigurationServlet`
 
## Hdfs

## MapReduce 

## YARN



example`SSH Keys`example

```
example`SSH Keys`example  
```

初步分析，在[GitHub]上搭建博客，实质是：将自己的博客内容上传到GitHub上*（因为GitHub提供了空间）；*总结一下，对应3个必要步骤：

1. GitHub上创建工程、并且能够将GitHub上的文件/代码，下载到本地；
2. 将本地的文件/代码，上传到GitHub上；
3. 配置GitHub，使其对外提供私人博客的访问页面；


\* \\

*single asterisk*  
**double asterisk** 

***double asterisk***


_single underscore_

__double underscore__


Heading 1
=========

Heading 2
---------

详细阅读"__3.2如何搭建博客__"中提到的

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a 
> 1 

> 2


~~~
/*
If you have sufficient control over the publishing process
(e.g. you are running Jekyll yourself), an easy solution is
to switch the markdown parser to one that supports TeX.
*/

//For example, using kramdown:
gem install kramdown

//Change the markdown line in _config.yml to
markdown: kramdown

//and add something like
<script type="text/javascript" 
src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
//to _layouts/default.html. 

//Now you can simply mark any mathematics in your posts with $$
~~~

* [CSDN]
* [安装使用Git（GitHub上传、下载文件的工具）](https://help.github.com/articles/set-up-git)

![git-github](/images/side-background.jpg)


[Lei]:    http://dadarom.github.io  "Lei"
[CSDN]: www.csdn.net
