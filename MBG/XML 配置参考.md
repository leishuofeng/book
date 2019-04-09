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
- java 类型解析器不应该强制使用 BigDecimal 字段- 这意味如果可能，将替换整数类型(短、整数、长等)。
- 