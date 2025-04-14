# ROS2替代倍福
## 倍福优势
1. 通信实时性高
1. 现有工业设备的集成度高(PLC、驱动器)

## 方案
| 项 | 倍福(闭源) | ROS2(开源) | 说明 |
| - | - | - | - |
| OS | Win + TwinCAT | Ubuntu(RT - Preempt) + ROS2 |  |
| 上位机通信 | ADS | DDS | ADS几毫秒，DDS几十毫秒 |
| 下位机通信 | EtherCAT | EtherCAT的开源版本？https://tech.wangyaqi.cn/#/comm/SUMMARY |  |