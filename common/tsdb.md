# 时间序列数据库
* [时间序列数据库(TSDB)初识与选择(InfluxDB、OpenTSDB、Druid、Elasticsearch对比)](https://www.cnblogs.com/WeaRang/p/12421842.html)
* [LSM-Tree](https://cloud.tencent.com/developer/article/1441835)
* [LSM 算法的原理是什么？](https://www.zhihu.com/question/19887265)

## InfluxDB
* InfluxDB里存储的数据被称为时间序列数据，其包含一个数值，就像CPU的load值或是温度值类似的。时序数据有零个或多个数据点，每一个都是一个指标值。
  * time(一个时间戳) 【类比SQL中的主键】
  * measurement(例如cpu_load) 【可以理解为SQL中的table】
  * 至少一个k-v格式的field(也即指标的数值例如 “value=0.64”或者“temperature=21.2”) 【类比SQL中的列】
  * 零个或多个tag，其一般是对于这个指标值的元数据(例如“host=server01”, “region=EMEA”, “dc=Frankfurt)。【可以理解为列，与field不同的是，tag理解为一个对象，例如server01的主机温度为21.2。并且tag是被索引起来的】
* 理解：n多指标表，时间是key，有1个value，还有n个自定义属性
