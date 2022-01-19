---
title: pip安装失败
date: 2022-01-19 17:19:54
tags:['pip','python']
updated:
categories:
  - 'Python'
  - 'pip安装'
keywords:
description:
top_img:
comments:
cover:
---

## pip安装报错解决

- ### 问题描述

  ```bash
  Could not fetch URL https://pypi.tuna.tsinghua.edu.cn/simple/pip/: There was a problem confirming the ssl certificate: HTTPSConnectionPool(host='pypi.tuna.tsinghua.edu.cn', port=443): Max retries exceeded with url: /simple/pip/ (Caused by SSLError(SSLEOFError(8, 'EOF occurred in violation of protocol (_ssl.c:997)'))) - skipping
  ```

- 解决方案：更换安装源

  windows下
   直接在user目录中创建一个pip目录，如：`C:\Users\xx\pip`，新建文件`pip.ini`，内容如下：

  ```bash
  [global]
  index-url = https://pypi.tuna.tsinghua.edu.cn/simple
  
  [install]
  
  trusted-host=https://pypi.tuna.tsinghua.edu.cn/simple
  ```



- 解决方案：增加信任服务器

  增加`--trusted-host pypi.douban.com`

  ```bash
  pip install  xxx  --index-url http://pypi.douban.com/simple/    --trusted-host pypi.douban.com
  ```

  - 注解

    ```bash
    1. pip install 表示通过pip 来安装某种包
    
    2. xxx     表示你要安装的包名，比如pipenv，jupyter等等
    
    3. -i http://pypi.douban.com/simple       表示将镜像地址切换为国内，这里切换到了豆瓣
    
    4.--trusted-host pypi.douban.com    表示将指定网站设置为信任服务器
    ```

  - 国内镜像地址：

    ```bash
    1)http://mirrors.aliyun.com/pypi/simple/    阿里云
    
    2)https://pypi.mirrors.ustc.edu.cn/simple/ 中国科技大学
    
    3) http://pypi.douban.com/simple/    豆瓣
    
    4) https://pypi.tuna.tsinghua.edu.cn/simple/   清华大学
    
    5)  http://pypi.mirrors.ustc.edu.cn/simple/ 中国科学技术大学
    ```

    

### tip: pip安装总是失败怎么办?

1. **安装包安装**

   从官网下载相应的安装包，解压后放在指定文件夹：

   打开命令行，切换到含有`setup.py`的文件夹

   然后输入`python setup.py install`

2. **WHL文件安装**

   首先，要从[官网](https://pypi.org/)上下载指定的 **.whl** 文件，选择最近版本点击，在`Downloadfiles`版块可以看到文件

   下载好后，切换到指定文件夹，输入**“pip install 文件名”**即可，如：

### 			

