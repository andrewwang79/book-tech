# 分库分表
* [分库分表：中间件最全方案对比](https://zhuanlan.zhihu.com/p/375072815)

## 3个问题
1. 事务一致性：比如更新10张表，最后一张失败，怎样保证事务。
1. 字典表问题：一般字典表维护在一个库中，分库查询的话影响效率，每个库都存储一份字典表的话，上面提到的事务一致性问题又会出现。库之间也会过于冗余。
1. 分页查询：比如查询100到110之间的数据，做法可不是每个库取100-110间的数据，再去前10条，而是每个库查询0-110间的数据，比如10个库，就会返回 10 * 110条数据，再从这里取100~110间的数据。这里的问题就是如果是 500000-500010的话，返回的数据量就太大了。
