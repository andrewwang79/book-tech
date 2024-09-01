# DDS
## 介绍
* [分布式实时通信-DDS技术](https://zhuanlan.zhihu.com/p/192981171), [介绍](https://blog.csdn.net/DDS_CSIT/article/details/104607476), [原理](https://keyou.github.io/blog/2020/09/21/dds-middleware/)
* Data Distribution Service(数据分发服务)。**端到端分布式通信中间件**。用于实时分布式系统，提供高性能、低延迟的消息传递，平均100微秒。
* 2004年由对象管理组织OMG（Object Management Group）发布，专门为实时系统设计的数据分发/订阅标准。最早应用于美国海军，解决舰船复杂网络环境中大量软件升级的兼容性问题，目前已经成为美国国防部的强制标准。广泛应用于**国防、民航、工业控制、汽车**等领域，成为分布式实时系统中数据发布/订阅的**标准解决方案**。

## 核心技术
1. 以数据为核心的基于TOPIC的发布订阅模型（Data-Centric Publish-Subscribe，DCPS）
1. 创建了一个虚拟的**“全局数据空间”**（global data space），系统所有数据都在这个空间中，所有独立的应用都可以去读写数据。每一个发布者或者订阅者都称为参与者（participant），每一个参与者都可以使用某种定义好的数据类型来读写全局数据空间。
1. 3个层级：domain(管理和维护便利，同domain的才可通信)，partition(访问权限控制)，topic(模块和数据名)
1. 基于TCP/IP，没有中心节点，通过topic各节点相互**自动发现**和通讯。
1. QoS支持持久化和访问权限

## 使用场景
1. 适用小规模数据，不是大规模数据。用于通讯(信令和信息传输)，不是大数据传输。大数据传输可使用NFS/FTP/socket等配合DDS。
1. 不适合大规模节点：通过广播自动发现限制了节点数量

## 使用方法
1. 同一型号的两台设备使用方法：domain一样，partition不一样(相当于SN)，topic一样(编码一致)。

## 第三方库
### FastDDS
* [eProsima Fast DDS](https://github.com/eProsima/Fast-DDS)
* [安装](https://eprosima-dds-router.readthedocs.io/en/latest/rst/developer_manual/installation/sources/linux.html)