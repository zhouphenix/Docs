# MySQL 安装

[toc]



所有平台的 MySQL 下载地址为： [MySQL 下载](https://dev.mysql.com/downloads/mysql/) 。 挑选你需要的 *MySQL Community Server* 版本及对应的平台。

> **注意：**安装过程我们需要通过开启管理员权限来安装，否则会由于权限不足导致无法安装。

------

## Linux/UNIX 上安装 MySQL

Linux平台上推荐使用RPM包来安装Mysql,MySQL AB提供了以下RPM包的下载地址：

- **MySQL** - MySQL服务器。你需要该选项，除非你只想连接运行在另一台机器上的MySQL服务器。
- **MySQL-client** - MySQL 客户端程序，用于连接并操作Mysql服务器。
- **MySQL-devel** - 库和包含文件，如果你想要编译其它MySQL客户端，例如Perl模块，则需要安装该RPM包。
- **MySQL-shared** - 该软件包包含某些语言和应用程序需要动态装载的共享库(libmysqlclient.so*)，使用MySQL。
- **MySQL-bench** - MySQL数据库服务器的基准和性能测试工具。

安装前，我们可以检测系统是否自带安装 MySQL:

```
rpm -qa | grep mysql
```

如果你系统有安装，那可以选择进行卸载:

```
rpm -e mysql　　// 普通删除模式
rpm -e --nodeps mysql　　// 强力删除模式，如果使用上面命令删除时，提示有依赖的其它文件，则用该命令可以对其进行强力删除
```

**安装 MySQL：**

接下来我们在 Centos7 系统下使用 yum 命令安装 MySQL，需要注意的是 CentOS 7 版本中 MySQL数据库已从默认的程序列表中移除，所以在安装前我们需要先去官网下载 Yum 资源包，下载地址为：https://dev.mysql.com/downloads/repo/yum/

![img](https://www.runoob.com/wp-content/uploads/2014/03/repo-name-small.png)

```
wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm
rpm -ivh mysql-community-release-el7-5.noarch.rpm
yum update
yum install mysql-server
```

权限设置：

```
chown mysql:mysql -R /var/lib/mysql
```

初始化 MySQL：

```
mysqld --initialize
```

启动 MySQL：

```
systemctl start mysqld
```

查看 MySQL 运行状态：

```
systemctl status mysqld
```

**注意：**如果我们是第一次启动 mysql 服务，mysql 服务器首先会进行初始化的配置。

> 此外,你也可以使用 MariaDB 代替，MariaDB 数据库管理系统是 MySQL 的一个分支，主要由开源社区在维护，采用 GPL 授权许可。开发这个分支的原因之一是：甲骨文公司收购了 MySQL 后，有将 MySQL 闭源的潜在风险，因此社区采用分支的方式来避开这个风险。
>
> MariaDB的目的是完全兼容MySQL，包括API和命令行，使之能轻松成为MySQL的代替品。
>
> ```
> yum install mariadb-server mariadb 
> ```
>
> mariadb数据库的相关命令是：
>
> ```
> systemctl start mariadb  #启动MariaDB
> systemctl stop mariadb  #停止MariaDB
> systemctl restart mariadb  #重启MariaDB
> systemctl enable mariadb  #设置开机启动
> ```

------

## 验证 MySQL 安装

在成功安装 MySQL 后，一些基础表会表初始化，在服务器启动后，你可以通过简单的测试来验证 MySQL 是否工作正常。

使用 mysqladmin 工具来获取服务器状态：

使用 mysqladmin 命令来检查服务器的版本, 在 linux 上该二进制文件位于 /usr/bin 目录，在 Windows 上该二进制文件位于C:\mysql\bin 。

```
[root@host]# mysqladmin --version
```

linux上该命令将输出以下结果，该结果基于你的系统信息：

```
mysqladmin  Ver 8.23 Distrib 5.0.9-0, for redhat-linux-gnu on i386
```

如果以上命令执行后未输出任何信息，说明你的Mysql未安装成功。

------

## 使用 MySQL Client(Mysql客户端) 执行简单的SQL命令

你可以在 MySQL Client(Mysql客户端) 使用 mysql 命令连接到 MySQL 服务器上，默认情况下 MySQL 服务器的登录密码为空，所以本实例不需要输入密码。

命令如下：

```
[root@host]# mysql
```

以上命令执行后会输出 mysql>提示符，这说明你已经成功连接到Mysql服务器上，你可以在 mysql> 提示符执行SQL命令：

```
mysql> SHOW DATABASES;
+----------+
| Database |
+----------+
| mysql    |
| test     |
+----------+
2 rows in set (0.13 sec)
```

------

## Mysql安装后需要做的

Mysql安装成功后，默认的root用户密码为空，你可以使用以下命令来创建root用户的密码：

```
[root@host]# mysqladmin -u root password "new_password";
```

现在你可以通过以下命令来连接到Mysql服务器：

```
[root@host]# mysql -u root -p
Enter password:*******
```

**注意：**在输入密码时，密码是不会显示了，你正确输入即可。

------

## Windows 上安装 MySQL

Windows 上安装 MySQL 相对来说会较为简单，点击链接 https://cdn.mysql.com//Downloads/MySQL-8.0/mysql-8.0.11-winx64.zip 下载 zip 包。

最新版本可以在 [MySQL 下载](http://dev.mysql.com/downloads/mysql/) 中下载中查看。

![img](https://www.runoob.com/wp-content/uploads/2014/03/330405-20160709174318905-664331194.png)

![img](https://www.runoob.com/wp-content/uploads/2014/03/20DBD7BA-A653-4AE3-887E-2A16E6EBB2E3.png)

点击 **Download****No thanks, just start my download.**



![img](https://www.runoob.com/wp-content/uploads/2014/03/330405-20160709174941374-1821908969.png)

下载完后，我们将 zip 包解压到相应的目录，这里我将解压后的文件夹放在 **C:\web\mysql-8.0.11** 下。

**接下来我们需要配置下 MySQL 的配置文件**

打开刚刚解压的文件夹 **C:\web\mysql-8.0.11** ，在该文件夹下创建 **my.ini** 配置文件，编辑 **my.ini** 配置以下基本信息：

```
[client]
# 设置mysql客户端默认字符集
default-character-set=utf8
 
[mysqld]
# 设置3306端口
port = 3306
# 设置mysql的安装目录
basedir=C:\\web\\mysql-8.0.11
# 设置 mysql数据库的数据的存放目录，MySQL 8+ 不需要以下配置，系统自己生成即可，否则有可能报错
# datadir=C:\\web\\sqldata
# 允许最大连接数
max_connections=20
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
```

**接下来我们来启动下 MySQL 数据库：**

以管理员身份打开 cmd 命令行工具，切换目录：

```
cd C:\web\mysql-8.0.11\bin
```

初始化数据库：

```
mysqld --initialize --console
```

执行完成后，会输出 root 用户的初始默认密码，如：

```
...
2018-04-20T02:35:05.464644Z 5 [Note] [MY-010454] [Server] A temporary password is generated for root@localhost: APWCY5ws&hjQ
...
```

**APWCY5ws&hjQ** 就是初始密码，后续登录需要用到，你也可以在登陆后修改密码。

输入以下安装命令：

```
mysqld install
```

【注意】

* 提示`Install/Remove of the Service Denied!`， 需要以管理员身份运行**DOS**

* 提示

  ```
  mysqld : 无法将“mysqld”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保路径
  正确，然后再试一次。
  所在位置 行:1 字符: 1
  + mysqld install
  + ~~~~~~
      + CategoryInfo          : ObjectNotFound: (mysqld:String) [], CommandNotFoundException
      + FullyQualifiedErrorId : CommandNotFoundException
  ```

  表示无法识别`mysqld`命令， 需要指定执行文件

  ```
  PS D:\DEVELOPER\mysql-8.0.18-winx64\bin> .\mysqld.exe install
  Service successfully installed.
  ```

  

启动输入以下命令即可：

```
net start mysql
```

> 注意: 在 5.7 需要初始化 data 目录：
>
> ```
> cd C:\web\mysql-8.0.11\bin 
> mysqld --initialize-insecure 
> ```
>
> 初始化后再运行 net start mysql 即可启动 mysql。

------

## 登录 MySQL

当 MySQL 服务已经运行时, 我们可以通过 MySQL 自带的客户端工具登录到 MySQL 数据库中, 首先打开命令提示符, 输入以下格式的命名:

```
mysql -h 主机名 -u 用户名 -p
```

参数说明：

- **-h** : 指定客户端所要登录的 MySQL 主机名, 登录本机(localhost 或 127.0.0.1)该参数可以省略;
- **-u** : 登录的用户名;
- **-p** : 告诉服务器将会使用一个密码来登录, 如果所要登录的用户名密码为空, 可以忽略此选项。

如果我们要登录本机的 MySQL 数据库，只需要输入以下命令即可：

```
mysql -u root -p
# or  
.\mysql.exe -u root -p
```

按回车确认, 如果安装正确且 MySQL 正在运行, 会得到以下响应:

```
Enter password:
```

若密码存在(第一次键入初始化时生成的秘钥), 输入密码登录, 不存在则直接按回车登录。登录成功后你将会看到 Welcome to the MySQL monitor... 的提示语。

然后命令提示符会一直以 **mysq>** 加一个闪烁的光标等待命令的输入, 输入 **exit** 或 **quit** 退出登录。

【注意】第一次登陆之后需要马上修改密码，否则无法操作数据库

```
mysql> show databases;
ERROR 1820 (HY000): You must reset your password using ALTER USER statement before executing this statement.
```

解决办法
1、 修改用户密码
`mysql> alter user 'root'@'localhost' identified by 'youpassword';`  

## 局域网共享mysql

mysql8.0无法给用户授权或提示You are not allowed to create a user with GRANT的问题

提示意思是不能用grant创建用户，mysql8.0以前的版本可以使用grant在授权的时候隐式的创建用户，8.0以后已经不支持，所以必须先创建用户，然后再授权，命令如下：

```
mysql> CREATE USER 'root'@'%' IDENTIFIED BY 'Hadoop3!';
Query OK, 0 rows affected (0.04 sec)

mysql> grant all privileges on *.* to 'root'@'%';
Query OK, 0 rows affected (0.03 sec)
```

另外，如果远程连接的时候报plugin caching_sha2_password could not be loaded这个错误，可以尝试修改密码加密插件：

```
 mysql> alter user 'root'@'%' identified with mysql_native_password by 'Hadoop3!';
```

 或者

1. 主机更改访问权限

在mysql shell或者Navicat中输入

```sql
use mysql;select * from user;
```

![img](E:\WONI\Git\Docs\images\70)

如果如上图所示 应该更改host名称，使得任意IP可以访问C1数据库

```sql
update user set host = '%' where user = 'root';
```

更改完成最好重启一下mysql

windows下方法：

  win+R输入services.msc在里面找到MySQL右击重启

 

2.更改主机防火墙

  打开windowsDefender防火墙->高级设置->入栈规则->新建规则

![img](E:\WONI\Git\Docs\images\71)

![img](E:\WONI\Git\Docs\images\72)

 

3.查询主机IP地址

注意保证客机和主机在同一局域网下！！

打开网络和共享中心->点击下图位置->详细信息

![img](https://img-blog.csdn.net/20180614185013187?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RhbmRlbGlvbl9jbGF3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![img](E:\WONI\Git\Docs\images\73)

红色码的位置（IPv4地址）就是主机IP地址

![img](E:\WONI\Git\Docs\images\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RhbmRlbGlvbl9jbGF3,size_16,color_FFFFFF,t_70)

 

4.客机建立连接

注意在这步之前主机一定要激活连接！！！

**方法一：Navicat里连接方法**

连接->MySql

![img](E:\WONI\Git\Docs\images\74)

注意主机IP地址不可以有多余的空格 否则会连接失败

 

方法二：在mysql shell中连接

输入

```sql
mysql -h （主机IP地址） -P 3306 -u （主机用户名） -p（主机密码）
```

注意主机密码和-p是要连在一起的 例如-p123