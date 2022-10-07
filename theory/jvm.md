# JVM
1. [JVM运行时数据区(Run-TimeDataAreas)及内存结构](https://www.cnblogs.com/wuzhenzhao/p/12346515.html)
1. [JVM的底层实现原理](https://blog.csdn.net/fangqun663775/article/details/54572635)
1. [Java JVM 运行机制及基本原理](https://zhuanlan.zhihu.com/p/25713880)
1. [高手教大家如何配置JVM参数](http://developer.51cto.com/art/200907/135160.htm)
1. minor GC : Eden的存活对象拷贝到某个Survivor Space, 当Survivor Space空间满了后, 剩下的live对象就直接拷贝到老一代中。每次GC后，Eden内存块会被清空。
1. JVM命令执行的工作原理
```
C/C++的工作原理：先将语句转化为汇编，再把汇编转换为二进制命令传给CPU
Java：编译成.class文件（字节码文件），JVM把字节码文件解析成汇编和二进制命令。
```
1. [字节码](https://juejin.im/post/6844903588716609543)
