# 灰度升级
* 功能逐级发布
* 本质是流量治理，逐级分配流量到不同环境
* facebook的机制, gatekeeper

## 方案
* 本质上是个功能的路由器，可重定向，可关闭。
* 每个功能都有发布级别，上下线
* 分流控制：可指定特定地域，用户级别等
* 每个发布控制点关联一个功能编码
* 功能的发布级别是可以管理配置的。支持手工调整和自动调整(如3天升一级)
* 用户选择随机性确保：功能编码做随机数种子。
* 独立的灰度服务：选出用户列表或设置筛选条件[级别，城市等]，关联对应灰度级别。
* 灰度信息：灰度级别及其对应的功能
* 前端
  1. 不用nginx发布，麻烦&&扩展性差
  1. 获取用户的灰度信息，执行不同的页面和逻辑

### 结构分析
| 项 | 内容 | 说明 |
| :-: | - | - |
| 前端-网站 | 1个 |  |
| 前端-app | 多个 |  |
| 前端-小程序 | 1个 |  |
| 服务端 | 多个；1个数据库 | Java用SpringCloud |

### QA
| Q | A |
| :-: | - |
| 如何处理：APP是灰度 && 服务端是正式的商户 | 不让它发生：不发布到任何app市场，选择出要灰度的商户做定向发布 |

### 发布级别
| 级别 | 范围 | 说明 |
| :----: | ---- | ---- |
| 1 | 公司内部 | 内测 |
| 2 | 1% | 外部小范围，忠诚度较高的种子用户/活跃用户 |
| 3 | 5% | 外部大范围 |
| n | 100% | 发布 |

# 资料
* [灰度发布方案](https://cloud.tencent.com/developer/article/1178722)
* [灰度发布](http://arganzheng.life/gray-release.html)
* [前端灰度发布](https://juejin.cn/post/6844903969110622222)
* [使用Nginx实现Web应用灰度发布](https://www.jianshu.com/p/e89ad8748764)，cookie,ip
* [BAT 公司是怎样做产品灰度发布的？](https://www.zhihu.com/question/28296375)
* [AB测试和灰度发布平台架构设计和实践](http://doc.mbalib.com/view/1622be0db26dc1400284e0ea95fd2f80.html)

## AB测试
* 可以用灰度发布，也可以用功能切换(1套服务)
* 用户有功能版本列表(功能+AB版本)，不同功能间的版本是独立的。
* 功能版本列表存放在本地，如cookie。
* 没有功能版本则使用功能前自动分配。
* 分流控制：等比例分配。如2个版本各是50%，5个版本各是20%。
* 每个功能版本都有其页面版本包(页面和逻辑)。通过用户版本自动加载不同的页面和逻辑。
* 测试完成后，可以全部使用选中的版本。

## SaaS系统的灰度
* 2个环境：灰度环境，正式环境
* 支持粒度：商户
* 升级失败c端无法回滚
* 升级商户筛选条件：设备支持静默升级 && 个人版
