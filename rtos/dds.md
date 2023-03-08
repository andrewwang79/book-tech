# DDS
## 介绍
* 基于Topic来实现发布-订阅模式，没有中心节点，是端到端分布式通信中间件。不适合大规模端点(没有中心节点导致发现成本太高)
  * 基于TCP/IP
  * 通过topic各节点相互发现和通讯
  * 虚拟的全局数据空间，所有数据都在这个空间中，每个节点可以向这个空间读写数据。
* 适用场景是群体协同，特别是多机器人协同

## 资料
* [分布式实时通信——DDS技术](https://zhuanlan.zhihu.com/p/192981171)
* [介绍](https://blog.csdn.net/DDS_CSIT/article/details/104607476)
* [原理](https://keyou.github.io/blog/2020/09/21/dds-middleware/)
