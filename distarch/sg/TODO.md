# 演示
## 1
* 演示各个组件的核心原理。
* zuul的负载均衡，前置拦截过滤，spring gateway在此基础上增加的长连接功能
* eureka和zookeeper  通过注册中心的客户端工具，显示服务在注册中心注册的数据
* 远程调用 feign的远程调用和负载均衡
* 熔断 hystrix 演示熔断效果，打开hystrix的dashboard
* 链路跟踪，先演示sleuth的原理，再整合zipkin
## 2
* 在elk系统里可以根据返回给客户端的traceId，直接在kibana里面检索到所有请求的日志
* 演示限流，熔断，降级

https://github.com/ctripcorp/apollo-use-cases
网关，限流，配置中心的整合
Spring Boot Admin

# 延伸
* 限流 熔断 降级怎么做
* 网关处限流解决方案
* 远程调用的熔断，降级解决方案
* 如何跟踪和定位问题
* 注册中心与CAP原理
* eureka和zookeeper的区别
* 如何设计一个rpc框架
* 分布式事务原理
* 分布式事务现有框架：http://seata.io/zh-cn/docs/overview/what-is-seata.html，https://www.codingapi.com/docs/txlcn-preface/
* 分库分表
