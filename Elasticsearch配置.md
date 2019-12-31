## Elasticsearch配置

[toc]

### 一、准备

工具：

 [下载Elasticsearch（版本7.4.0）](https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.4.0-windows-x86_64.zip)

 [Kibana版本7.4.0 ( 访问Elasticsearch的客户端 )](https://artifacts.elastic.co/downloads/kibana/kibana-7.4.0-windows-x86_64.zip)

### 二、安装

1.Elasticsearch 免安装，解压之后拷贝到开发环境所在目录即可
2.安装中文分词插件 [下载地址](https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.4.0/elasticsearch-analysis-ik-7.4.0.zip)

```shell
D:\DEVELOPER\env\elasticsearch-7.4.0\bin>elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.4.0/elasticsearch-analysis-ik-7.4.0.zip
-> Downloading https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.4.0/elasticsearch-analysis-ik-7.4.0.zip
[=================================================] 100%??
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@     WARNING: plugin requires additional permissions     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
* java.net.SocketPermission * connect,resolve
See http://docs.oracle.com/javase/8/docs/technotes/guides/security/permissions.html
for descriptions of what these permissions allow and the associated risks.

Continue with installation? [y/N]y
-> Installed analysis-ik
```

3.运行bin目录下的elasticsearch.bat启动Elasticsearch 

4.Kibana免安装，解压之后拷贝到开发环境所在目录即可

5.运行bin目录下的kibana.bat，启动Kibana的用户界面 

6.访问[http://localhost:5601](http://localhost:5601/) 即可打开Kibana的用户界面 

 ![展示图片_30.png](E:\WONI\Git\Docs\images\展示图片_30) 

### 三、使用

