# Spring Cloud
## 组件
### 网关
* spring gateway (基于netty异步io)
* zuul (同步Servlet，多线程阻塞模型)
* spring gateway性能比zuul更好/支持长连接/长期维护

###  注册中心
* [alibaba/nacos](https://nacos.io/zh-cn/):注册和配置
* Eureka
* etcd
* zk

### 通讯
* Feign(http)
* https://www.jianshu.com/p/3d597e9d2d67
* https://www.jianshu.com/p/191d45210d16

### 链路追踪
* 客户端采集工具sleuth。 核心原理(traceId,spanId)
* 分布式追踪系统zipkin(可以接入kafka缓冲，es存储)

### 流量管理/限流
* alibaba/Sentinel
* redis限流设计

### 服务容错:熔断，降级
* Hystrix
* Hystrix Dashboard

### 配置中心
* [使用Spring Cloud构建统一配置中心](https://www.jianshu.com/p/69dea19abf04)
https://blog.csdn.net/Ay_Ly/article/details/81077226
* Nacos
  * [spring cloud集成nacos配置中心](https://juejin.im/post/6844903783684653064)
* Apollo
  * [配置中心功能与设计参考apollo作者文章](https://nobodyiam.com/2018/07/29/configuration-center-makes-microservices-smart/)
* Zookeeper
  * [ZooKeeper 笔记(3) 实战应用之【统一配置管理】](https://www.cnblogs.com/yjmyzz/p/4604947.html)
  * [使用 zk与 springboot 搭建配置中心](https://www.jianshu.com/p/9b805dfc2a7b)
  * [Zookeeper笔记之基于zk的分布式配置中心](https://www.cnblogs.com/cc11001100/p/10230608.html)
  * [Zookeeper的集群配置和Java测试程序](https://blog.csdn.net/catoop/article/details/50848555)

## 服务治理系统
* spring boot admin

## 资料
* [spring-cloud](http://projects.spring.io/spring-cloud/)
* [spring cloud_百度百科](https://baike.baidu.com/item/spring%20cloud/20269825)
* Spring Cloud中文网：[1](http://springcloud.cn/)，[2](https://springcloud.cc/)
* [微服务框架-SpringCloud简介](http://blog.sina.com.cn/s/blog_493a84550102wkp2.html)
* [SpringCloud分布式开发五大神兽](http://www.cnblogs.com/ilinuxer/p/6580998.html)
* [springcloud(一)：大话Spring Cloud](http://www.cnblogs.com/ityouknow/archive/2017/05/01/6791221.html)
* [史上最简单的 SpringCloud 教程](http://blog.csdn.net/forezp/article/details/70148833)
* [ccblog教程](http://www.ccblog.cn/contentTag.htm?tag_id=94)
* [Spring Cloud 系列文章](http://www.ityouknow.com/spring-cloud.html)
