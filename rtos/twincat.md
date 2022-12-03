## TwinCAT
* [TwinCAT(The Windows Control and Automation Technology)](https://blog.csdn.net/jldemanman/article/details/79207148)是Beckhoff公司基于Windows的运动控制软件
* 通过C++/PLC混合程序控制PLC。PLC通过EtherCAT总线和设备通讯，PLC通过[ADS通讯](https://blog.csdn.net/akadiao/article/details/118185495)和上位机(PC)通讯
* 包含三层结构：PLC轴、NC轴和物理轴。
  1. PLC轴是通过系统PLC中的梯形图编写后会运行的轴,
  1. NC轴就是系统本身自带的运行轴
  1. 物理轴
