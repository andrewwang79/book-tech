# 测试
* 测试目的：不是找bug，而是确保质量。
* 质量保证方法：覆盖率

## 概念术语
| 名称 | 英文 | 说明 |
| --------  | ----- | ---- |
| 测试用例 | TestCase | 有类型区别 |
| 测试用例集 | TestCaseSuite | 由测试用例组成，用于不同的测试目标。如每天测试，回归测试，性能测试，压力测试 |
| 测试报告 | TestReport | 由测试用例集组成，有对应的bug列表 |
| 缺陷 | Bug |  |  |

## 测试类型
### 功能测试
| 测试 | 英文 | 说明 |
| ---- | ---- | ---- |
| 单元测试 | Unit Testing | 最小可测试单元：类、方法或者函数 |
| 接口测试 | Interface Testing | API |
| 集成测试 | Integration Testing | 测试不同组件的接口部分 |
| 冒烟测试 | Smoke Testing | 核心业务的正向流程 |
| 系统测试 | System Testing | all |
| 回归测试 | Regression Testing | 修改部分的测试 |
| 确认测试/验收测试 | Acceptance Testing | 软件需求规格说明书里的功能和性能 |

### 非功能测试
| 测试 | 英文 | 说明 |
| ---- | ---- | ---- |
| 性能测试 | Performance Testing |  |
| 负载测试 | Load Testing |  |
| 压力测试 | Stress Testing |  |
| 容量测试 | Volume Testing |  |
| 安全测试 | Security Testing |  |
| 兼容性测试 | Compatibility Testing |  |
| 安装测试 | Install Testing |  |
| 恢复测试 | Recovery Testing |  |
| 可靠性测试 | Reliability Testing |  |
| 可用性测试 | Usability Testing | 可用易用 |
| 一致性测试 | Compliance Testing |  |
| 本地化测试 | Localization Testing |  |

## 内容对应的测试
| 内容 | 测试 | 说明 |
| :----: | ---- | ---- |
| 需求 | 系统测试 |  |
| 概要设计 | 集成测试，接口测试 |  |
| 详细设计 | 单元测试 |  |
| 风险 | 系统测试 |  |

## 测试用例
* UI的测试用例不用分开一个个写，一个UI一个测试用例
* 注意测试用例的复用性，不要因为小改动而要调整测试用例
* [软件测试用例模板（带实例）](https://wenku.baidu.com/view/37712285b9d528ea81c77939)

## 资料
* [软件测试方法——单元测试、集成测试、系统测试、确认测试](https://blog.csdn.net/u012426327/article/details/78400045)
* [单元测试、集成测试、系统测试和验收测试、冒烟测试、回归测试、随机测试、探索性测试和安全测试](https://juejin.im/post/6844903986462457864)
* [软件测试基础知识](http://wenku.baidu.com/view/388fdad0360cba1aa911da01.html)
* [软件测试类型](http://baike.baidu.com/item/%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95%E7%B1%BB%E5%9E%8B)
* [软件测试的16种测试类型](http://wenku.baidu.com/view/cac33c37eefdc8d376ee32ed.html)
* [bug优先级和严重级定义](http://blog.csdn.net/sunshine_mei/article/details/49230199)
* [阿里完整自动化测试解决方案macaca](https://yq.aliyun.com/articles/8310)
* [软件测试网](http://www.51testing.com/)

### 用户的测试级别
用户的测试级别有3级

| 级别 | 范围 | 说明 |
| :----: | ---- | ---- |
| 1 | 测试部门 |  |
| 2 | 公司内部 |  |
| 3 | 公司外部 |  |
