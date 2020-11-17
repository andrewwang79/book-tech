# NoSql
* [三大NoSQL数据库HBase、Cassandra和MongoDB大比拼](http://m.sohu.com/a/109760616_465914)
* [cassandra简单介绍与基本操作](https://www.cnblogs.com/youzhibing/p/6549960.html)
* [Mongodb cassandra 和 Mysql对比](https://www.cnblogs.com/wangbaojun/p/9724702.html)
* [MongoDB、Cassandra 和 HBase 三种 NoSQL 数据库比较](https://www.cnblogs.com/youjy-mros/p/4917367.html)

# 大数据
* 解决大数据的可靠存储(1台计算机不够存储)和处理(1台计算机无法在要求的时间内完成处理)。
* 数据收集，处理，存储
* 告警和监控是大量接入的前提，可以快速定位和解决问题。

## 产品
* 批处理框架：Apache Hadoop
* 流处理框架：Apache Storm，Apache Samza
* 混合框架：Apache Spark，Apache Flink

| 项 | 计算 | 用途 | 数据集 |
| :----: | ---- | ---- | ---- |
| Hadoop | 离线批量 | 数据挖掘和分析 | 批处理 |
| Storm | 实时单条消息 | 热门话题；金融，股票等 | 流处理 |
| Spark | 准实时(秒级)批量 | 数据挖掘和机器学习等需要迭代的算法 | RDD |

![](http://img.ptcms.csdn.net/article/201503/09/54fcc951a9ca5.jpg)

## 技术
| 项 | 级别 | 说明 |
| :----: | ---- | ---- |
| 批处理(MapReduce) | 低层次抽象 | 类似逻辑门电路中的与门，或门和非门 |
| RDD(Resilient Distributed Dataset) | 高层次抽象 | 类似逻辑电路中的编码器或译码器等 |

### 批处理
MapReduce引擎。MapReduce的处理技术符合使用键值对的map、shuffle、reduce算法要求。基本处理过程包括：
1. 从HDFS文件系统读取数据集
1. 将数据集拆分成小块并分配给所有可用节点
1. 针对每个节点上的数据子集进行计算（计算的中间态结果会重新写入HDFS）
1. 重新分配中间态结果并按照键进行分组
1. 通过对每个节点计算的结果进行汇总和组合对每个键的值进行“Reducing”
1. 将计算而来的最终结果重新写入 HDFS

### 流处理
* 对随时进入系统的数据进行计算，是永久运行的拓扑（topology）。
* 流处理方式无需针对整个数据集执行操作，而是对通过系统传输的每个数据项执行操作。
* 流处理中的数据集是“无边界”的，这就产生了几个重要的影响：
  1. 完整数据集只能代表截至目前已经进入到系统中的数据总量
  1. 工作数据集也许更相关，在特定时间只能代表某个单一数据项。
  1. 处理工作是基于事件的，除非明确停止否则没有“尽头”。处理结果立刻可用，并会随着新数据的抵达继续更新。

### RDD
1. 是一个不可变的带分区的记录集合
1. 提供两类操作，转换和动作。
  * 转换：map,filter,flatMap,sample,groupByKey,reduceByKey,union,join,cogroup,mapValues,sort,partionBy
  * 动作：count,collect,reduce,lookup,save
1. 任何操作都可以像函数式编程中操作内存中的集合一样直观、简便。集合操作的实现是在后台分解成一系列Task发送到几十台上百台服务器组成的集群上完成的。

## 资料
* [美团的大数据平台架构实践](https://zhuanlan.zhihu.com/p/26359613)
* [携程基于Storm的实时大数据平台实践](http://blog.csdn.net/tangdong3415/article/details/52448030)
* [如何创建一个大数据平台？具体的步骤 - 知乎](https://www.zhihu.com/question/37627092?sort=created)
* [Apache数据序列化Avro](https://www.jianshu.com/p/12cf73c19ecf)
* [JSON与AVRO数据文件的相互转换](http://blog.csdn.net/strongyoung88/article/details/54293263)

### 性能
![](https://pic4.zhimg.com/80/v2-691e92dcb3a49e4a32126a3dd7a44f79_hd.jpg)

### 实例
[文章单词数量统计](http://blog.csdn.net/tendency_yang/article/details/52350852)
1. 每个句子分解成单词
1. 计算每个句子的每个单词的数量
1. 合并每个单词的数量

## 资料
* [大数据学习笔记](https://chu888chu888.gitbooks.io/hadoopstudy/content/)

# 数据挖掘
## 资料
- [数据挖掘百科](http://baike.baidu.com/view/7893.htm)
- [数据挖掘十大经典算法](http://blog.csdn.net/aladdina/article/details/4141177)
- [数据挖掘十大算法总结–核心思想，算法优缺点，应用领域](http://blog.csdn.net/iemyxie/article/details/40736773)
[other](http://itindex.net/detail/49268-%E6%95%B0%E6%8D%AE%E6%8C%96%E6%8E%98-%E7%BB%8F%E5%85%B8-%E7%AE%97%E6%B3%95)
- [机器学习](http://www.cnblogs.com/tornadomeet/p/3395593.html)
- [SqlServer数据挖掘教程](http://club.topsage.com/thread-162737-1-1.html)

## 区别
- 数据分析：先决而后知。侧重于解决数据挖掘以外的问题：如描述性统计、交叉报表、假设检验等。
- 数据挖掘：先知而后决。有模型就是挖掘。侧重解决四类问题：分类、聚类、关联、预测

## 参考
http://www.gooseeker.com/cn/node/Fuller/2010041303
http://superlxw1234.iteye.com/blog/1708718
