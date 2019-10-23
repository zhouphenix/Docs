## 批处理bat命令

[toc]

### 一、获取目录路径

 `%~d0` 是当前盘符
`%cd%` 是当前目录 

```shell
@echo off
echo 当前盘符：%~d0
echo 当前盘符和路径：%~dp0
echo 当前盘符和路径的短文件名格式：%~sdp0
echo 当前批处理全路径：%~f0
echo 当前CMD默认目录：%cd%
pause
```



### 附录：小功能

### 1.循环执行子目录下bat文件

```shell
chcp 65001
@echo on
title AI启动
 
for /f "tokens=* delims=" %%m in ('dir /b/ad') do (
	echo 检索文件夹%%m...
    for /f "tokens=* delims=" %%n in ('dir /b "%%m\*.bat"') do (
		start "" "%%m\%%n"
    )
)
```

###  2.子目录bat文件

如启动Redis

```
chcp 65001
@echo on
title Redis-x64-3.2.100
cd %~dp0
echo Linkinging Redis...
redis-server.exe redis.windows.conf
```

