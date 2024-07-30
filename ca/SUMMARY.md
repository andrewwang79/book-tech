# 计算机架构
## 操作系统

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
| [DDS(Data Distribution Service)](/os/sw_component/dds) | 基于Topic来实现发布-订阅模式，没有中心节点，是端到端分布式通信中间件。 <br> 不适合大规模端点(没有中心节点导致发现成本太高) | 标准以太网 |
| MQTT |  | 标准以太网 |

* [物联网通信协议——比较-MQTT、 DDS、 AMQP、XMPP、 JMS、 REST、 CoAP](https://www.cnblogs.com/saryli/p/9742709.html)

## 软件架构
| 名称 | 说明 |
| - | - |
| Adaptive AUTOSAR | 针对汽车行业的标准软件架构，提供大量的接口，通信与诊断规范，最终生成ECU的固件。 <br> SOME/IP和DDS都在标准内 |
