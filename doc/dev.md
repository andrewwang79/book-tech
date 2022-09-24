# 开发文档编写

## 阶段
| 阶段 | 目标 | 输出 | 说明 |
| :-: | - | - | - |
| 需求分析 | 要解决什么问题 | 需求规格说明书 | 功能清单，原型图 |
| 概要设计 | 整体怎么做 | 概要设计说明书 | 整体架构，各模块的功能和模块间的关系，与外部系统的关系。技术调研和选择的技术路线 |
| 详细设计 | 每个模块怎么做 | 详细设计说明书 | 细化需求文档到具体的实现细节，确定每个模块逻辑、数据结构和接口 <br> **如有结构调整（如分解出子模块等），必须返回到概要设计** |

## 需求分析
* 非业务功能：可靠性、安全性，可规模化、可定制化，可扩展性，可维护性

## 概要设计
* [IDEFO简介](http://blog.vsharing.com/feng5877/A693334.html)

## 详细设计
### 功能设计
* [HIPO图](https://blog.csdn.net/wangjingna/article/details/41318739) = 层次结构图(H图) + IPO图
* [层次图和HIPO图---描绘软件结构的图形工具](https://blog.51cto.com/mengdong/1398151)
* [HIPO图、IPO图、H图的关系](https://blog.csdn.net/lvshihua/article/details/8545345)

## UML
* https://www.cnblogs.com/wsg25/p/9592915.html

| 图 | 阶段 | 说明 | 常用 |
| :-: | - | - | - |
| 用例图 | 需求分析 | 系统所有功能的视图 | Y |
| 流程图 | 需求分析 | 系统所有功能的流程 | N |
| 泳道图 | 需求分析 | 按照职责/角色组织的流程图。可用于非研发流程的整理 | Y |
| 类图 | 概要设计 |  | Y |
| 时序图 | 详细设计 | 对象间基于传递消息的时间顺序的协作 | Y |
| 活动图 | 详细设计 | 具体功能的流程，类似流程图 | N |
| 状态图 | 详细设计 | 对象基于事件反应的动态行为 | N |
| 协作图 | 详细设计 | 对象间的交互过程，对象间的关联关系。是对象在时序图所有交互的视图 | N |

* [UML用例图详解](https://juejin.cn/post/6844903805226582030)
* [UML类图详解](https://www.codetd.com/article/3271199), [使用starUML绘制类关系图](https://www.365seal.com/y/zyn1LKKmp3.html)
* [看懂UML类图和时序图](http://design-patterns.readthedocs.io/zh_CN/latest/read_uml.html)
* [时序图、流程图、状态图、协作图](https://blog.csdn.net/rosekin/article/details/14519277)
* [UML的类关系](https://blog.csdn.net/K346K346/article/details/59582926)

| 关系 | 符号 | 说明 | 示例 |
| :-: | - | - | - |
| 泛化(generalize) | 空心三角箭头 | 继承 |  |
| 实现(realize) | 空心虚线三角箭头 | 继承抽象类 |  |
| 聚合关系(aggregation) | 空心菱形箭头 | 集体与个体的关系。非强依赖，集体不存在了个体仍然存在 | 部门撤销了人员依然存在 |
| 组合关系(composition) | 实心菱形箭头 | 整体与组成部分的关系。强依赖的一种聚合关系，整体不存在了部分也不存在了 | 公司不存在了部门也将不存在了 |
| 关联关系(association) | 直线箭头 | 不同对象间的静态关系 |  |
| 依赖关系(dependency) | 虚线直线箭头 | 不同对象间的运行期间的关系 |  |

## 资料
* 文档模板 : 本仓库目录/s/doc/dev/
