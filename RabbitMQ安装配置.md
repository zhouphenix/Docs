# RabbitMQ安装配置

[toc]

1.安装Erlang，下载地址：http://erlang.org/download/otp_win64_21.3.exe

![展示图片_53.png](https://macrozheng.github.io/mall-learning/images/arch_screen_53.png)

2.安装RabbitMQ，下载地址：https://dl.bintray.com/rabbitmq/all/rabbitmq-server/3.7.14/rabbitmq-server-3.7.14.exe

![展示图片_54.png](https://macrozheng.github.io/mall-learning/images/arch_screen_54.png)

3.安装完成后，进入RabbitMQ安装目录下的sbin目录

![展示图片_55.png](https://macrozheng.github.io/mall-learning/images/arch_screen_55.png)

4.在地址栏输入cmd并回车启动命令行，然后输入以下命令启动管理功能：

```
rabbitmq-plugins enable rabbitmq_managementCopy to clipboardErrorCopied
```

![展示图片_56.png](https://macrozheng.github.io/mall-learning/images/arch_screen_56.png)

5.访问地址查看是否安装成功：http://localhost:15672/

![展示图片_57.png](https://macrozheng.github.io/mall-learning/images/arch_screen_57.png)

6.输入账号密码并登录：guest guest

7.创建帐号并设置其角色为管理员：mall mall

![展示图片_58.png](https://macrozheng.github.io/mall-learning/images/arch_screen_58.png)

8.创建一个新的虚拟host为：/mall

![展示图片_59.png](https://macrozheng.github.io/mall-learning/images/arch_screen_59.png)

9.点击mall用户进入用户配置页面

![展示图片_60.png](https://macrozheng.github.io/mall-learning/images/arch_screen_60.png)

10.给mall用户配置该虚拟host的权限

![展示图片_61.png](https://macrozheng.github.io/mall-learning/images/arch_screen_61.png)

11.至此，RabbitMQ的安装和配置完成。