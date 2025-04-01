# 计算机系统

> book : https://tech.wangyaqi.cn/

## 概念
### 系统和设备
| 名称 | 说明 | 实例 |
| - | - | - |
| 硬件 | 是计算机或其他电子系统中物理部件的统称，通过软件(如操作系统、驱动程序等)进行控制和管理 | 内部设备 : 处理器、内存、硬盘、显卡、电源 <br> 外围设备 : 显示器、键盘、鼠标、摄像头 |
| 软件 | 软件程序，需在硬件设备上运行 | Linux、Notepad、Word |
| 设备 | 实现特定任务或功能而设计制造的工具、机器或装置 | 电子设备：显微镜、打印机、手机、笔记本、电视、空调 <br> 机械设备：机床 |
| 系统 | 由一组互相协作的**组件**（包括硬件、软件、设备等）共同完成一个或多个任务的有机整体，复杂系统可以包含子系统。 | 12306 系统包含了服务器硬件、售票软件、数据库管理系统、网络设备等多种组件，通过这些组件的协同工作，实现了火车票的预订、查询、售票等功能。 |

## 通信设备
| 名称 | 说明 |
| - | - |
| [SPI(串行外围设备接口/Serial Peripheral interface)](https://zhuanlan.zhihu.com/p/150121520) | 高速、同步、全双工。EtherCAT使用了SPI |
| [UART(通用异步收发器/Universal Asynchronous Receiver/Transmitter)](https://zhuanlan.zhihu.com/p/150504364) | 串行、异步、全双工。在嵌入式领域应用的非常广泛 |

## 操作系统

## 软件架构
| 名称 | 说明 |
| - | - |
| AUTOSAR | 针对汽车行业的标准软件架构，提供大量的接口，通信与诊断规范，最终生成ECU的固件。 <br> SOME/IP和DDS都在标准内 |
| [ROS2(Robot Operating System)](/os/sw_component/ros) | 机器人管理软件，可运行在Linux等操作系统 |

## 通信中间件
* [通信标准协议](/comm/SUMMARY)

| 名称 | 说明 | 总线 |
| - | - | - |
| [SOME/IP(Scalableservice-Oriented Middleware over IP)](https://zhuanlan.zhihu.com/p/253077443) | 事件通知，远程过程调用和访问进程数据 | 标准以太网 |
| [DDS(Data Distribution Service)](/os/sw_component/dds) | 对象管理组织（OMG）制定的标准，满足分布式实时系统中设备或系统间的数据通信，强调数据的高效分发和共享 <br> 基于Topic来实现发布-订阅模式，没有中心节点，是端到端分布式通信中间件。 <br> 不适合大规模端点(没有中心节点导致发现成本太高) | 标准以太网 |
| [ADS(Automation Device Specification)](/os/sw_component/twincat) | 倍福（Beckhoff），自动化系统中设备间通信的协议 |  |