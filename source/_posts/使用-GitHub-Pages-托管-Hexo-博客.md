---
title: 使用 GitHub Pages 托管 Hexo 博客
categories: 
- Hexo
tags:
- hexo
- 博客
date: 2017-09-05 23:14:48
---
## 前提
### 搭建好的 Hexo 本地博客
还没有搭建好的童鞋,请看 [Windows系统下搭建Hexo个人博客](/post/Windows系统下搭建Hexo个人博客/)
### GitHub 账号
还没有注册的童鞋,请到 [GitHub](https://github.com/) 注册

## GitHub 准备
### 新建代码仓库
* 直接在你的 GitHub 上新建 Repository,名称必须为 username.github.io
* username 就是你的用户名,下同 

## Hexo 配置准备
### 安装 Hexo-Git 插件
在 PowerShell 或 CMD 中,运行以下命令: <br>
(啥,你问为啥用 PowerShell 而不用 CMD ?,因为 PoweShell 更 Powerful 啊,当然,要是没有 PowerShell 那只能用 CMD 了,不过有可能出现问题,先打个预防针)<br>
注:所有的命令均需要在你的 Hexo 项目路径下执行
* 稳定版

	npm install hexo-deployer-git --save 

* 最新版

	`npm install git+git@github.com:hexojs/hexo-deployer-git.git --save`

### 配置 _config.yml 文件
这里只说常用几个配置详细请看 [Hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git),没错你没看错,就是英文的,但是都是基本词汇,不难

	deploy:
	  type: git
	  repo: <repository url>
	  branch: [branch]
	  message: [message]

* repo: 仓库的URL,就是刚才新建的仓库地址<br>
* branch: 要同步的分支( 因为是用Github Pages 做服务器,分支这里必须填 master )<br>
* message: 提交信息.

## 发布网站到 GitHub Pages
一下三种之中任意一种都可以
### 命令 I

	hexo generate
	hexo deploy

当然可以简化为

	hexo g
	hexo d

### 命令 II

	hexo generate --deploy
简化

	hexo g -d

### 命令 III

	hexo deploy --generate

简化

	hexo d -g

### 命令执行结果
必须看到以下 Log 才算完全成功

	INFO  Deploy done:

## 查看你的博客
浏览器地址栏输入 <font color=orange>username</font><font color=skyblue>.github.io</font> 
## 接下来说说把整个项目同步到 GitHub
有两种方法
* 放到 username.github.io 仓库下
* 放到其他仓库下( 当然是你自己建的仓库,仓库名根据自己的喜好取 )
### username.github.io
* 在你自己的 username.github.io 下新建 Branch (分支),分支名自取,例: hexo
* 初始化 git

	git init

* 新建分支 hexo (替换为你刚才在 username.github.io 下新建的分支,下同)

	git branch hexo

* 切换分支

	git checkout hexo

* 关联远程仓库

	git remote add origin https://github.com/username/username.github.io.git

* 添加文件

	git add -A
	( -A 为添加所有改动文件,也可以单独指定文件或文件夹)

* 提交改动

	git commit -m message
	( message 为改动信息,自己填,如果有空格需要用 " " 引起来 )

* 同步到远程仓库

	git push origin hexo  
	(注:分支名 hexo 加不加都可以,因为已经切换到 hexo 分支,若不在 hexo 必须加)

### 其他仓库
* 在自己的 GitHub 新建一个仓库,例: hexo
* 初始化 git

	git init

* 关联远程仓库,替换 username,hexo 为自己的用户名和仓库名

	git remote add origin https://github.com/username/hexo.git

* 添加文件

	git add -A
	( -A 为添加所有改动文件,也可以单独指定文件或文件夹)

* 提交改动

	git commit -m message
	( message 为改动信息,自己填,如果有空格需要用 " " 引起来 )

* 同步到远程仓库

	git push origin master  
	(注:分支名 master 加不加都可以,因为默认在 master 分支,若不在 master 必须加)