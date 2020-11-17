# Spark

## 介绍
1. 由Scala写成

## 原理
1. 迭代数据可以保存在内存

## 体系
![](http://spark.apache.org/images/spark-stack.png)

## Spark Streaming(批处理)
![](http://img.ptcms.csdn.net/article/201503/09/54fcc92668e64.jpg)

## 实例
Word Count
```
JavaRDD<String> textFile = sc.textFile("hdfs://...");
JavaPairRDD<String, Integer> counts = textFile
    .flatMap(s -> Arrays.asList(s.split(" ")).iterator())
    .mapToPair(word -> new Tuple2<>(word, 1))
    .reduceByKey((a, b) -> a + b);
counts.saveAsTextFile("hdfs://...");
```
http://spark.apache.org/examples.html

## 资料
* [官网](http://spark.apache.org/)
* [ccblog](http://www.ccblog.cn/contentTag.htm?tag_id=101)
* [Spark的Java API例子详解](https://www.cnblogs.com/itboys/p/6674132.html)
* [spark java 示例代码wordcount](https://www.cnblogs.com/brainstorm/p/7909739.html)
* [内存有限的情况下Spark如何处理T级别的数据](https://www.zhihu.com/question/23079001)
* [第三篇：一个Spark推荐系统引擎的实现](https://www.cnblogs.com/muchen/p/6882465.html)
* [spark的UI界面](http://blog.csdn.net/u013013024/article/details/73498508)
