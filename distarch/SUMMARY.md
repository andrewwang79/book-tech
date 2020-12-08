# 分布式系统架构

## 架构图
![](../s/distarch/arch.jpg)

## 构成

| 类型 | 功能 | 组件 |
| - | - | - |
| 规范-通讯协议 | [RPC](distarch/rpc) | gRPC |
| 基础层 | 服务编排 | Kubernetes |
| 资源层-数据 | 缓存 | Redis |
| 资源层-数据 | 结构化数据库 | MySQL |
| 资源层-数据 | 非结构化数据库 | MongoDB |
| 资源层-文件 | 文件系统 | FastDFS, CEPH |
| 服务层 | 网络负载均衡 | Nginx |
| 服务层 | [锁](distarch/locker) | Redis |
| 服务层 | 消息队列 | Kafka |
| 服务层 | 搜索 | ES |
| 服务层 | 日志 | ELK |
| 服务层 | [全局ID](distarch/globalid) |  |
| 框架层 | [服务治理](distarch/sg/SUMMARY) | Spring Cloud |
| 框架层-sidecar | 权限，审计日志，字典等 |  |

## 资料
* [漫谈何时从单体架构迁移到微服务？](https://mp.weixin.qq.com/s/VpQvqRc8UxZLs5L3iyJoQQ)
* [多研究些架构，少谈些框架](https://www.heguang-tech.com/blog/2020/architect/architect-or-framework/)
* [imooc公开课](http://class.imooc.com/sale/javaarchitect)
* [阿里云公开课](https://edu.aliyun.com/roadmap/microservice)
