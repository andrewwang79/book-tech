# QNX
* [QNX](https://www.vxworks.net/qnx/817-introduction-of-qnx)是一种商用的分布式、嵌入式、可规模扩展、遵从POSⅨ规范的类Unix实时操作系统
* 安全（Secure）、可靠（Reliable）、可信（Trusted）：稳定性和安全性非常高，实时性也比较好
* 主要市场(安全性要求极高的领域)：汽车、航空、核电站、工业自动化、通讯设备等

## 微内核架构
* 核心仅提供4种服务：进程调度、进程间通信、底层网络通信和中断处理。
* 驱动程序、协议栈、文件系统、应用程序等都在微内核之外内存受保护的安全的用户空间内运行，组件之间能避免相互影响，在遇到故障时也能重启。
