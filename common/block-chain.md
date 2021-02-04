# 区块链

## 介绍
1. 区块链的主要作用是储存信息。任何需要保存的信息，都可以写入区块链，也可以从里面读取，所以它是数据库。
1. 任何人都可以架设服务器，加入区块链网络，成为一个节点。区块链的世界里面，没有中心节点，每个节点都是平等的，都保存着整个数据库。你可以向任何一个节点，写入/读取数据，因为所有节点最后都会同步，保证区块链一致。

## 原理机制
* 区块链技术是指通过去中心化和去信任的方式集体维护一个可靠数据库的技术
* 本质是去中心化(去中介)，原理是一串使用密码学相关联所产生的数据块。
* 4个关键词：去中心化（Decentralized）、去信任（Trustless）、集体维护（Collectively maintain）、可靠数据库（Reliable Database）。
* 如比特币的每一个数据块中包含了多次比特币网络交易有效确认的信息。

## 应用
### 原则
1. 不存在所有成员都信任的管理当局
1. 写入的数据不要求实时使用
1. 挖矿的收益能够弥补本身的成本

### 场景
1. 数字资产（数字货币）、数字货币交易平台
1. 智能合约、数字票据、权益证明
1. 征信
1. 政务服务
1. 电子病历

## 共识机制
* 区块链的共识机制基于计算能力(POW)
* [POW,POS,DPOS,PBFT](http://blog.csdn.net/lsttoy/article/details/61624287)
* https://www.zhihu.com/question/55794026/answer/146667857

## QA
### 节点接入群(peers)，原理同P2P
* 种子节点：使用多个DNS服务器（节点专用）来解析节点的IP。可以在代码里固化一个域名数组和IP地址数组，程序启动的时候就去连这些域名和IP。
* 节点引荐：如果不知道DNS，则必须知道至少一个节点的IP。

### 数据可信
#### 随意写入(新增)数据
* 通过创世区块link保证是有连续性的(交易)
* 通过区块hash计算(挖矿)保证新增的是有依据的

#### 修改删除数据
* HASH算法保证无法篡改

#### 区块能被替换吗？
* 可能，当这个人的计算能力超过网络的50%
* 区块不是绝对的确认，如果有人从一开始就计算(确保计算能力)，可以换掉所有的区块

#### 区块何时生效
* 新节点总是采用最长的那条区块链。如果区块链有分叉，将看哪个分支在分叉点后面，先达到6个新区块（称为"六次确认"）。按照10分钟一个区块计算，一小时就可以确认。

## 参考
### 资料
* [区块链是什么鬼？一文看懂区块链挖矿&记账原理](https://wenku.baidu.com/view/bc1edcc7f9c75fbfc77da26925c52cc58bd6907d.html)
* https://github.com/LiuBoyu/blockchain
* http://www.ruanyifeng.com/blog/2017/12/blockchain-tutorial.html
* [DPoS](https://steemit.com/dpos/@legendx/dpos)
* [Nodejs开发加密货币](http://bitcoin-on-nodejs.ebookchain.org/)
* [分布式账本系统](http://www.cnblogs.com/aberic/tag/Hyperledger/)：记录、管理和同步传统金融机构间的「金融合约」

### 系统和代码
* [Hyperledger](http://www.hyperledger.org/)
* https://github.com/littleredhat1997/CrowdFunding

### 产品
* http://www.onchain.com/
