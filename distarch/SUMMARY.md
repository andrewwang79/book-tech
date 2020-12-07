# 分布式系统

## 架构图
![](/s/distarch/arch.jpg)

## 构成

| 类型 | 功能 | 组件 |
| - | - | - |
| 基础层-网络 | 网络负载均衡 | Nginx |
| 基础层-网络通讯 | [RPC](./rpc) | gRPC |
| 基础层 | 服务编排 | Kubernetes |
| 资源层-数据 | 缓存 | Redis |
| 资源层-数据 | 结构化数据库 | MySQL |
| 资源层-数据 | 非结构化数据库 | MongoDB |
| 资源层-文件 | 文件系统 | FastDFS, CEPH |
| 服务层 | 锁 | Redis |
| 服务层 | 消息队列 | Kafka |
| 服务层 | 搜索 | ES |
| 服务层 | 日志 | ELK |
| 服务层 | 全局ID |  |
| 框架层 | [服务治理](sg/) | Spring Cloud |
| 框架层-sidecar | 权限，审计日志，字典等 |  |

## 知识
### 接口幂等性
* 接口可重复调用，在调用方多次调用的情况下，接口最终得到的结果是一致的

| 操作 | 实现 |
| - | - |
| insert | 唯一索引 |
| delete | 唯一索引(删除之前，先查询是否存在) |
| update | 乐观锁(version字段控制) |
| select | 无 |

### 布隆过滤器

### MongoDB
分片，副本集

## 架构技术
* https://mp.weixin.qq.com/s/VpQvqRc8UxZLs5L3iyJoQQ。简单，适用，演化的原则
* https://www.heguang-tech.com/blog/2020/architect/architect-or-framework/
* https://doocs.github.io/advanced-java
* http://class.imooc.com/sale/javaarchitect
* https://www.rainbond.com/docs/quick-start/rainbond_overview/
* [CAP定理](http://www.ruanyifeng.com/blog/2018/07/cap.html)
* [服务下的数据一致性的几种实现方式之概述](https://www.jianshu.com/p/b264a196b177)

* 配置，事务，缓存
* [Paxos算法简易理解](https://www.zybuluo.com/heavysheep/note/620169)

### 3个技术点
技术点：服务聚合拆分、事务、查询
* http://blog.didispace.com/microservice-three-problem-1/
* http://blog.didispace.com/microservice-three-problem-2/
* https://www.heguang-tech.com/blog/2020/architect/how-to-design-micro-service/：事件源（Event sourcing），命令查询责任分离（CQRS）
