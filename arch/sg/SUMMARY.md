# 服务治理

## 微服务
### 改变
1. 部署单元 越来越小的粒度，加快交付效率，同时增加运维的复杂度。
1. 依赖方式从依赖库到依赖服务，增加了开发者选择的自由（语言，框架，库），提高了复用效率，同时增加了治理的复杂度。
1. 架构模式从单体应用到微服务架构，架构设计的关注点从分层转向了服务拆分。

### 成本
1. 组织架构
1. 运维
1. 服务治理

### 使用前提条件
1. 敏捷开发
1. 领域驱动设计(DDD)
1. 团队结构：一个模块一个团队独立做，如订单模块
1. 技术架构
1. **DevOps**
1. 管理工具，如调用链管理

### 3个技术点
技术点：服务聚合拆分、事务、查询
* http://blog.didispace.com/microservice-three-problem-1/
* http://blog.didispace.com/microservice-three-problem-2/
* https://www.heguang-tech.com/blog/2020/architect/how-to-design-micro-service/：事件源（Event sourcing），命令查询责任分离（CQRS）

## 介绍
* 服务治理基于RPC包含以下治理中间件

| 项 | 作用 | 示例 |
| :-: |  |  |
| 网关 | 外部请求入口 | 外部沟通，如业主要求刷漆 |
| 服务管理 | 服务镜像仓库和服务启停管理 | 装修公司，如提供人员 |
| 注册中心 | 服务实例登记/退出 | 人员管理，如刷漆工到现场后登记 |
| 配置中心 | 配置项统一管理 | 装修信息，如用xx漆 |
| 链路监控 | 请求实例的flow和输入输出 | 操作记录，如某墙面的某次刷漆记录 |
| 流量管控 | 1. 负载均衡<br> 2. 熔断<br> 3. 降级<br> | 1. 刷漆工甲当前工作量较多，后续刷漆请求可以交给工作量少的其他工人<br> 2. 刷漆工都病倒了，业主被告知暂不提供服务。装修公司介入处理<br> 3. 当前刷漆工作量超过刷漆工，为了完成尽可能多的工作，降低刷漆标准(比如播放低分辨率的视频)<br> |

* [熔断&降级](https://blog.csdn.net/guwei9111986/article/details/51649240)
| 项 | 触发 | 目的 | 处理方式 |
| :----: | -- | -- | -- |
| 降级 | 压力瞬间剧增 | 降低整体负荷 | 简单/延迟/暂停使用一些不重要/不紧急的服务，释放资源以保证核心交易正常运作或高效运作 |
| 熔断 | 某个下游服务故障 | 防止雪崩效应 | 熔断该节点微服务的调用，快速返回错误的响应信息。当检测到服务调用响应正常后，恢复调用链路 |

![](/s/microservice.png)
说明：绿色虚框是SpringCloud的服务，蓝色虚框是业务方工作

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

## 服务治理系统
* spring boot admin
* 面向开发人员
  * 看服务状态和日志等
  * 服务依赖和调用链。pinpoint
  * 动态路由

# 资料
## 微服务
* [微服务实战（一）：微服务架构的优势与不足](http://dockone.io/article/394)
* [微服务架构设计的10个要点](http://developer.51cto.com/art/201807/579943.htm)
* [微服务实施失败总结：7大步骤高效推进微服务架构演进](http://developer.51cto.com/art/201708/549876.htm)

## Spring Cloud
1. [spring-cloud](http://projects.spring.io/spring-cloud/)
1. [spring cloud_百度百科](https://baike.baidu.com/item/spring%20cloud/20269825)
1. Spring Cloud中文网：[1](http://springcloud.cn/)，[2](https://springcloud.cc/)
1. [微服务框架-SpringCloud简介](http://blog.sina.com.cn/s/blog_493a84550102wkp2.html)
1. [SpringCloud分布式开发五大神兽](http://www.cnblogs.com/ilinuxer/p/6580998.html)
1. [springcloud(一)：大话Spring Cloud](http://www.cnblogs.com/ityouknow/archive/2017/05/01/6791221.html)
1. [史上最简单的 SpringCloud 教程](http://blog.csdn.net/forezp/article/details/70148833)
1. [ccblog教程](http://www.ccblog.cn/contentTag.htm?tag_id=94)
1. [Spring Cloud 系列文章](http://www.ityouknow.com/spring-cloud.html)

## Feign
https://www.jianshu.com/p/3d597e9d2d67
https://www.jianshu.com/p/191d45210d16

## 配置
* [使用Spring Cloud构建统一配置中心](https://www.jianshu.com/p/69dea19abf04)
https://blog.csdn.net/Ay_Ly/article/details/81077226
* [ZooKeeper 笔记(3) 实战应用之【统一配置管理】](https://www.cnblogs.com/yjmyzz/p/4604947.html)
