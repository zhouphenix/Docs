# Vue-Server
> vue后台服务



[TOC]

```
██╗    ██╗ █████╗ ███╗   ██╗
██║    ██║██╔══██╗████╗  ██║
██║ █╗ ██║███████║██╔██╗ ██║
██║███╗██║██╔══██║██║╚██╗██║
╚███╔███╔╝██║  ██║██║ ╚████║
 ╚══╝╚══╝ ╚═╝  ╚═╝╚═╝  ╚═══╝
                            
```

## 一、Ngnix服务搭建

### 步骤：

#### 1.首先下载安装Nginx（免安装），要下载稳定版：http://nginx.org/en/download.html

#### 2.启动命令与查看状态

 ```
D:\Tools\nginx-1.16.0>start nginx

D:\Tools\nginx-1.16.0>tasklist /fi "imagename eq nginx.exe"

映像名称                       PID 会话名              会话#       内存使用
========================= ======== ================ =========== ============
nginx.exe                     9040 Console                    2      9,532 K
nginx.exe                     6808 Console                    2      9,664 K

D:\Tools\nginx-1.16.0>nginx -V
nginx version: nginx/1.16.0
built by cl 16.00.40219.01 for 80x86
built with OpenSSL 1.1.1b  26 Feb 2019
TLS SNI support enabled
configure arguments: --with-cc=cl --builddir=objs.msvc8 --with-debug --prefix= --conf-path=conf/nginx.conf --pid-path=logs/nginx.pid --http-log-path=logs/access.log --error-log-path=logs/error.log --sbin-path=nginx.exe --http-client-body-temp-path=temp/client_body_temp --http-proxy-temp-path=temp/proxy_temp --http-fastcgi-temp-path=temp/fastcgi_temp --http-scgi-temp-path=temp/scgi_temp --http-uwsgi-temp-path=temp/uwsgi_temp --with-cc-opt=-DFD_SETSIZE=1024 --with-pcre=objs.msvc8/lib/pcre-8.43 --with-zlib=objs.msvc8/lib/zlib-1.2.11 --with-http_v2_module --with-http_realip_module --with-http_addition_module --with-http_sub_module --with-http_dav_module --with-http_stub_status_module --with-http_flv_module --with-http_mp4_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_auth_request_module --with-http_random_index_module --with-http_secure_link_module --with-http_slice_module --with-mail --with-stream --with-openssl=objs.msvc8/lib/openssl-1.1.1b --with-openssl-opt='no-asm no-tests -D_WIN32_WINNT=0x0501' --with-http_ssl_module --with-mail_ssl_module --with-stream_ssl_module
 ```

#### 3.启动Nginx之后，如何在其他设备上访问？

可以通过访问服务器设备IP+端口号，如192.168.0.110:80, 未配置访问则会显示Nginx页面

![Ngnix访问页面](/RES/nginx_access.PNG)

#### 4.如何配置Nginx，正确映射到服务端口上?

比如如何将服务http://localhost:8080/ 映射到80端口上，需要如下配置

在nginx.conf文件server节点下配置

```nginx
location / {
            root   html;
            index  index.html index.htm;
			proxy_pass  http://localhost:8080/;
        }
```

再`D:\Tools\nginx-1.16.0>nginx -s reload` 刷新页面即可访问

顺便配置后端服务

```nginx
location /ume {
			proxy_pass  http://localhost:9009/ume;
        }
```

![Nginx后端服务配置](E:\PHENIX\GIT\Phenix-Manager\RES\Nginx_access2.PNG)





**重点：比如80端口可以监听多个，根据不同域名转发到不同服务器上**



下面是一些常用语句

查看Nginx的版本号：`nginx -V`

启动Nginx：`start nginx`

快速停止或关闭Nginx：`nginx -s stop`

正常停止或关闭Nginx：`nginx -s quit`

配置文件修改重装载命令：`nginx -s reload`




## 附录

### 1.[window 怎么查看nginx是否启动](https://jingyan.baidu.com/article/f79b7cb33acfed9145023e78.html)

