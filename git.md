# Git使用

Git工具的使用文档

[TOC]

### 一、如何在github创建新的仓库项目

#### 步骤：

##### 1.在your profile的Repositories，点击创建，如下图： 

![新建git仓库](RES/20180307161211461.png)

##### 2.填写Repository信息

![Repository信息](RES/20180307161342565.png)

根据需求填写就好

##### 3.创建成功之后

![创建成功之后仓库](RES/20180307161544685.png)

##### 4.这样你就创建好了一个仓库，接下来的事情是你怎么把本地的git仓库和这个仓库相连接

在本地git仓库下打开git bash，执行： 

```
Administrator@V1BECM4KRXA7UVW MINGW64 /e/Git
$ git init
Initialized empty Git repository in E:/Git/.git/
$ git remote add origin https://github.com/zhouphenix/Docs.git
fatal: remote origin already exists.
Administrator@V1BECM4KRXA7UVW MINGW64 /e/Git (master)
$ git remote rm origin

Administrator@V1BECM4KRXA7UVW MINGW64 /e/Git (master)
$ git remote add origin https://github.com/zhouphenix/Docs.git

Administrator@V1BECM4KRXA7UVW MINGW64 /e/Git (master)
$ git pull https://github.com/zhouphenix/Docs.git

remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), done.
From https://github.com/zhouphenix/Docs
 * branch            HEAD       -> FETCH_HEAD

```

















