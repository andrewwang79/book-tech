# 通用测试工具

| 技术 | 采用 | 说明 |
| :----: | ---- | ---- |
| 集成/系统测试 | PyTest | 使用了第三方selenium(web)和pywinauto(Windows客户端) |
| 接口测试 | PyTest |  |
| 性能/压力测试 | JMeter |  |

## jmeter
### 使用流程
1. 在Windows上将计划保存成jmx文件，如a1.jmx
1. 下载jmeter解压到linux的指定目录
  1. wget https://mirrors.tuna.tsinghua.edu.cn/apache//jmeter/binaries/apache-jmeter-5.2.1.tgz && tar -zxvf apache-jmeter-5.2.1.tgz && rm apache-jmeter-5.2.1.tgz
  1. mkdir -p /usr/local/jmeter/apache-jmeter-5.2.1 && mv apache-jmeter-5.2.1 /usr/local/jmeter/
1. /usr/local/jmeter/apache-jmeter-5.2.1/bin/jmeter.sh -n -t a1.jmx

### 资料
1. [jmeter集群](https://my.oschina.net/u/1241970/blog/635507)

## Postman
1. [Postman](https://blog.csdn.net/u012453843/article/details/78537040)
