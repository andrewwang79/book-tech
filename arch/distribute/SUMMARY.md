# 分布式

## 功能
### 负载均衡
* Nginx核心原理解析
反向代理/负载均衡/动静分离
* LVS+Keepalived+Nginx实现高可用集群

### 缓存
* Redis核心原理解析：持久化机制/主从架构模式/主从复制/无磁盘化复制/哨兵机制/集群/雪崩
* 缓存雪崩的解决方案
* 缓存穿透的解决方案

### 搜索
* ES架构与原理解析
* 集成ES集群故障  节点宕机 / 脑裂问题
* ES深度分页下带来的性能问题分析与解决
* 大数据量下该如何使用scroll滚动技术进行搜索

### 消息队列
* kafka核心原理解析
* kafka高可用
* kafka如何保证消息消费的幂等性(redis bitmap)
* kafka如何保证消息的可靠性传输(回调控制)
* kafka如何保证消息的顺序性

### 分布式锁
* 基于Redis的setnx实现分布式锁
* 基于Redisson实现分布式锁
* 基于ZooKeeper的瞬时节点实现分布式锁
* 基于ZK的Curator客户端实现分布式锁

### 读写分离，分库分表
* shardingsphere
* MyCAT

### 分布式全局id
* SnowFlake算法
* UUID

### 日志收集
* 应用输出json格式日志
* 日志收集器filebeat
* 日志缓冲kafka
* 日志转换器logstash(从kafka读数据，输出到es)
* 日志存储 es
* 日志展示 kibana

### 分布式存储
* ceph

### 分布式文件系统
* FastDFS

### 拓缩容
* Kubernetes

## 知识
### 接口幂等性
* 接口的幂等性实际上就是接口可重复调用，在调用方多次调用的情况下，接口最终得到的结果是一致的
* insert操作 唯一索引/token机制(提交的数据包含随机token)
* delete操作通过唯一索引(删除之前，先查询是否存在)
* update操作通过乐观锁(version字段控制)
* select操作无需考虑
