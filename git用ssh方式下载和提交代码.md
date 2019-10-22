文章地址：[git用ssh方式下载和提交代码](https://www.cnblogs.com/yanh0606/p/9199774.html) 



# [git用ssh方式下载和提交代码](https://www.cnblogs.com/yanh0606/p/9199774.html)

之前git上传下载代码都是用的http方式，但是今天遇到个大文件上传的时候，http方式上传超出大小限制了413 request entity too large，所以改成了用ssh方式上传，简单记录下ssh的配置方式。

并且有一个工程下载的时候也报错了，错误信息如下：

fatal: The remote end hung up unexpectedly

fatal: early EOF

fatal: index-pack failed

也可以用下面的方法解决。

 

代码用Eclipse管理，用http方式的时候没什么特别的，直接clone输入地址和用户名密码即可，ssh的方式需要额外配置一下ssh key。

1、运行Git Bash客户端，执行`ls ~/.ssh`; 如果列出下图这两个rsa文件，那应该就不需要配置ssh key了，如果不放心就将这几个文件删掉，重新生成。

![img](https://images2018.cnblogs.com/blog/795775/201806/795775-20180619172450826-1558620544.png)

 

2、生成ssh key文件，执行`ssh-keygen -t rsa -C "xxx.xxx.com"`

  \- t 指定密钥类型，默认是 rsa ，可以省略

  -C 设置注释文字，比如git的地址。

  -f 指定密钥文件存储文件名，我们省略了命令执行的时候会让你选择文件名，直接回车就会保存在默认的位置。

  然后会让你输入两次密码，最后出现 key fingerprint和 key's randomart 就表示创建成功了。

![img](https://images2018.cnblogs.com/blog/795775/201806/795775-20180619175611366-2140867523.png)

 

3、将ssh key添加到git中， vi id_rsa.pub 然后复制文件内容，进入git页面，个人设置，SSH Keys设置页面，在Key文本框中输入复制的内容，然后点Add Key按钮完成添加。

![img](https://images2018.cnblogs.com/blog/795775/201806/795775-20180619173617790-40753718.png)

 

4、测试连接你的git地址，`ssh -T git@xxx.xxx.com` 输入正确密码后如果出现Welcome就是连接成功了。

![img](https://images2018.cnblogs.com/blog/795775/201806/795775-20180619175515942-771922145.png)

 

5、接下来就可以通过`git clone git@xxx.xxx.com:xxx` 来下载代码了，或者Eclipse中图形化界面下载操作基本一样的，只是都要注意，选择项目地址的时候跟之前http的不一样，现在要选择ssh的。

![img](https://images2018.cnblogs.com/blog/795775/201806/795775-20180619174844162-1719871666.png)

 

并且注意Eclipse中的这个ssh的路径配置

![img](https://images2018.cnblogs.com/blog/795775/201806/795775-20180620103639593-2077638021.png)