---
layout:     post
title:      JVM 分析
subtitle:    "\"技术博客列表\""
date:       2017-02-15
author:     rockybobo
header-img: img/myname/post_20170212_01.jpg
catalog: true
tags:
    - JDK&JVM
---

## JVM分析

#### 实践

1. 对JVM内存快照进行DUMP并分析
2. 分析一下现有环境上的GC日志，查看下GC频率

#### 思考：

1. JVM进程CPU偏高，如何定位问题？
2. 线上机器RT抖动厉害，如何分析原因？
3. JVM发送OOM，如何找到原因？
4. javaagent模式可以做些什么？

#### 操作

1. dump命令

   > jmap -dump:format=b,file=jmap_dump_`date +%Y%m%d%H%M`_`hostname`.hprof `pgrep -u mapp java`

   ​

2. 内存设置

   -Xmx：最大堆大小  4g

   -Xms：初始堆大小 4g

   -Xmn:  年轻代大小  

   设-XX:NewRatio=X，用公式X:1计算                老年代：新生代

   > 如果-XX:NewRatio=3，  则老年代：3g, 新生代1g

   设-XX:SurvivorRatio=X，用公式X:1:1计算       Eden : survivor：survivor

   > 如果-XX:SurvivorRatio=8，则Edean：819.2m,survivor：102.4

3. JVM OOM生成Dump文件

   方法一：

   >  命令：jmap -dump:format=b,file=heap.bin
   >
   >  file：保存路径及文件名
   >
   >  pid：进程编号（windows通过任务管理器查看，linux通过ps aux查看）
   >
   >  dump文件可以通过MemoryAnalyzer(MAT)分析查看,可以查看dump时对象数量，内存占用，线程情况等。

   方法二：

   > 让JVM在遇到OOM(OutOfMemoryError)时生成Dump文件
   >
   > -XX:+HeapDumpOnOutOfMemoryError 
   >
   > -XX:HeapDumpPath=/path/heap/dump

#### jvm分析工具

1. Visual VM

   > http://www.ibm.com/developerworks/cn/java/j-lo-visualvm/
   >
   > 打开命令： jvisualvm



  #### java8之后 

1.  Java8内存模型—永久代(PermGen)和元空间(Metaspace)

   > http://www.cnblogs.com/paddix/p/5309550.html





#### 其他

mac下配置不同的jdk版本

> http://blog.csdn.net/lichangzhen2008/article/details/44959563

#### 各种溢出举例

https://github.com/pzxwhc/MineKnowContainer/issues/25

   

  



