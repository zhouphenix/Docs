# idea_java_gradle配置打包可执行jar

[TOC]

#### 目录

##### 1.新建java-gradle工程

略...

##### 2.配置入口main类， 以及main方法

略...

##### 3.配置build.gradle 

```
plugins {
    id 'java'
    id 'application' // 可执行
}
//...
mainClassName = 'com.xx.Main' //配置主类
```

##### 4.配置Artifacts 打包jar

###### 4.1 Project Structure > add jar

![Add jar](RES/15669004041553.png)



###### 4.2 create jar

![Create JAR from Modules](RES/15669008043731.png)

之后会生成META-INF文件

![生成META-INF文件](RES/15669012783050.png)

###### 4.3 build jar

Build菜单 > Build Artifacts... >Action 

之后就会在

![生成JAR](RES/1566901388-1.jpg)

###### 4.4 测试jar

dos命令 ` java -jar jar绝对路径`



















