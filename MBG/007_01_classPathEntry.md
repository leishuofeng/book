# <classPathEntry> 元素（标签）

<classPathEntry>元素用于将类路径位置添加到MyBatis Generator（MBG）运行的类路径中。 <classPathEntry>元素是<generatorConfiguration>元素的选项子元素。 MBG在这些实例中从这些位置加载类：

- 当为数据库 introspection 加载JDBC驱动.
- 在JavaModelGenerator中加载根类以检查重写方法时

**重要提醒**：在加载扩展MBG类之一或实现MBG接口之一的类时，不使用这些位置。在这些情况下，您必须将外部类添加到运行时类路径中，方法与将MBG添加到类路径中的方式相同（例如，使用java命令的-cp参数）。

## 必须的参数

| 属性     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| location | 添加到classpath下的 JAR/ZIP的完整路径，或者添加到classpath中的目录 |

## Optional Attributes

None

## Child Elements

None

## Example

这个元素指定一个DB2 JDBC驱动的位置

```xml
<classPathEntry location="/Program Files/IBM/SQLLIB/java/db2java.zip" />
```

