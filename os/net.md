# 网络知识

## 资料
* [OSI七层模型与TCP/IP四层模型](https://blog.csdn.net/qq_39521554/article/details/79894501)
![](../s/os/net.jpg)
* [互联网通讯原理](https://segmentfault.com/a/1190000023316912)
  * 核心概念是交换和路由
  * 路由：请求通过路由表跳跃到下个点，路由算法会动态维护网络拓扑
  * 通过自治系统简化网络复杂度，本质是多层网络，可以简化路由表和路由算法。
* [ip段和掩码说明，如24](http://www.nocidc.com/News/New-96.html)
* Socket的四个构成：服务端地址、服务端端口、客户端地址、客户端端口。1台服务器可以同时支持远超65536个socket/请求

## 协议
* [传输协议](https://www.cnblogs.com/xgqfrms/p/4999202.html)
* [SCP和SFTP](https://www.jianshu.com/p/3adcce4e2661):SCP基于SSH，默认加密是“AES-128”
* [SSH](https://zh.m.wikipedia.org/zh-hans/Secure_Shell)
  1. Secure Shell（安全外壳协议），不是SSL。
  1. 加密的网络传输协议，可在不安全的网络中为网络服务提供安全的传输环境
  1. 以非对称加密实现身份验证

### HTTP协议
### 服务异常场景
| 场景 | HTTP状态码 | 说明 |
| :-: | - | - |
| 客户端无网络 | 无 |  |
| web服务(nginx)停止 && API服务停止 | 无 |  |
| web服务(nginx)运行 && API服务停止 | 502 |  |
| web服务(nginx) && API服务运行 && API服务处理异常 | 500 |  |

## 网络代理

### 代理机制
| 方式 | 原理 | 网络层级 | 说明 |
| :-: | - | - | - |
| HTTP代理 | HTTP代理 | HTTP层 | Squid(通用转发)，Nginx(定向转发，需设置所需规则) |
| IP路由转发 | 网关gateway | TCP/IP层 | [iptables之NAT代理-内网访问外网](https://www.cnblogs.com/freeblogs/p/7788804.html) |

### 代理方式
| 模式 | 原理 | 代理机制 | 使用场景 |
| :-: | - | - | - |
| 正向代理forward proxy | 代理和客户端同属一个LAN，对服务端透明。发送透明 | HTTP代理 | 客户机在浏览器或软件上配置代理服务器 |
| 透明代理transparent proxy | 拦截客户端发送的请求 | HTTP代理+IP路由转发 | 客户机用代理服务器IP配置网关 |
| 反向代理 | 代理和服务端同属一个LAN，对客户端透明。接收透明 | HTTP代理 |  |

### 资料
* [代理原理介绍](https://laravelacademy.org/post/9336), https://www.cnblogs.com/f-ck-need-u/p/9739870.html
* 正向代理和透明代理的区别: 本质都是找到代理服务。前者通过人肉配置代理服务，后者通过网关自动接收且重定向到代理服务
  * 正向代理时，客户端明确指明请求要交给正向代理服务，也就是说要设置代理。而透明代理对客户端是透明的，客户端不知道更不用设置透明代理，但是客户端发出去的请求都会被透明代理拦截。
  * 正向代理为了实现某些额外的需求，有可能会修改请求报文，但按照RFC文档的要求，透明代理不会修改请求报文。
  * 正向代理可以内网也可以外网，但透明代理都是内网。
* [socks代理协议](https://wiyi.org/socks5-protocol-in-deep.html) : 网络传输协议，主要用于客户端与外网服务器之间通讯的中间传递。全称是Socket Secure。
## 长连接
### 理解
* Socket和WebSocket，不是RPC模式(请求响应模式)。本质上用于通知和请求。
* 有两种场景
  1. 无需返回结果的通知：请求
  1. 需返回结果的请求：请求，请求结果(异步返回)。
* 请求和请求结果必须要有唯一对应的key，可以异步处理。比如pos机的流水号。
* http模式(API)本质是一次短连接，也是异步返回请求结果，只是这个返回结果无需做key关联，因为当前连接只有一个请求。

#### 为何要有心跳来保活
* TCP本身有心跳包机制(SO_KEEPALIVE，默认2小时)。但是检查不到以下情况：
  1. 机器断电、网线拔出、防火墙断线。
  1. 中间节点（如防火墙）自动把一定时间之内没有数据交互的连接给断掉。

## Websocket
### 资料
* Websocket是socket，也可以支持N个。如使用了nginx作为代理，则因为nginx作为remoteIp只有1个，导致websocket连接数最多六万多，如果是一台服务器则要除2
* [看完让你彻底搞懂Websocket原理](http://blog.csdn.net/frank_good/article/details/50856585)
* [websocket知识](https://www.ruanyifeng.com/blog/2017/05/websocket.html)
* [WebSocket与TCP、Http的关系](http://blog.csdn.net/linwei_1029/article/details/47836249)
  * WebSocket协议是一个独立的基于TCP的协议。它与HTTP唯一的关系是它的握手是由HTTP服务器解释为一个Upgrade请求。
  * 发起连接是http，传输是tcp，所以要开TCP的80端口

### 规模
* [Netty-WebSocket长连接推送服务](http://blog.csdn.net/z69183787/article/details/52505249)
* [Websocket推送中心(三)-单机100W连接(C1000K)达成](https://shibd.github.io/2019/08/17/Message-Center-3/)
