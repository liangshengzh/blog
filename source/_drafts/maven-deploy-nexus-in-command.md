title: Maven命令发布项目到Nexus
date: 2016-03-02 22:04:30
tags:
- Java
- Maven
- Nexus
---

通常我们需要把项目发布到Nexus服务器供人下载时， 我们需要在项目到POM文件或者父POM文件中添加distributionManagement来制定我们的repo地址。在用户的settings.xml中配置server的用户名和密码相关信息。
``` xml
...
```
然后运行maven deploy命令即可把当前项目发布到Nexus服务器。

今天遇到的场景时这样的， 需要一个项目发布到nexus服务器， 而有不想改动现有项目的POM文件。可以在运行mvn deploy命令是加上如下参数来把项目发布到nexus。

``` bash
mvn deploy -D...
```
