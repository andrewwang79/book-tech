# dubbo

## dubbo-admin部署
1. 下载[incubator-dubbo-2.5.x.zip](https://github.com/apache/incubator-dubbo/tree/2.5.x)，解压拷贝到服务器
1. 进入目录dubbo-admin编译："mvn package -Dmaven.skip.test=true"
1. 解压生成的war包
1. 修改zookeeper和账号密码：编辑"dubbo-admin-2.5.10/WEB-INF/dubbo.properties"
1. 将其用tomcat启动，推荐用docker
1. 密码设置：WEB-INF/dubbo.properties
