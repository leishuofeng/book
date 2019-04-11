# 运行 MyBatis Generator

MyBatis Generator(MBG) 能够通过以下几种方法运行：

- 从XML配置的命令提示符

- XML配置作为一个 Ant 任务

- 作为Maven 插件

- 来自另一个具有XML配置的Java程序

- 来自另一个基于Java的配置的Java程序

- 作为Eclipse功能

  任何一个方法描述细节在关联的页面

  **注意：**还有对于MBG的Eclipse插件，添加了额外的功能-既很好的集成到Eclipse，支持Eclipse的Ant任务，并且支持自动合并Java文件。安装Eclipse插件信息，请参阅MyBatis网站。

  **重要：**在例如Eclipse之类的IDE环境之外运行时,MBG解释所有XML配置中的 targetProject 和 targetPackage 属性,如下所示：

  targetProject 假定是一个存在的目录结构。如果目录结构不存在MBG将失败。这个规则有一个列外-当MBG通过Maven插件运行时。在Maven中如何解析targetProject，详情请参阅Maven插件页面。

  targetPackage 将被转换targetProject目录结构的额合适子目录结构。如果有必要，MBG将创建这些子目录。