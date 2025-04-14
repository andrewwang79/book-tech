# 通信标准协议

## 分类清单

| 分类 | 应用 | 特点 | 常用协议 |
| - | - | - | - |
| 现场总线 | 工业自动化和过程控制 | 分布式控制、实时性、开放性和互操作性。<br> 双绞线，低速小数据量，成本低 | Profibus、Foundation Fieldbus、Modbus、CAN、DeviceNet、HART |
| 工业以太网 | 高性能和高可靠性的工业自动化系统 | 高带宽、实时通信、冗余设计<br> 网线，高速大数据量，成本中高 | Profinet、EtherNet/IP、Modbus TCP、EtherCAT、Powerlink |
| 物联网 | 智能制造、智能城市、智能家居等 | 广泛连接、数据驱动、智能分析 | MQTT、CoAP、LoRaWAN、NB-IoT、Zigbee |

## 资料
| 名称 | 说明 |
| - | - |
| 标准以太网 | TCP/UDP |
| [EtherCAT总线](https://zhuanlan.zhihu.com/p/80572311) | 以太网为基础的现场总线系统，工业以太网 <br> 环形拓扑 |
| CAN总线(Controller Area Network) | 分布式控制或实时控制的串行通信网络 |  

* [现场总线CAN和工业以太网EtherCAT](https://blog.csdn.net/weixin_37863258/article/details/109556747)
* [物联网通信协议——比较-MQTT、 DDS、 AMQP、XMPP、 JMS、 REST、 CoAP](https://www.cnblogs.com/saryli/p/9742709.html)

### CAN
* 支持节点间直接通信

## OPC
* OPC Foundation：一个国际性组织，成立于1996年，致力于开发和推广工业自动化和过程控制领域的通信标准。
* OPC UA（OPC Unified Architecture）：实现不同设备和系统之间的互操作性，安全、可靠地传输数据和信息。是一个跨平台、服务导向、独立于传输层的工业自动化的通信协议(不止以太网)，提供了一个标准化的**框架**
