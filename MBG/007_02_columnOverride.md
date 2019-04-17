# <columnOverride>元素（标签）

MyBatis Generator(MBG) 使用 <columnOverride>元素从默认计算的更改内省数据库列的某些属性。这个元素是<table>元素的可选子元素。

## 必需属性

| 属性   | 描述              |
| ------ | ----------------- |
| column | introspected 列名 |

## 可选属性

| 属性     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| property | 要使用的java属性名称，如果没有指定，MBG将基于列名生成属性名。例如，如果一张表有一个列名叫做“STRT_DTE”字段，然后基于“useActualColumnNames”属性的值，MBG将生成属性名“STRT_DTE”或者“strtDte”，（更多信息请参阅<table>元素的描述）。此属性可用于重命名列“startDate” |
|          |                                                              |
|          |                                                              |
|          |                                                              |
|          |                                                              |
|          |                                                              |

