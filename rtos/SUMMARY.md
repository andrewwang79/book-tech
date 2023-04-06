# 计算机架构
## 实时操作系统

| 名称 | 说明 |
| - | - |
| [QNX](/rtos/qnx) | 类Unix实时操作系统 |
| [Linux](/rtos/linux) | X86是PREEMPT_RT(Linux内核的一个实时补丁)，Arm是Xenomai。[QNX与Linux比较](https://blog.csdn.net/xjhhjx/article/details/95724770) |

### 特征
1. 高精度计时系统
计时精度是影响实时性的一个重要因素。在实时应用系统中，经常需要精确确定实时地操作某个设备或执行某个任务，或精确的计算一个时间函数。这些不仅依赖于一些硬件提供的时钟精度，也依赖于实时操作系统实现的高精度计时功能。
1. 多级中断机制
一个实时应用系统通常需要处理多种外部信息或事件，但处理的紧迫程度有轻重缓急之分。有的必须立即作出反应，有的则可以延后处理。因此，需要建立多级中断嵌套处理机制，以确保对紧迫程度较高的实时事件进行及时响应和处理。
1. 实时调度机制
实时操作系统不仅要及时响应实时事件中断，同时也要及时调度运行实时任务。但是处理机调度并不能随心所欲的进行，因为涉及到两个进程之间的切换，只能在确保“安全切换”的时间点上进行，实时调度机制包括两个方面，一是在调度策略和算法上保证优先调度实时任务；二是建立更多“安全切换”时间点，保证及时调度实时任务。

## 软件
| 名称 | 说明 |
| - | - |
| [ROS2(Robot Operating System)](/rtos/ros) | 机器人管理软件，可运行在Linux等操作系统 |
| [TwinCAT(The Windows Control and Automation Technology)](/rtos/twincat) | 基于Windows的运动控制软件(运动控制+通讯)，使用EtherCAT总线 |

## 总线
| 名称 | 说明 |
| - | - |
| 标准以太网 | TCP/UDP |
| [EtherCAT总线](https://zhuanlan.zhihu.com/p/80572311) | 以太网为基础的现场总线系统，工业以太网 <br> 环形拓扑 |
| CAN总线(Controller Area Network) | 分布式控制或实时控制的串行通信网络 |  

* [现场总线CAN和工业以太网EtherCAT](https://blog.csdn.net/weixin_37863258/article/details/109556747)

## 通信设备
| 名称 | 说明 |
| - | - |
| [SPI(串行外围设备接口/Serial Peripheral interface)](https://zhuanlan.zhihu.com/p/150121520) | 高速、同步、全双工。EtherCAT使用了SPI |
| [UART(通用异步收发器/Universal Asynchronous Receiver/Transmitter)](https://zhuanlan.zhihu.com/p/150504364) | 串行、异步、全双工。在嵌入式领域应用的非常广泛 |

## 通信协议和中间件
| 名称 | 说明 | 总线 |
| - | - | - |
| [SOME/IP(Scalableservice-Oriented Middleware over IP)](https://zhuanlan.zhihu.com/p/253077443) | 事件通知，远程过程调用和访问进程数据 | 标准以太网 |
| [DDS(Data Distribution Service)](/rtos/dds) | 基于Topic来实现发布-订阅模式，没有中心节点，是端到端分布式通信中间件。 <br> 不适合大规模端点(没有中心节点导致发现成本太高) | 标准以太网 |
| MQTT |  | 标准以太网 |

* [物联网通信协议——比较-MQTT、 DDS、 AMQP、XMPP、 JMS、 REST、 CoAP](https://www.cnblogs.com/saryli/p/9742709.html)

## 软件架构
| 名称 | 说明 |
| - | - |
| Adaptive AUTOSAR | 针对汽车行业的标准软件架构，提供大量的接口，通信与诊断规范，最终生成ECU的固件。 <br> SOME/IP和DDS都在标准内 |
