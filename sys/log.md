# 系统日志

## 大中规模系统
用logstash之类的

## 小规模系统
用Jenkins创建日志查询任务，执行即可查看。配置步骤
  1. 启用jenkins账号的bash(centos特有操作)
  1. 切换账号：su jenkins
  1. 配置ssh的config：加入日志服务器的IP和账号
  1. jenkins账号免登录ssh(日志服务器)

## 资料
* [利用ssh和tail实时监控应用日志](http://blog.csdn.net/u011355981/article/details/49001877)

# 用户行为
## 记录
通过MQ转存，周期性数据(如用户每天的使用记录)通过Redis(不要用DB)判断是否已记录
* 不影响业务流程
* 并行成串行

```
userLog = get UserLog
if (userLog.type.IS_PERIOD() && userLog.IS_RECORD()) {
  return;
}

record(userLog);
```
