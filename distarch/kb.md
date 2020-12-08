# 知识
* [互联网 Java 工程师进阶知识完全扫盲](https://doocs.github.io/advanced-java)
* [Paxos算法简易理解](https://www.zybuluo.com/heavysheep/note/620169)
* [CAP定理](http://www.ruanyifeng.com/blog/2018/07/cap.html)
  * 一致性(C onsistency), 可用性(A vailability), 分区容忍性(P artition tolerance)
  * 3选2，一般用最终一致性

## ACID
事务的：一致性（Consistency），而原子性（Atomicity）、隔离性（Isolation）、持久性（Durability）

## 2PC
* 两阶段提交
* 数据库类型需要保持一致

## STM
* 软件事务内存(Software Transactional Memory)
* [事务内存（Transactional Memory）](https://zhuanlan.zhihu.com/p/151425608)

## 事务模型
* Actor模型：是强隔离性且弱一致性，在并发中有良好的性能，且易于控制和管理。涉及到多个Actor的事务，无法保证原子性操作。
* 传统模型(STM)：是强一致性弱隔离性的。比如悲观锁/同步的方式，其实就是使用强一致性的方式控制并发。
* [Actor模型介绍](https://www.cnblogs.com/listenfwind/p/9963489.html)

## CAS
* CompareAndSwap，比较并替换。解决原子操作问题
* 需要3个操作数：内存地址V，旧的预期值A，即将要更新的目标值B。CAS指令执行时，当且仅当内存地址V的值与预期值A相等时，将内存地址V的值修改为B，否则就什么都不做。整个比较并替换的操作是一个原子操作。
* CAS仍然存在三大问题：
  * 循环时间长开销很大。
  * 只能保证一个共享变量的原子操作。
  * ABA问题。Java并发包提供了一个带有标记的原子引用类“AtomicStampedReference”，通过控制变量值的版本来保证CAS的正确性。

## 接口幂等性
* 接口可重复调用，在调用方多次调用的情况下，接口最终得到的结果是一致的

| 操作 | 实现 |
| - | - |
| insert | 唯一索引 |
| delete | 唯一索引(删除之前，先查询是否存在) |
| update | 乐观锁(version字段控制) |
| select | 无 |

## 布隆过滤器

## MongoDB
分片，副本集
