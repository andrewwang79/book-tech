# 事务
## 定义
订机票的例子来说明：
```
1、原子操作：你付了钱，航空公司也出了票，这两件事必须同时完成，这就是一个原子操作。
2、不一致：付了钱但没出票，或者没花钱却出了票，就是数据不一致。
3、最终一致：付了钱，票没出，但两天后钱退到了你的账户，这就是最终一致。退钱的过程，就叫做业务补偿。
```

## 技术知识
### 数据一致性方案
| 数据一致性 | 技术 |
| :-: | - |
| 强一致性 | 分布式事务+RPC |
| 最终一致性 | 可靠事件模式 |

数据一致性的技术模式

| 类型 | 模式 | 说明 |
| :-: | - | - |
| 事件 | 可靠事件 | 常用模式，一般用MQ。异步，消费者不会回滚 |
| 事件 | 最大努力 |  |
| 事务 | TCC等 | 同步，消费者可回滚 |
| 事务 | 业务补偿 | 同步 |

### 最终一致性的2种场景
| 场景 | 实例 |
| :-: | - |
| 操作时间长，不能影响主业务的事务性 | 同服务的业务，比如处理头像 |
| 功能后加，无法提前知道，只能订阅 | 跨服务的业务，比如log服务 |

### 技术方案
| 方案 | 机制 | 场景 | 说明 |
| :-: | - | - | - |
| 2PC | XA规范，数据库锁 |  |  |
| 3PC | XA规范，数据库锁 |  |  |
| [AT](http://seata.io/zh-cn/docs/dev/mode/at-mode.html) | 业务锁 |  | 业务无侵入 |
| TCC | 业务锁 | 高并发的重要业务 | 代码侵入性强 |
| Saga | 无锁 | 高并发的业务 | 无法保证隔离性（脏写） |
| 可靠事件 | 无锁 |  |  |

## 本地事务

## 分布式事务

### 两阶段提交(2PC)
![](https://images0.cnblogs.com/blog2015/522490/201508/091642197846523.png)
* 两阶段提交协议（Two-phase Commit）：典型的是XA，有个事务协调器
  1. 协调器告诉大家都准备好提交，大家回复都准备好了。
  1. 协调器告诉大家一起提交，大家都提交了。

### 三阶段提交(3PC)
* 3PC把2PC的准备阶段再次一分为二，这样三阶段提交就有CanCommit、PreCommit、DoCommit三个阶段。

### AT
和2PC的区别
1. 从数据库锁到业务锁
1. 2PC的锁到第二阶段，AT的锁到第一阶段

### TCC
![](https://static001.geekbang.org/infoq/e3/e37f11e97dd228997257ee1d3c9ee608.webp?x-oss-process=image/resize,p_80/format,jpg)
* http://www.tianshouzhi.com/api/tutorials/distributed_transaction/388
* Try Confirm Cancel。Confirm 与 Cancel 互斥
1. Try阶段：尝试执行业务
  1. 完成所有业务检查( 一致性 )
  1. 预留必须的业务资源( 准隔离性 )
1. Confirm / Cancel 阶段：
  1. Confirm ：确认执行业务
    1. 真正执行业务
    1. 不做任务业务检查
    1. Confirm 操作满足幂等性
  1. Cancel ：取消执行业务
    1. 释放 Try 阶段预留的业务资源
    1. Cancel 操作满足幂等性

## 业务补偿(Saga)
先处理业务，然后定时或者回调里检查状态是不是一致的，如果不一致采用某个策略，强制状态到某个结束状态（一般是失败状态）。典型的就是冲正操作。

## 可靠事件
* ![](http://img.mp.itc.cn/upload/20170320/216e5dbc264d4b8a8e3a1019adf5208b_th.jpeg)
* [事务消息](https://juejin.cn/post/6844904106532962311)
* ![](https://user-gold-cdn.xitu.io/2020/3/30/17128badd2b89469?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
### 设计
| 方式 | 说明 |
| :-: | - |
| [DB](https://www.jianshu.com/p/8de3b3bba4e8) | 可确保，和业务数据一起事务insert。即使业务时MQ无效。 |
| MQ | 无法确保。确保方案是MQ不通时业务也失败 |
| [服务](https://segmentfault.com/a/1190000022857277) | 无法确保。确保方案是服务不通时业务也失败 |

结论：可用DB或服务。但从可用性和性能来说，DB更合适
### DB流程
业务方需要同时写入event表
```
保存DB
发送到MQ
ACK后删除DB
如无ACK，则重试
补偿机制确保所有消息执行，重试次数等
```

## 资料
### 方案
* [微服务下的数据一致性的几种实现方式之概述](https://www.jianshu.com/p/b264a196b177)
* [聊聊分布式事务&分布式系统事务一致性解决方案](http://blog.csdn.net/gaowenhui2008/article/details/53910341)
* [阿里的GTS](http://tech.huanqiu.com/news/2017-04/10451235.html)
* [如何用消息系统避免分布式事务](http://www.cnblogs.com/LBSer/p/4715395.html)
* [微服务架构下的分布式数据管理 ](https://www.sohu.com/a/129437612_468741)
* springboot多库分布式事务管理（atomikos）:https://blog.csdn.net/WI_232995/article/details/78124885, https://my.oschina.net/bianxin/blog/1610100
* 分布式事务现有框架: http://seata.io/zh-cn/docs/overview/what-is-seata.html, https://www.codingapi.com/docs/txlcn-preface/

### 事务四大特性ACID
一致性（Consistency），而原子性（Atomicity）、隔离性（Isolation）、持久性（Durability）

### 事务模型
* Actor模型：是强隔离性且弱一致性，在并发中有良好的性能，且易于控制和管理。涉及到多个Actor的事务，无法保证原子性操作。
* 传统模型(STM)：是强一致性弱隔离性的。比如悲观锁/同步的方式，其实就是使用强一致性的方式控制并发。
* [Actor模型介绍](https://www.cnblogs.com/listenfwind/p/9963489.html)

### CAP，强一致性
[CAP定理](http://www.ruanyifeng.com/blog/2018/07/cap.html)
  * 一致性(C onsistency), 可用性(A vailability), 分区容忍性(P artition tolerance)
  * 3选2，一般用最终一致性

### BASE，最终一致性
* CAP理论的延伸
* BASE是指基本可用（Basically Available）、软状态（ Soft State）、最终一致性（ Eventual Consistency）
