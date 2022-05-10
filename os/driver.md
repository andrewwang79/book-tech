# 硬件驱动
![系统架构](https://pic3.zhimg.com/80/v2-946e2945c18392f8f0e8546c42a72fea_1440w.jpg)

## 原理理解
* 应用程序和驱动程序之间是数字信号，驱动程序基于硬件手册从硬件引脚发送和接收信号
* [驱动开发理解](https://blog.csdn.net/weixin_43162745/article/details/102884603)

## 驱动开发
* [Linux驱动基础开发](https://zhuanlan.zhihu.com/p/154288298)
* [Linux驱动开发-编写PCF8591(ADC)芯片驱动](https://blog.51cto.com/u_11822586/5200761)

## 资料
* [FPGA和单片机的区别](https://zhuanlan.zhihu.com/p/267495455)
* [单片机和PLC的区别](https://www.eet-china.com/mp/a13549.html)

| 项 | 定义 | 说明 |
| :-: | - | - |
| FPGA | 可编程(通用)的硬件集成电路，通过硬件编程语言实现复杂逻辑 | 是设计芯片的芯片，不需要流片 |
| 单片机(Microcontrollers) | 固化逻辑的硬件集成电路(CPU芯片) | 一般都代指单片机系统，会有配套内存IO等，通过软件编程语言实现逻辑 <br> 软件编程语言通过汇编语言转换成芯片的指令，在芯片上执行 |
| PLC(Programmable Logic Controller) | 是一种工控系统(软硬件)，预置特定业务功能 | 相当于开发板+已开发好的各种业务功能 <br> 大多PLC的控制芯片实际上就是单片机，没有合适的PLC就自行开发单片机系统 |
