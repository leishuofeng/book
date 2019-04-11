# XML 配置参考

在大多数公共的使用情况，MyBatis Generator(MBG) 都是通过一个XML配置文件驱动。这个配置文件告诉 MBG:

- ​       如何连接到数据库
- ​       生成什么对象和如何生成他们
- ​       什么表应该被使用来生成对象

以下是一个MBG 配置文件的例子，有关元素和属性的值的更多信息，请看每一个元素的单独的页面。

```xml
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE generatorConfiguration  
  PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"  
  "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">  
  
<generatorConfiguration>  
  <classPathEntry location="/Program Files/IBM/SQLLIB/java/db2java.zip" />  
  
  <context id="DB2Tables" targetRuntime="MyBatis3">  
    <jdbcConnection driverClass="COM.ibm.db2.jdbc.app.DB2Driver"  
        connectionURL="jdbc:db2:TEST"  
        userId="db2admin"  
        password="db2admin">  
    </jdbcConnection>  
  
    <javaTypeResolver >  
      <property name="forceBigDecimals" value="false" />  
    </javaTypeResolver>  
  
    <javaModelGenerator targetPackage="test.model" targetProject="\MBGTestProject\src">  
      <property name="enableSubPackages" value="true" />  
      <property name="trimStrings" value="true" />  
    </javaModelGenerator>  
  
    <sqlMapGenerator targetPackage="test.xml"  targetProject="\MBGTestProject\src">  
      <property name="enableSubPackages" value="true" />  
    </sqlMapGenerator>  
  
    <javaClientGenerator type="XMLMAPPER" targetPackage="test.dao"  targetProject="\MBGTestProject\src">  
      <property name="enableSubPackages" value="true" />  
    </javaClientGenerator>  
  
    <table schema="DB2ADMIN" tableName="ALLTYPES" domainObjectName="Customer" >  
      <property name="useActualColumnNames" value="true"/>  
      <generatedKey column="ID" sqlStatement="DB2" identity="true" />  
      <columnOverride column="DATE_FIELD" property="startDate" />  
      <ignoreColumn column="FRED" />  
      <columnOverride column="LONG_VARCHAR_FIELD" jdbcType="VARCHAR" />  
    </table>  
  
  </context>  
</generatorConfiguration>  
```

以下是这个文件的重点注释：

- 该文件制定 legacy db2 cli 驱动将被使用来连接数据库，同时也制定驱动在那里能被找到

- java Type Resolver不应该强制使用 BigDecimal 字段- 这意味如果可能，将替换整数类型(短、整数、长等)。这个特征试图让数据库 DECIMAL 和 NUMERIC 列更容易被处理。

- Java model generator 应该使用子包，意思是在上面的案例中生成模型对象将被放置在包名叫做 **test.model.db2admin** （因为该表位于DB2admin模式中），如果 enableSubPackages 属性设置为 false , 包将会是 **test.model**. Java model generator也应该 trim strings. 这意味着任何String属性的setter都将调用trim函数 - 如果你的数据库在字符列可能返回空白字符这是非常有用的。

- SQL Map generator 应该使用子包，这意味着在上面的案列中生成的XML文件将被放置在包名叫做 **test.xml.db2admin**（因为该表位于DB2admin模式中). 如果 enableSubPackages 属性被设置为 false, 包会是 **test.xml**

- DAO generator 应该使用子包，这意味着在上面的案列中生成的DAO类将被放置在包名叫做 **test.dao.db2admin** 中（因为该表位于DB2admin模式中)。如果 enableSubPackages 属性被设置为 false，包会是 **test.dao**。DAO generator 会参照mybatis xml 配置文件生成 mapper 接口。

- 该文件指定一个表将被内省，但是可以指定更多的表。有关指定表的重要说明包括：

  - 生成的对象将基于Customer（CustomerKey,Customer,CustomerMapper等等）而不是表名。
  - 实际上列名将被当做属性名。如果这个属性被设置为false(或者是没有指定)， MBG将会尝试驼峰规则将列名翻译为属性名。在任一情况下，属性名可以通过<columnOverride> 元素重写。
  - 该列具有生成的密钥，它是标识列，数据库类型是DB2。 这将导致MBG在生成的<insert>语句中生成正确的<selectKey>元素，以便可以返回新生成的密钥（使用DB2特定的SQL）。
  - DATE_FIELD 列将被映射成一个叫做startDate的属性。这将覆盖在本列中 DATE_FIELD 的默认属性。或者 dateField 如果 userActualColmunNames 属性被设置为false.
  - fred 列将被忽略， 没有 sql 会列出这个字段，并且没有Java属性将被生成。
  - LONG_VARCHAR_FIELD 列将被当做 VARCHAR字段而不管实际数据类型。

  ​	