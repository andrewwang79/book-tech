## TwinCAT
* [TwinCAT(The Windows Control and Automation Technology)](/os/sw_component/twincat) ：基于Windows的运动控制软件(运动控制+通讯)，使用EtherCAT总线
* [TwinCAT](https://blog.csdn.net/jldemanman/article/details/79207148)是Beckhoff公司基于Windows的运动控制软件，有[ADS(Automation Device Specification/自动化设备规范)](https://blog.csdn.net/akadiao/article/details/118185495)
* 通过C++/PLC混合程序控制PLC
* 通讯：上位机(PC) <-ADS通讯-> PLC <-EtherCAT总线-> 设备
* 包含三层结构：PLC轴、NC轴(Numberic Control)和物理轴
* [倍福学院](https://tr.beckhoff.com.cn/)

## 开发
### 结构定义
1. POU (Program Organization Unit)：程序组织单元，包括程序（Program）、功能块（Function Block）和函数（Function）。是PLC编程的基本构建块。
    * Program：一可以独立执行的代码块，通常用来实现特定的控制任务。
    * Function Block：带有内部状态的代码块，可以实例化多次。类似于面向对象编程中的类。
    * Function：没有内部状态的代码块，通常用来执行特定的计算任务，并返回一个结果。
1. DUT (Data Unit Type)：数据类型单元。用户定义的数据类型，包括枚举（Enum）、结构（Struct）和联合（Union）等。
1. GVL (Global Variable List)：全局变量列表。定义在整个项目中都可以访问的全局变量。提供了一种在不同的POU之间共享数据的方式。
1. VISU (Visualization)：创建人机界面（HMI），监控和控制PLC系统。

## EAP
* EAP（EtherCAT Automation Protocol）是一种用于工业自动化的通信协议，基于EtherCAT实时以太网技术，实现设备之间的高效数据交换。
* EAP设备之间的通讯基于发布服务器/订阅服务器原则进行。

## ADS
* [ADS高级培训](https://tr.beckhoff.com.cn/pluginfile.php/44857/mod_resource/content/0/ADS%E9%AB%98%E7%BA%A7%E5%9F%B9%E8%AE%AD.pdf)
* [ADS返回码](https://infosys.beckhoff.com/english.php?content=../content/1033/tf6701_tc3_iot_communication_mqtt/374277003.html&id=)