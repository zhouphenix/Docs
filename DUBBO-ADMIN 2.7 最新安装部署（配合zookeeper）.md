## DUBBO-ADMIN 2.7 最新安装部署（配合zookeeper）

[toc]

参考： http://www.freesion.com/article/917946424/ 

### 1、下载最新地址 https://github.com/apache/dubbo-admin     

这里下载日期是2019-07-07，会有时间的不同访问的地址也不同。

![img](http://www.freesion.com/images/237/94b4c58845f26552d89e89419714c6c5.png)

 



### 2、下载解压后修配置文件 dubbo-admin-server/src/main/resources/application.properties

![img](http://www.freesion.com/images/667/265a59c473e1817bb677b8a6d10f9f2b.png)

配置文件修改zookeeper地址，dubbo控制台端口默认8080，

可以修改为其他端口例如 server.port=9898，以免与其他服务端口冲突。

**【注意】zookeeper的访问地址及端口，根据自己安装的修改。**

![img](http://www.freesion.com/images/187/df62fcacc4aab166161197c326c3fec3.png)

### 3、在主目录dubbo-admin-develop目录下，执行 mvn clean package

（注意：刚开始安装很多版本都是在dubbo-admin-develop/dubbo-admin-server 目录下执行打包命令，更换各种版本无果从官网获得正确的安装方式），官网解释如下，还是在下载源码的网页下，有文档说明。---------踩过坑所以记录下！

![img](http://www.freesion.com/images/325/bfc4edfbd4a9cf2dd89bd544649602ad.png)

### 4、启动方式

一种方法启动 ：执行

```shell
mvn --projects dubbo-admin-server spring-boot:run 
```

   二种方法启动：

```shell
cd dubbo-admin-distribution/targetjava -jar dubbo-admin-0.1.jar
```

### 5、浏览器输入网址：[http://localhost:9898](http://localhost:9898/)

![img](http://www.freesion.com/images/303/d475adca52b429e46b41f131f7fae41f.png)

 