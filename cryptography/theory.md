# 理论原理
## 算法
* [DES，3DES,AES这三种对称密钥的区别与联系](https://www.cnblogs.com/ttss/p/4279757.html)
* [RSA与AES混合加密算法的实现](https://blog.csdn.net/jkxqj/article/details/25228707)
* [私钥签名，公钥验签](https://www.jianshu.com/p/3331467d139f)
  * 加签名是为了防止传输过程中篡改。比如信息被恶意公钥解密然后公钥加密，接收方验证是失败的【因为没有私钥】。
  * 签名=加密(秘钥, 摘要算法(信息))
  * 接收方验证：解密(公钥，签名)==摘要算法(信息)

## 场景
* 签名
* 数据安全
