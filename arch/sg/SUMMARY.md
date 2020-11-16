# 服务治理

## 介绍
* 服务治理基于RPC包含以下治理中间件

| 项 | 作用 | 举例 |
| :-: |  |  |
| 网关 | 外部请求入口 | 外部沟通，如业主要求刷漆 |
| 服务管理 | 服务镜像仓库和服务启停管理 | 装修公司，如提供人员 |
| 注册中心 | 服务实例登记/退出 | 人员管理，如刷漆工到现场后登记 |
| 配置中心 | 配置项统一管理 | 装修信息，如用xx漆 |
| 链路监控 | 请求实例的flow和输入输出 | 操作记录，如某墙面的某次刷漆记录 |
| 流量管控 | 1. 负载均衡<br> 2. 熔断<br> 3. 降级<br> | 1. 刷漆工甲当前工作量较多，后续刷漆请求可以交给工作量少的其他工人<br> 2. 刷漆工都病倒了，业主被告知暂不提供服务。装修公司介入处理<br> 3. 当前刷漆工作量超过刷漆工，为了完成尽可能多的工作，降低刷漆标准(比如播放低分辨率的视频)<br> |

## 服务治理组件
### 网关
* zuul (同步Servlet，多线程阻塞模型)
* spring gateway (基于netty异步io)
* spring gateway性能比zuul更好/支持长连接/长期维护

###  注册中心
* eureka
* zk
* [alibaba/nacos](https://nacos.io/zh-cn/):注册和配置
* 什么是服务治理https://www.jianshu.com/p/dd818114ab4b
* 注册/发现/续约/下线/自保

### 通讯
* feign(http)
* dubbo(rpc)

## 链路追踪
* 客户端采集工具sleuth。 核心原理(traceId,spanId)
* 分布式追踪系统zipkin(可以接入kafka缓冲，es存储)

### 流量管理/限流
* alibaba/Sentinel
* redis限流设计

### 服务容错:熔断，降级
* Hystrix
* Hystrix Dashboard

### 配置中心
* apollo
* 配置中心功能与设计参考apollo作者文章（https://nobodyiam.com/2018/07/29/configuration-center-makes-microservices-smart/）
* 配置即控制

#### 配置需要治理
* 权限控制、审计日志
* 灰度发布、配置回滚
* 不同环境、集群管理

#### 配置中心核心功能
* 功能发布开关
* A/B测试
* QA测试
* 运维开关
* 限流
* 黑白名单
* 动态日志级别
* 动态网关路由
* 动态路由修改

# 资料
* [ZooKeeper 笔记(3) 实战应用之【统一配置管理】](https://www.cnblogs.com/yjmyzz/p/4604947.html)
