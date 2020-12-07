# Kafka
## QA
* 高可用
* 消息消费的幂等性(redis bitmap)
* 消息的可靠性传输(回调控制)
* 消息的顺序性

## 介绍
* 是一个分布式、支持分区的（partition）、多副本的（replica），基于zookeeper协调的分布式消息系统。用scala语言编写
* 以时间复杂度为O(1)的方式提供消息持久化能力
* 大数据场景
  1. 基于hadoop的批处理系统
  1. 低延迟的实时系统：storm/Spark流式处理引擎
  1. web/nginx日志、访问日志
* 特性
  1. 高吞吐量、低延迟：kafka每秒可以处理几十万条消息，它的延迟最低只有几毫秒，每个topic可以分多个partition, consumer group 对partition进行consume操作。
  1. 可扩展性：kafka集群支持热扩展
  1. 持久性、可靠性：消息被持久化到本地磁盘，并且支持数据备份防止数据丢失
  1. 容错性：允许集群中节点失败（若副本数量为n,则允许n-1个节点失败）
  1. 高并发：支持数千个客户端同时读写

## 设计重点
1. 磁盘持久化数据：顺序读写，零拷贝([zero copy](Kafka持久化方案))
1. 数据失效机制：过期时间或者最大容量
1. 基于Partition的Replication，Partition的索引是稀疏矩阵存储
1. leader机制

### leader机制
Kafka动态维护了1个leader和一个同步状态的副本集合（in-sync replicas），简称ISR，在这个集合中的节点都是和leader保持高度一致的，任何一条消息必须被这个集合中的每个节点读取并追加到日志中了，才回通知外部这个消息已经被提交了。因此这个集合中的任何一个节点随时都可以被选为leader.ISR在ZooKeeper中维护。ISR中有f+1个节点，就可以允许在f个节点down掉的情况下不会丢失消息并正常提供服。ISR的成员是动态的，如果一个节点被淘汰了，当它重新达到“同步中”的状态时，他可以重新加入ISR.这种leader的选择方式是非常快速的，适合kafka的应用场景。
当所有的ISR都down掉时，必须及时作出反应。可以有以下两种选择:
1. 等待ISR中的任何一个节点恢复并担任leader。
1. 选择所有节点中（不只是ISR）第一个恢复的节点作为leader.

这是一个在可用性和连续性之间的权衡。如果等待ISR中的节点恢复，一旦ISR中的节点起不起来，那集群就永远恢复不了。如果等待ISR外的节点恢复，这个节点的数据就会被作为线上数据，有可能和真实的数据有所出入，因为有些数据它可能还没同步到。
这种窘境不只Kafka会遇到，几乎所有的分布式数据系统都会遇到。

## 资料
* [各消息队列对比](http://blog.csdn.net/oanqoanq/article/details/51190358)
* [kafka的分布式原理解读](http://blog.csdn.net/gaoying_blogs/article/details/51744951)
* [Kafka的内部机制深入(持久化，分布式，通讯协议)](http://blog.csdn.net/u012961566/article/details/76736471)
* [为什么kafka使用磁盘而不是内存](http://blog.csdn.net/endlu/article/details/51392905)
* [kafka深入理解](http://blog.csdn.net/jifei12/article/details/51490679)：为何使用MQ
* [kafka leader选举机制原理](http://blog.csdn.net/yanshu2012/article/details/54894629)
* [Kafka史上最详细原理总结](http://blog.csdn.net/u013573133/article/details/48142677)
* [Kafka 几个重要的配置总结](http://blog.csdn.net/huanggang028/article/details/47830529)
* 消息协议
  * MQ常用协议：https://reedf.gitbooks.io/mq/content/mqyuan_li/mqchang_yong_xie_yi.html
  * Stomp协议：https://www.jianshu.com/p/db21502518b9
  * MQTT协议中文版：https://mcxiaoke.gitbooks.io/mqtt-cn/content/
  * XMPP：聊天软件为主
