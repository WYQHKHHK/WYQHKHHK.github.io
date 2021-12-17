---
title: git pull error
date: 2021-12-13 20:26:18
tags: ['git','error']
updated:
categories:
  - 'Git教程'
  - 'git拉取错误'
keywords:
description:
top_img:
comments:
cover:
---

## git pull 报错



#### 本地git拉取时 报错：

```bash
error: Your local changes to the following files would be overwritten by merge:

####
####
####

Please commit your changes or stash them before you merge.
Aborting
Updating 3ffed04..fae751e

```

#### 提示可以看到：您不能与本地修改合并。Git 保护您免于丢失潜在的重要更改



#### 有三种解决方案：

1. 使用提交更改

   ```bash
   git commit -m "My message"
   ```

   进行合并，然后拉到本地

   ```bash
   git stash pop
   ```

2. 丢弃本地更改

   ```bash
   git reset --hard
   
   或者
   
   git checkout -t -f remote/branch
   ```

   然后拉取到本地

   ```bash
   git pull
   ```

3. 放弃本地的文件更改

   ```bash
   git checkout filename
   ```



#### 参考链接

1. [How do I resolve git saying "Commit your changes or stash them before you can merge"?](https://stackoverflow.com/questions/15745045/how-do-i-resolve-git-saying-commit-your-changes-or-stash-them-before-you-can-me)

