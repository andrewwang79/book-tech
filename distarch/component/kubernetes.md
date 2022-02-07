# Kubernetes
* https://www.kubernetes.org.cn/
* 容器编排系统，服务扩容和升级

## 资料
* [扫盲](https://www.cnblogs.com/menkeyi/p/7134460.html)
* [官方](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
* [词汇表](https://kubernetes.io/zh/docs/reference/glossary/)

## 定义
| 项 | 名称 | 说明 |
| :----: | ---- | ---- |
| Master | 管理节点 |  |
| Node | 服务节点 | 运行Pod的工作机器 |
| Pod |  | 原子对象，有一个IP和端口，类似服务器。运行在Node上，包含一个容器或者多个相关容器(依赖)，所有容器共享相同的主机名和网络接口 |
| Service |  | 运行在一组Pods上的应用程序公开为网络服务 |
| Deployment |  | 创建ReplicaSet 和Pod |
| Label |  | 可以附加在各种资源对象上，如Node、Pod、Service、RC |

## QA
* [有了容器为什么 kubernetes 还需要 Pod？](https://xie.infoq.cn/article/cd386e6de0a37dbe0af4cb2e7) : 1个容器一般1进程，pod解决了业务是多进程的需求

## 参考
* [k8s介绍及与docker搭建集群](https://blog.csdn.net/skh2015java/article/details/80300562)
* [中文文档](https://www.kubernetes.org.cn/k8s)
* [Kubernetes提供服务发现](http://baijiahao.baidu.com/s?id=1579758778464216551)
* [Service Mesh](https://zhuanlan.zhihu.com/p/27512075)
