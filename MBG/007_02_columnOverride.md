# <columnOverride>元素（标签）

MyBatis Generator(MBG) 使用 <columnOverride>元素从默认计算的更改内省数据库列的某些属性。这个元素是<table>元素的可选子元素。

## 必需属性

| 属性   | 描述              |
| ------ | ----------------- |
| column | introspected 列名 |

## 可选属性

| 属性                | 描述                                                         |
| ------------------- | ------------------------------------------------------------ |
| property            | 要使用的java属性名称，如果没有指定，MBG将基于列名生成属性名。例如，如果一张表有一个列名叫做“STRT_DTE”字段，然后基于“useActualColumnNames”属性的值，MBG将生成属性名“STRT_DTE”或者“strtDte”，（更多信息请参阅<table>元素的描述）。此属性可用于重命名列“startDate” |
| javaType            | 此列的属性的完全限定Java类型。如果需要,这可以被用做覆盖通过`JavaTypeResolverj`计算出来的类型。对于一些数据库，这是处理“奇数”数据库类型所必需的(例如：MySql的 无符号 bigint 类型 应该被映射为 java.lang.Object)。 |
| jdbcType            | 列的JDBC类型（INTEGER,DECIMAL,NUMERIC,VARCHAR,等等。如果需要，这个能够被用来覆盖通过`JavaTypeResolver`计算出来的类型。 对于某些数据库，处理JDBC怪癖这是必须的 。（例如：DB2的 `LONGVARCHAR`类型对于`iBATIS`应该被映射成VARCHAR ） |
| typeHandler         | 应该用于此列的用户定义的类型处理程序。这应该一个实现了iBATIS' `TypeHandler` or `TypeHandlerCallback`接口的类的全限定路径类名（`TypeHandlerCallback`更容易实现）。如果没有指定，或者是空，iBATIS将使用默认类型工具来处理类型。**重要：**MBG没有验证type handler是否存在，或者是否有效。MBG只是将此值插入生成的SQL Map配置文件中的适当位置。 |
| delimitedColumnName |                                                              |
| isGeneratedAlway    | 指定在数据库中，此列是否是一个 GENERATED ALWAYS 列。如果这列是 |

