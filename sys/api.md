# API规范
1. 采用POST模式
1. 数据通信格式采用json传输
1. 所有数据采用UTF8编码
1. [方法命名规范](#方法命名规范)基于RESTFUL规范
1. 传输默认时间：使用字符串，格式"yyyyMMddHHmmss"

## 接口规范
### 请求
* 报文头字段

| 名称 | 字段 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 签名 | sign | string | Y |  |
| 用户令牌 | token | string | N | 登录后才有 |
| [请求方信息结构](#请求方信息结构) | client | string | N |  |

* 业务字段

| 名称 | 字段 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 请求号 | requestId | string | N | 唯一号，异步使用 |
| 方法 | method | string | Y |  |
| 版本 | ver | string | Y |  |
| 业务数据 | data | json | N |  |

```json
curl -H "Content-type: application/json" -X POST -d '{"requestId":135213, "method":"user/read", "ver":"1.0", "data":{"id":1}}' 'https://api.x.com/'
```

### 返回
* 报文头字段

| 名称 | 字段 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 签名 | sign | string | Y |  |

* 业务字段

| 参数 | 名称 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 请求号 | requestId | string | N | 唯一号，异步使用 |
| 开始时间 | beginTime | long | Y | 时间戳，毫秒 |
| 结束时间 | endTime | long | Y | 时间戳，毫秒 |
| [返回码](#返回码) | code | int | Y | 0是成功 |
| 业务数据 | data | json | N | 业务执行结果。返回码成功时的业务信息，返回码非零的错误信息(是结构，不是message) |
| 异常信息 | verbose | string | N | 一般是堆栈，条件=(异常 AND (非生产环境 OR (生产环境 AND 未知错误))) |

* 成功
```json
{"requestId":135213, "beginTime":1650868552, "endTime":1650868552, "code":0, "data":{"name":"wangyaqi"}}
```

* 失败
```json
{"requestId":135213, "beginTime":1650868552, "endTime":1650868552, "code":1011}
```

### data定义示例
* API输出data定义

| 名称 | 字段 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 姓名 | name | string | Y |  |
| 当前公司 | company | Company | Y |  |
| 上过的学校 | schools | array(School) | N |  |

* Company定义

| 名称 | 字段 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 名称 | name | string | Y |  |
| 地址 | address | string | N |  |

* School定义

| 名称 | 字段 | 类型 | 必须 | 说明 |
| :-: | - | - | - | - |
| 名称 | name | string | Y |  |
| 地址 | address | string | N |  |

## 方法命名规范
* 格式 : entity/operation，entity多层用/分隔，operation多单词用_分隔
* 示例

| 操作 | 示例 | 说明 |
| :-: | - | - |
| 创建(C) | user/create |  |
| 读取(R) | user/read |  |
| 更新(U) | user/update |  |
| 删除(D) | user/delete |  |
| 查询 | user/query | 无分页 |
| 搜索 | user/search | 有分页 |
| 自定义操作 | user/batch_delete | 批量删除用户 |
| 多层entity-列表读取 | user/school/all | 获取用户所有学校 |
| 多层entity-自定义操作 | user/password/forget | 忘记密码 |

* 常用自定义操作

| 功能 | 编码 |
| :-: | - |
| 登录 | login |
| 登出 | logout |
| 列表 | list |
| 所有 | all |
| 批量删除 | batch_delete |
| 忘记 | forget |
| 重置 | reset |
| 导入 | import |
| 导出 | export |
| 检查 | check |
| 申请 | apply |

## 返回码
### 范围
| 项 | 定义 | 说明 |
| :-: | - | - |
| 0 | 请求成功 |  |
| 1-499 | 通用系统错误 |  |
| 500-999 | 通用业务错误 |  |
| 1000以上 | 自定义业务错误 | 业务系统自行定义使用 |

### 定义
* 成功

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 0 | 成功 | SUCCESS |

* 系统

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 1 | 失败 | FAIL，包括异常 |
| 2 | 资源锁定失败 | LOCK_FAIL |
| 3 | 无可用资源 | NO_RESOURCE |

* 请求

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 40 | 请求的内容类型错误 | REQUEST_CONTENT_TYPE_ERROR |
| 41 | 请求的数据结构错误 | REQUEST_DATA_STRUCT_ERROR |

* 接口

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 50 | 无接口 | NO_METHOD |
| 51 | 无权限 | NO_PERMISSION |
| 52 | 接口废弃 | DEPRECATED |
| 53 | 操作频繁 | OPERATION_FAST |
| 54 | 超过最大尝试次数 | MAX_TRY |

* 输入参数检查

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 80 | 参数缺失 | PARAM_MISS |
| 81 | 参数错误 | PARAM_ERROR |
| 82 | 参数错误-长度 | PARAM_LENTH_ERROR |
| 83 | 参数错误-格式 | PARAM_FORMAT_ERROR |

* 业务处理

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 400 | 数据不存在 | NOT_EXIST |
| 401 | 数据已存在 | EXIST |
| 402 | 数据重复 | DATA_DUP |
| 413 | 删除失败 | DELETE_ERROR |
| 414 | 创建失败 | CREATE_ERROR |
| 415 | 修改失败 | UPDATE_ERROR |
| 450 | 验证码错误 | CAPTCHA_ERROR |
| 451 | 验证码发送频繁 | CAPTCHA_SEND_FAST |
| 460 | 地址解析错误 | ADDRESS_PARSE_ERROR |

* 账号权限

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 500 | 登录失败 | LOGIN_FAIL |
| 501 | 需登录  | NEED_LOGIN |
| 503 | 账户冻结 | ACCOUNT_FROZEN |
| 506 | 账户警告 | ACCOUNT_WARNING |
| 507 | 手机号已使用 | MOBILE_USED |
| 508 | 该账户已被禁用，请联系客服 | ACCOUNT_BAN |
| 509 | 该账号已完成绑定，请勿重复提交 | ACCOUNT_BIND |
| 510 | 微信和微信公众号不是同一个账号 | WX_USER_USED |
| 511 | 手机号不存在 | MOBILE_NOT_EXIST |
| 512 | 密码错误 | PWD_ERROR |
| 513 | 新旧密码相同 | SAME_PWD |
| 520 | 角色编码错误 | ROLE_CODE_ERROR |

* 文件系统

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 900 | 目录不存在 | NO_DIR |
| 901 | 目录为空  | EMPTY_DIR |
| 905 | 目录已存在  | EXIST_DIR |
| 910 | 文件不存在 | NO_FILE |

* 算法

| 编码 | 名称 | 说明 |
| :-: | - | - |
| 950 | 预处理错误 | PREPROCESS_ERROR |
| 951 | 推理错误  | MODEL_INFERENCE_ERROR |
| 952 | 后处理错误  | POSTPROCESS_ERROR |

## 其他
### 请求方信息结构
* 结构：系统-设备-设备号-运行环境容器-版本
* 示例：taihang/taihang_boss-iOS-UUID-MobileBrowser-2.8.20.1495017
* 枚举
  * 设备：Android iOS Pc
  * 运行环境容器：MobileBrowser(手机浏览器), WXBrowser(手机微信浏览器), APP(客户端)]

### 分页
* 输入

| 名称 | 字段 | 类型 | 必须 | 说明 |
| ---- | -- | -- | -- | -- |
| 页号 | page | int | Y | 从1开始，默认是1 |
| 每页个数 | pageSize | int | Y | 默认是10，默认是10，0是所有 |

* 输出

| 名称 | 字段 | 类型 | 必须 | 说明 |
| ---- | -- | -- | -- | -- |
| 总个数 | total | int | Y |  |
| 总页数 | pages | int | Y |  |
| 数据列表 | list | array | Y |  |

### 提交接口设计
* 实体及其数组属性(如我的地址)都使用本方案

| 操作 | ID | 提交数据 |
| ---- | ---- | ---- |
| 新增 | 无 | 有 |
| 修改 | 有 | 增量(修改部分)，全量(时间戳) |
| 删除 | 有 | 无 |

* 增量修改：如修改期间有其他人修改了同一个属性，则会提示确认。
```Java
update(老数据, 增量新数据, 强制修改) {
    if (!强制修改 && 当前数据 != 老数据) // 不强制修改 && 数据有改变
      return "数据有调整(当前数据, 老数据, 增量新数据)，确定修改吗？"

    修改成新数据
}
```

* 全量修改：基于实体时间戳，如修改期间有其他人修改了同一个实体，则会提示确认。
```Java
update(老数据.时间戳, 全量新数据, 强制修改) {
    if (!强制修改 && 当前数据.时间戳 != 老数据.时间戳) // 不强制修改 && 数据时间戳有改变
      return "数据有调整(当前数据, 老数据, 全量新数据)，确定修改吗？"

    修改成新数据，同时更新数据时间戳
}
```
