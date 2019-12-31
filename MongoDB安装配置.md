## MongoDB安装配置

[toc]

### 一、下载并安装配置

#### 1.1 MongoDB 下载

[MongoDB 下载](https://www.mongodb.com/download-center/community?jmp=nav)

### ![在这里插入图片描述](E:\WONI\Git\Docs\images\mongodb_down_url)

#### 1.2 安装

##### 1.2.1 开始安装

![在这里插入图片描述](E:\WONI\Git\Docs\images\mongodb_install1)
![在这里插入图片描述](E:\WONI\Git\Docs\images\mongodb_install2)

##### 1.2.2 双击下载后的安装程序，选择“Complete”安装完整版本。这个过程非常简单，除了“下一步”就是最后的“完成”。

![在这里插入图片描述](E:\WONI\Git\Docs\images\mongodb_install3)

![在这里插入图片描述](E:\WONI\Git\Docs\images\mongodb_install4)
![在这里插入图片描述](E:\WONI\Git\Docs\images\mongodb_install5)
安装好以后接下来是配置

#### 1.3 配置

3.1 创建D:\mongodb\data\log目录，用来存放日志文件；
3.2 在D:\mongodb\data\log目录里新建mongodb.log，用来存放日志信息；
3.3 创建D:\mongodb\data\db目录，用来存放数据库数据，
3.4 并在D:\mongodb目录下创建mongo.config，在文件内部复制如下文本：

```
##数据文件  此处=后对应到数据所存放的目录
dbpath=d:\mongodb\data\db
##日志文件  此处=后对应到日志文件所在路径
logpath=d:\mongodb\data\log\mongodb.log
##错误日志采用追加模式，配置这个选项后mongodb的日志会追加到现有的日志文件，而不是从新创建一个新文件
logappend=true 
#启用日志文件，默认启用
journal=true 
#这个选项可以过滤掉一些无用的日志信息，若需要调试使用请设置为false
quiet=true 
#端口号 默认为27017
port=27017 
```

测试是否安装成功

 进入C:\Program Files\MongoDB\Server\3.4\bin文件夹下，点击mongod.exe，如果闪一下退出，说明安装正常 ![在这里插入图片描述](E:\WONI\Git\Docs\images\20190315183136516.png)

#### 1.4 安装服务

用管理员权限打开cmd命令行，输入如下命令安装mongodb服务

先进入C:\Program Files\MongoDB\Server\3.4\bin文件夹，使用如下命令： 

```
mongod --logpath "D:\mongodb\data\log\mongodb.log" --logappend --dbpath "D:\mongodb\data\db" --serviceName "MongoDB" --install 
```

在cmd.exe上输入services.msc打开服务管理器，找到MongoDB服务，设置成自动启动，并启动

如果启动不成功，先删除服务，使用如下命令： `sc delete MongoDB` 

#### 1.5.配置环境变量（可省略）

6.1如果不配置环境变量可进入C:\Program Files\MongoDB\Server\3.4\bin，然后把mongo.exe发送桌面作为快捷方式
6.2 还可以通过设置环境变量的方式，让mongo命令在所有文件夹内都可以访问
![在这里插入图片描述](E:\WONI\Git\Docs\images\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlbmd0aW5nWWFu,size_16,color_FFFFFF,t_70)

在系统变量中找到path,window7或window8双击打开后在变量值中的末尾增加
;C:\Program Files\MongoDB\Server\3.4\bin\配置成之后，可以在任何目录下去调用mongo命令，打开如下图：
![在这里插入图片描述](E:\WONI\Git\Docs\images\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlbmd0aW5nWWFu,size_16,color_FFFFFF,t_71)
注意：Window10 可新建一个选项，输入C:\Program Files\MongoDB\Server\3.4\bin即可！
![在这里插入图片描述](E:\WONI\Git\Docs\images\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlbmd0aW5nWWFu,size_16,color_FFFFFF,t_72)
![在这里插入图片描述](E:\WONI\Git\Docs\images\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlbmd0aW5nWWFu,size_16,color_FFFFFF,t_73)

### 二.推荐使用的图形化工具

Robo 3T 下载地址：
https://robomongo.org/
MongoBooster 下载地址：
http://www.softpedia.com/get/Internet/Servers/Database-Utils/MongoBooster.shtml
![在这里插入图片描述](E:\WONI\Git\Docs\images\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2Zlbmd0aW5nWWFu,size_16,color_FFFFFF,t_74)

### 三、命令

###  ![在这里插入图片描述](E:\WONI\Git\Docs\images\20190315185006104.png)

以下命令是必须掌握的： 

`mongo`  运行mongo db	
显示当前的数据库名称

`show dbs`	
显示当前服务器下数据库（非空的数据库）列表

`use test`	
如果test数据库不存在，则创建test数据库
如果test已存在，则切换到test数据库

`show collections`	
显示当前数据库下所包含的集合（表）列表

`db.users.insert({name:'zhangsha'})`	
向users集合中插入数据
如果users集合存在，则直接插入数据，如果不存在，则创建users集合再插入数据

`db.createCollection('products')`
创建一个空集合products

`db.products.insert([{name:'lishi'},{name:'wangwu'}])`		
一次插入多个数据

`db.products.find()`
查询products集合中所有的数据

`db.products.find({name:'苹果手机'})`
查询stu集合中name='苹果手机'的数据

`db.products.find({name:{$eq:'苹果手机'}})`
同上，$eq=>等号，建议使用上面的方式，易记，易输入
eq = equal

`db.products.find({price:{$gt:18}})`
查询stu集合中age>18的数据  

把$gt换成如下的符号试试：
`$gt`=>大于   great
`$gte`=>大于等于 great equal
`$lt`=>小于   less than
`$lte`=>小于等于 less than equal
`$ne`=>不等于  not equal
`$in`=>在范围内
`$nin`=>不在范围内
以上几个符号格式总结为：{ field: {符号: value}}

`db.products.find({name:/^华为/})`
查找stu集合中name域中以“华为”字符的开头的数据

`db.products.find({name:{$in:['手机1','手机2']}})`
查询stu集合中name='手机1'和name='手机2'的数据
`$in`=>在范围内
`$nin`=>不在范围内
以上两个符号格式为：{ field:{符号:[value1,value2,....]}}

`db.products.find({name:"华为手机",price:800})`
查找name="华为手机"并且price:800的数据

`db.products.find({$or:[{name:'华为手机'},{price:{$lt:1000}}]})`
查询products集合中name='华为手机' 或者 price<1000的数据
`$or`=>或者  注意$or:[{},{},....]
`$and`=>并且  格式同$or, 例：{$and:[{},{},....]}
`$nor`=>not or 与$or相反， 格式同$or

`db.products.find({price:{$not:{$gt:100}}})`
查询products集合中price<=100的数据，不存在price属性的数据也会查询出来
`$not`=>取反 

`db.products.find({price:{$exists: true}})`
查询products集合中包含域名称为price的数据

`db.products.find({name:{$type:2}})`
查询products集合中name属性为字符串类型的数据

```
db.products.find({
	$where: function(){
		return this.name == '华为手机'
	}
})
```


查询products集合中name='华为手机’的数据

```
db.products.find({
	$where: function(){
 		return  this.name.indexOf('华为手机') > -1;
	}
})
```


查询products集合中name域中包含“华为手机”字符的数据

```
db.products.update({name:'华为手机'},{$set:{price:2000}},{
	upsert: true,
	multi:false
})
```

把products集合中name='华为手机'的那条数据，把price属性设置成2000，其它属性保留
$set是指更改的属性列表，不在列表中其他属性会被保留，如果不加此符号，其它属性会被丢弃（_id属性比较特殊，不会丢失）
upsert:true如果没有符号条件的更新时，则插入一条，为false时，则不会插入, 默认是false
multi:false一次只能更新一条数据，为true时，可更新多条，默认是false

`db.students.remove({})`
清空集合students

`db.products.remove({name:'abc'})`
删除products集合中name='abc'的数据，注意，即使把集合products中的所有数据都删除了
products集合仍然存在， remove()是用来删除数据的，而drop()不仅会删除数据，还会把
集合的结构给删除

`db.products.drop()`
把stu集合彻底从当前数据中删除，集合stu不再存在，注意与remove()的区别

`db.dropDatabase()`
删除当前数据库

`db.users.distinct('name')`
查询users集合中不重复的name属性，返回的是数组

`db.stu.count({name:'zhangshan'})`
查询stu集合中name='zhangshan'的数据数量

`db.stu.find().limit(5)`
查询stu集合中前5条数据

`db.stu.find().skip(5)`
查询stu集合中跳过前5条后的数据

`db.stu.find().sort({name:1})`
查询stu集合中的全部数据，并按name属性正序排列  注：1：正序 -1: 倒序

由于mongodb的api接口方法很多，除以上命令外，其他的命令请多看官方文档
要求：根据官方文档中的方法原型，能够操作相应的方法

