# 网络知识
* [互联网通讯原理](https://segmentfault.com/a/1190000023316912)
  * 核心概念是交换和路由
  * 路由：请求通过路由表跳跃到下个点，路由算法会动态维护网络拓扑
  * 通过自治系统简化网络复杂度，本质是多层网络，可以简化路由表和路由算法。
* [ip段和掩码说明，如24](http://www.nocidc.com/News/New-96.html)

# 长连接
## 理解
* Socket和WebSocket，不是RPC模式(请求响应模式)。本质上用于通知和请求。
* 有两种场景：
  1. 无需返回结果的通知：请求
  1. 需返回结果的请求：请求，请求结果(异步返回)。
* 请求和请求结果必须要有唯一对应的key，可以异步处理。比如pos机的流水号。
* http模式(API)本质是一次短连接，也是异步返回请求结果，只是这个返回结果无需做key关联，因为当前连接只有一个请求。

## Socket
* Socket的四个构成：服务端地址、服务端端口、客户端地址、客户端端口。1台服务器可以同时支持远超65536个socket/请求

## Websocket
### 资料
* Websocket是socket，也可以支持N个。如使用了nginx作为代理，则因为nginx作为remoteIp只有1个，导致websocket连接数最多六万多
* [看完让你彻底搞懂Websocket原理](http://blog.csdn.net/frank_good/article/details/50856585)
* [websocket知识](https://www.ruanyifeng.com/blog/2017/05/websocket.html)
* [WebSocket与TCP、Http的关系](http://blog.csdn.net/linwei_1029/article/details/47836249)
  * WebSocket协议是一个独立的基于TCP的协议。它与HTTP唯一的关系是它的握手是由HTTP服务器解释为一个Upgrade请求。
  * 发起连接是http，传输是tcp，所以要开TCP的80端口
### 规模
* [Netty-WebSocket长连接推送服务](http://blog.csdn.net/z69183787/article/details/52505249)
* [Websocket推送中心(三)-单机100W连接(C1000K)达成](https://shibd.github.io/2019/08/17/Message-Center-3/)
