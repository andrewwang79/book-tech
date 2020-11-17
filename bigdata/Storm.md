# Storm

## 介绍
1. 由java和clojure写成

## 原理
1. 实时计算的图状结构为拓扑（topology）。
1. 这个拓扑将会被提交给集群，由集群中的主控节点（Nimbus后台程序）分发代码，将任务分配给工作节点（worker node）Supervisor执行。Nimbus类似Hadoop里面的JobTracker。Nimbus负责在集群里面分发代码，分配计算任务给机器，并且监控状态。
1. 一个拓扑中包括spout和bolt两种角色
  * spout发送消息，负责将数据流以tuple元组的形式发送出去。tuple是不可变数组，对应着固定的键值对。
  * bolt负责转换这些数据流，在bolt中可以完成计算、过滤等操作，bolt自身也可以随机将数据发送给其他bolt。

![](http://img.ptcms.csdn.net/article/201503/09/54fcc9176d069.jpg)

## 资料
* [官网](http://storm.apache.org/)
* [Storm概念学习系列之storm的设计思想](https://www.cnblogs.com/zlslch/p/5989248.html)
* [使用Storm实现实时大数据分析](http://www.178linux.com/2657)
* [Storm实时大数据处理（二）Java实例](http://blog.csdn.net/tendency_yang/article/details/52350852)
