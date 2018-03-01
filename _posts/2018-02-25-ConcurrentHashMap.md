---
layout:     post
title:      浅谈ConcurrentHashMap
subtitle:   
date:       2018-02-25
author:     rockybobo
header-img: img/myname/post_20170212_01.jpg
catalog: true
tags:
    - 技术
---

## 浅谈ConcurrentHashMap

 #### ConcurrentHashMap的原理

~~~
1.比于Hashtable以及Collections.synchronizedMap()，ConcurrentHashMap在线程安全的基础上提供了更好的写并发能力，但同时降低了对读一致性的要求;
2.ConcurrentHashMap的设计与实现非常精巧，大量的利用了volatile，final，CAS等lock-free技术来减少锁竞争对于性能的影响，无论对于Java并发编程的学习还是Java内存模型的理解，ConcurrentHashMap的设计以及源码都值得非常仔细的阅读与揣摩。
~~~

#### Jdk1.6&1.7与Jdk1.8的区别

~~~

~~~

#### CAS原理介绍

~~~

~~~

#### 其他

~~~

~~~

#### 参考

