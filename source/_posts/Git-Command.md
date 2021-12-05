---
title: Git-Command
date: 2021-12-05 10:51:31
tags:
  - Git
updated:
categories:
  - Git教程
  - Git命令
keywords:
description:
top_img:
comments:
cover: '/img/hexo/1205/trees.png'
---

本文转载自[JourWon](https://github.com/JourWon) [提交常用Git命令](https://github.com/JourWon/git/commit/a411ff5ff10bba58c06de878ea6c2ec52bb68342)

# Git常用命令--Git Command



## git工作流程

![workflow](/img/hexo/1205/git工作流程.png)

说明：

- workspace：工作区
- staging area：暂存区/缓存区
- local repository：版本库或本地仓库
- remote repository：远程仓库

## 配置用户名和邮箱

```bash
$ git --version   # 查看git的版本信息
$ git config --global user.name   # 获取当前登录的用户
$ git config --global user.email  # 获取当前登录用户的邮箱

```

登陆 `git`

```bash
# 如果刚没有获取到用户配置，则只能拉取代码，不能修改  要是使用git，你要告诉git是谁在使用
$ git config --global user.name 'userName'    # 设置git账户，userName为你的git账号，
$ git config --global user.email 'email'
# 获取Git配置信息，执行以下命令：
$ git config –list

```



## 配置https和ssh推送时保存用户名和密码

```bash
# https提交保存用户名和密码
$ git config --global credential.helper store
# 生成公钥私钥，将公钥配置到GitHub，ssh提交就可以免输入用户名密码
# 三次回车即可生成 ssh key
$ ssh-keygen -t rsa
# 查看已生成的公钥
$ cat ~/.ssh/id_rsa.pub

```



## 推送到远程仓库正确流程

```bash
1. git init # 初始化仓库
2. git add .(文件name) # 添加文件到本地仓库
3. git commit -m "first commit" # 添加文件描述信息
4. git remote add origin 远程仓库地址 # 链接远程仓库，创建主分支
5. git pull origin master --allow-unrelated-histories # 把本地仓库的变化连接到远程仓库主分支
6. git push -u origin master # 把本地仓库的文件推送到远程仓库

```

