# 需求文档

* 需求类型

| 项 | PRD内容 | 追溯表 |
| - | - | - |
| 市场/用户需求 | / | / |
| 产品需求 | 子系统间的 | 追溯到市场需求或法律法规 |
| 子系统需求 | 子系统内的 | 追溯到产品需求或法律法规 |

* 需求用例编码：系统代号_子系统缩写_一级缩写_次级缩写(可选)
* 需求用例的详细内容可以记录到需求系统(如JIRA、TFS)

## 编写
### 文档结构
* [PRD到底该怎么写？](http://www.woshipm.com/pmd/192826.html)
1. 术语，目标，原则
1. 需求
    1. 功能需求：产品的需求用例图，产品的业务流程(流程图、泳道图、时序图)，模块功能
    1. 非功能需求：如安全性能，网络安全等
1. 模块
    1. 模块的需求用例图
    1. 需求用例

### 需求用例图
![](https://yqfile.alicdn.com/img_7a58cb217ccdd665f24519ceead1bc9c.png)

### 需求用例
* = 系统规则 + 界面交互
* 内容：
  1. 编号，名称，优先级
  1. 使用角色，场景描述
  1. 前置条件，后置条件
  1. 原型
  1. 业务规则 = 数据规则，状态逻辑规则，交互规则。部分在原型，部分在UML(状态图，主流程，分支流程，异常流程)

![](https://yqfile.alicdn.com/img_a8bfef6d646b841b9be04bfcf31363da.jpeg)

### 资料
1. [BRD、MRD和PRD](https://www.zhihu.com/question/19655491) : 分别是做吗，做什么，怎么做
1. [市场需求文件（MRD）简介、框架、模板](https://zhuanlan.zhihu.com/p/57413137)
1. [产品经理十四章：产品需求文档(PRD)](https://developer.aliyun.com/article/655300)
1. [用原型代替PRD时，原型应该包含哪些内容](http://www.woshipm.com/rp/227461.html)

## 工具
1. [Axure RP 7.0快捷键 汇总](http://www.woshipm.com/pd/81482.html)
1. axure库：[axure](http://www.axure.com/community/widget-libraries)，[axureland](http://axureland.com/axure-widget-libraries)
