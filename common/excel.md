# excel

## 使用
* =VLOOKUP(A1, 'sheetX'!$A$1:$B$10000, 2, False) // 按照A1去精确匹配range('sheetX'!$A$1:$B$10000)的第1列(默认，无法配置)，显示range的第2列

## Excel计算时间差（精确到分钟、秒）
* 设置单元格格式为常规，时间形式为“2017-9-28 18:14:49”
* 精确到分钟:ABS(J1-K1)*1440 或者INT(K1-J1)*1440
* 精确到秒:ABS(J1-K1)*1440*60

## 透视图表
* https://www.zhihu.com/question/22484899
* https://www.jianshu.com/p/23c8984f7cc7
* [公式.xlsx](https://tech.wangyaqi.cn/s/excel/公式.xlsx)
