# 问题描述:    直接使用gtihub.com网址访问github浏览器无响应。

【收藏自】[github无法访问问题解决方法](https://www.cnblogs.com/zhoujishan/p/14669762.html)

## 解决办法：

### 1、登录https://github.com.ipaddress.com/去查询github.com、github.global.ssl.fastly.net对应的IP地址；

### 2、在网站的Domain Summary下查询到Github的IP地址；

![img](https://img2020.cnblogs.com/blog/2127117/202104/2127117-20210417103930954-2038591506.png)

 

### 3、直接在浏览器中输入IP地址访问Github，网页正常响应。

### 4、编辑C:\Windows\System32\drivers\etc下的hosts文件，将github的IP地址保持到hosts文件。

![img](https://img2020.cnblogs.com/blog/2127117/202104/2127117-20210417105300349-2026976966.png)

 

 

### 5、如果遇到无法保存hosts文件的问题，由于hosts文件权限导致，可以右键点击hosts文件，选择“属性”->“安全”->给user用户勾选写入权限。

![img](https://img2020.cnblogs.com/blog/2127117/202104/2127117-20210417104857108-1428517550.png)

 

###  6、在cmd中运行ipconfig /flushdns ，刷新dns，此时浏览器中直接输入github.com即可成功访问。

