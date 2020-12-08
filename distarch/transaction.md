# 事务
## 定义
订机票的例子来说明：
```
1、原子操作：你付了钱，航空公司也出了票，这两件事必须同时完成，这就是一个原子操作。
2、不一致：付了钱但没出票，或者没花钱却出了票，就是数据不一致。
3、最终一致：付了钱，票没出，但两天后钱退到了你的账户，这就是最终一致。退钱的过程，就叫做业务补偿。
```

## 微服务开发过程中的挑战
* [3个难题(拆分、事务、查询](https://www.heguang-tech.com/blog/2020/architect/how-to-design-micro-service/)
### 原有的分布式事务无法在微服务下使用
1. 原因
  * 业务侵入，无法用于微服务
  * 数据库需支持2PC
  * 复杂业务回滚的开发成本高
1. 解决方案
  1. TCC(强一致性，消费者会回滚)
  1. 消息(最终一致性，消费者不会回滚。微服务内部是强一致性)
    1. 事务消息：类似本地事务
    1. 事件驱动
### 联表查询
1. 解决方案
  1. CQRS

## 事件驱动架构
* 核心要点是可靠的事件投递和避免事件的重复消费。有两种事件发布的实现：
  * 本地事务
  * 事件源
* 缺点
  * 编程模式比传统基于事务的交易模式更加复杂
  * 必须实现补偿事务以便从应用程序级故障中恢复，例如，如果信用检查不成功则必须取消订单
  * 应用必须应对不一致的数据，比如当应用读取未更新的最终视图时也会遇见数据不一致问题。
  * 订阅者必须检测和忽略冗余事件，避免事件重复消费。
#### 本地事务
![](http://img.mp.itc.cn/upload/20170320/216e5dbc264d4b8a8e3a1019adf5208b_th.jpeg)
* 业务方需要写event表
#### 事件源(Event sourcing)
![](http://img.mp.itc.cn/upload/20170320/af48b6c7bac64cda98df6bd2c772eb09.png)
* 持久化事件，而不是对象
  * 传统方式中，每个订单映射为ORDER表中一行。
  * 事件源方式中，订单以事件状态改变方式存储一个订单。
* 数据查询时，必须使用CQRS来完成查询业务

#### 命令查询责任分离(CQRS)
![](http://img.mp.itc.cn/upload/20170320/79a102e691434963bf8f00c824e7c693_th.jpeg)

## 事务资料
* [微服务下的数据一致性的几种实现方式之概述](https://www.jianshu.com/p/b264a196b177)

### 本地事务

### 分布式事务
#### 两阶段提交(2PC)
![](https://images0.cnblogs.com/blog2015/522490/201508/091642197846523.png)
* 两阶段提交协议（Two-phase Commit）：典型的是XA，有个事务协调器
  1. 协调器告诉大家都准备好提交，大家回复都准备好了。
  1. 协调器告诉大家一起提交，大家都提交了。
#### 三阶段提交(3PC)

### 微服务的数据一致性
* 事件通知型：可靠事件通知模式，最大努力通知模式
  * 可靠事件通知：1. 事件的正确发送； 2. 事件的重复消费。
* 补偿型：TCC模式，业务补偿模式
* 常用的是可靠事件通知模式

#### TCC
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

#### 业务补偿
先处理业务，然后定时或者回调里检查状态是不是一致的，如果不一致采用某个策略，强制状态到某个结束状态（一般是失败状态）。典型的就是冲正操作。

### 事务消息
![](https://user-gold-cdn.xitu.io/2020/3/30/17128badd2b89469?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)
* https://juejin.cn/post/6844904106532962311

### 事务模型
* Actor模型：是强隔离性且弱一致性，在并发中有良好的性能，且易于控制和管理。涉及到多个Actor的事务，无法保证原子性操作。
* 传统模型(STM)：是强一致性弱隔离性的。比如悲观锁/同步的方式，其实就是使用强一致性的方式控制并发。
* [Actor模型介绍](https://www.cnblogs.com/listenfwind/p/9963489.html)

## 资料
### 方案
* [聊聊分布式事务&分布式系统事务一致性解决方案](http://blog.csdn.net/gaowenhui2008/article/details/53910341)
* [阿里的GTS](http://tech.huanqiu.com/news/2017-04/10451235.html)
* [如何用消息系统避免分布式事务](http://www.cnblogs.com/LBSer/p/4715395.html)
* [微服务架构下的分布式数据管理 ](https://www.sohu.com/a/129437612_468741)
* springboot多库分布式事务管理（atomikos）:https://blog.csdn.net/WI_232995/article/details/78124885, https://my.oschina.net/bianxin/blog/1610100

### CAP
[CAP定理](http://www.ruanyifeng.com/blog/2018/07/cap.html)
  * 一致性(C onsistency), 可用性(A vailability), 分区容忍性(P artition tolerance)
  * 3选2，一般用最终一致性

### ACID
事务的：一致性（Consistency），而原子性（Atomicity）、隔离性（Isolation）、持久性（Durability）

### BASE
* CAP理论的延伸，核心思想是即使无法做到强一致性，应用采用合适的方式达到最终一致性。
* BASE是指基本可用（Basically Available）、软状态（ Soft State）、最终一致性（ Eventual Consistency）
