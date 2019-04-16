# 通过Eclipse运行MyBatis Generator

## 安装Eclipse功能

eclipse功能能够通过以下任何途径安装

- 查询"MyBatis Generator" 在Eclipse marketplace 并且从marketplace正确的安装。你可以通过2种方式访问Eclipse marketplace：

1. 点击菜单选项 Help>Eclipse Marketplace...在一个正在运行的Eclipse实例。

去 https://marketplace.eclipse.org/

- 手动配置一个下载站点指向 https://dl.bintray.com/mybatis/mybatis-generator
- 从Github发布页面（https://github.com/mybatis/generator/releases）下载压缩的eclipse更新站点,解压，并且配置一个更新站点指向你的解压目录。

## 使用Eclipse功能

在eclipse环境中快速运行MyBatis Generator，参阅以下步骤：

1. 创建一个配置文件：
   1. File>New>Other...
   2. 从"Mybatis"类别选择“MyBatis Generator Configuration File”，点击“Next”
   3. 指定本地文件和文件名（默认为generatorConfig.xml）
   4. 结束向导
2. 适当地填写配置文件，最低限度，你必须指定：
   1. jdbcConnection 信息去指定如何连接目标数据库
   2. 为 javaModelGenerator 一个target package,和target project
   3. 为 sqlMapGenerator指定一个target package和target project
   4. 为 javaClientGenerator 指定一i个 target package和 target project 和 type。(如果你不想生成Java Clients 你可以移除 javaClientGenerator 元素)
   5. 至少一个 database table
3. 保存文件
4. 在eclipse向导右击配置文件，或者package explorer,view 和 点击菜单选项“Run As>Run Mybatis Generator”

重要提示：在eclipse中MyBatis Generator 不会覆盖你对其生成的对象所做的任何自定义改变。你可以反复运行它，而不必担心丢失自定义更改。