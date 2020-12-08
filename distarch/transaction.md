# 事务

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

## 3个难题(拆分、事务、查询)
* http://blog.didispace.com/microservice-three-problem-1/
* http://blog.didispace.com/microservice-three-problem-2/
* https://www.heguang-tech.com/blog/2020/architect/how-to-design-micro-service/

### 微服务开发过程中的挑战
* 服务A处理服务B的数据
* 方式：API，分布式事务(2PC)
* 问题：
  1. 2PC需要数据库类型一致
  1. 联表查询

## 资料
* [聊聊分布式事务&分布式系统事务一致性解决方案](http://blog.csdn.net/gaowenhui2008/article/details/53910341)
* [阿里的GTS](http://tech.huanqiu.com/news/2017-04/10451235.html)
* [如何用消息系统避免分布式事务](http://www.cnblogs.com/LBSer/p/4715395.html)
* [！！！！](https://www.sohu.com/a/129437612_468741)
* springboot多库分布式事务管理（atomikos）:https://blog.csdn.net/WI_232995/article/details/78124885, https://my.oschina.net/bianxin/blog/1610100
* [微服务下的数据一致性的几种实现方式之概述](https://www.jianshu.com/p/b264a196b177)
