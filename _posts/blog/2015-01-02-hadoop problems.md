---
layout: post
title: Hadoop problems
description: collect hadoop dev problems
categories: hadoop problems
---

##1. hadoop common compile error##

> 
```
Failed to execute goal org.apache.maven.plugins:maven-antrun-plugin:1.6:run 
(compile-proto) on project hadoop-common: An Ant BuildException has occured: exec returned: 127 -> [Help 1]
```

```
export LD_LIBRARY_PATH=/usr/local/lib
```

#Be attetion to version: hadoop2.0.0 --> protobuf-2.4.0a

[proto buffers error] , [proto buffers install] , [Ubuntu编译Hadoop源码异常总结]



[Lei]:    http://dadarom.github.io  "Lei"

[Ubuntu编译Hadoop源码异常总结]: http://m.oschina.net/blog/356552
[proto buffers error]:http://hadoop-common.472056.n3.nabble.com/failed-to-build-trunk-what-s-wrong-td3660097.html
[proto buffers install]:https://github.com/google/protobuf