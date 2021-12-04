---
title: 创建Git分支将Hexo博客迁移到其它电脑
date: 2021-12-05 01:16:25
tags: 
  - hexo
  - git
updated:
categories:
  - hexo教程
  - hexo多端登陆
keywords:
description:
top_img:
comments:
cover:
---

```
介绍：GitHub+Hexo搭建博客的过程比较平滑，但是它的配置却非常耗时间，一旦电脑出现问题或者需要在另外一台电脑上写博客，那么Hexo博客的迁移非常就让人头疼。下面参考其他博客的方法，实现在不同电脑端维护网站配置
```

## 部署示意图

![](/img/hexo/1205/Artboard.png)

## 必备文件

| 文件（夹）   | 说明                                            |
| :----------- | ----------------------------------------------- |
| scaffolds/   | 博客文章的模版                                  |
| source/      | 所有博客文章，以及about、tags、categories等page |
| themes/      | 网站的主题                                      |
| .gitignore   | 在push时需要忽略的文件和文件夹                  |
| _config.yml  | 站点配置文件                                    |
| package.json | 依赖包的名称和版本号                            |



## 环境配置

1. 安装`git`
2. 安装`nodejs`
3. 安装`hexo`

​	**说明**：以上配置请参照[`hexo`](https://hexo.io/zh-cn/docs/)



## 创建分支

**根据示意图**

在`Github`的`username.github.io`仓库上新建一个`hexo`(分支名字可自定义)分支, 在下图箭头位置输入分支名字,完成创建

![0215](/img/hexo/1205/0215.png)

**更改默认分支**：

切换到该`hexo分支`，并在`该仓库->Settings->Branches->Default branch`中将默认分支设为`hexo`,然后点击`update`进行保存，更改教程看[这里](https://docs.github.com/cn/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository/changing-the-default-branch)



## 克隆分支

然后在本地的任意目录下，打开git bash

```bash
git clone git@github.com:username/username.github.io.git
```

将其克隆到本地，因为默认分支已经设成了`hexo`，所以`clone`时只`clone`了`hexo`

接下来在克隆到本地的`username.github.io`中，把除了`.git` 文件夹外的所有文件都删掉

把之前我们写的博客源文件全部复制过来，除了`.deploy_git`。这里应该说一句，复制过来的源文件应该有一个`.gitignore`，用来忽略一些不需要的文件，如果没有的话，自己新建一个，在里面写上如下，表示这些类型文件不需要git：

```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

**注意**，如果你之前克隆过`theme`中的主题文件，那么应该把主题文件中的`.git`文件夹删掉，因为`git`不能嵌套上传，最好是显示隐藏文件，检查一下有没有，否则上传的时候会出错，导致你的主题文件无法上传，这样你的配置在别的电脑上就用不了了



## 上传分支

此时，你的 `username.github.io`文件夹内所有文件都已经准备完成

运行 `git bash` 执行：

```bash
git add .
git commit –m "initial commit"
git push 
```

这样就上传完了，可以去你的`github`上看一看`hexo`分支有没有上传上去，其中`node_modules`、`public`、`db.json`已经被忽略掉了，没有关系，不需要上传的，因为在别的电脑上需要重新输入命令安装



## 更换电脑-环境配置

1. 安装`git`

2. 设置`git`全局邮箱和用户名

   ```bash
   git config --global user.name "yourgithubname"
   git config --global user.email "yourgithubemail"
   
   ```

3. 设置`ssh` `key`

   ```bash
   ssh-keygen -t rsa -C "youremail"
   #生成后填到github和coding上（有coding平台的话）
   #验证是否成功
   ssh -T git@github.com
   
   #返回  You've successfully authenticated  代表成功
   
   ssh -T git@git.coding.net #(有coding平台的话)
   ```

4. 安装`nodejs`

5. 安装`hexo`

   但是已经不需要初始化了	

   直接在任意文件夹下

   ```bash
   git clone git@github.com:username/username.github.io.git
   ```

最后：

```bash
cd username.github.io
npm install
npm install hexo-deployer-git --save
```

生成，部署：

```bash
hexo g
hexo d
```



## tips

提交流程：

![](/img/hexo/1205/Artboard_1.png)



## 参考链接

- [迁移hexo到新电脑](https://www.jianshu.com/p/153490a029a5)
- [GitHub + Hexo搭建自己博客(三) 多设备管理](https://juejin.cn/post/6844903780664737806)
