---
date: 2023-07-24T09:01:17.000Z
updated: 2024-02-08T07:27:19.289Z
title: 猴子也不一定能听懂的超可爱前后端分离博客mix space部署
slug: mix-space-development
oid: 65b4c65d60dc4a15ba7abcb8
categories: 学习
type: post
---

## 配置环境

### 安装docker和docker-compose

此处建议使用root账户

#### 更新软件源

```bash
apt update
apt upgrade
```

#### 安装必要依赖

```bash
apt install curl unzip vim
```

#### 安装docker和docker-compose

国内:

```bash
export DOWNLOAD_URL="https://mirrors.tuna.tsinghua.edu.cn/docker-ce"
curl -fsSL https://get.docker.com/ | sudo -E sh
```

国外:

```bash
curl -fsSL https://get.docker.com | bash -s docker
```

### 检查安装

使用如下命令:

```bash
docker -v
docker compose version
```

如果有输出则为安装成功

若提示类似 <mark>Command 'docker' not found</mark> 的提示(善用翻译),请检查安装步骤

### (非必要)配置镜像加速器

自己去[阿里云](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)看

## 安装mix space后端

### 拉取docker-compose编排文件

使用如下命令:

```bash
cd && mkdir -p mx-space/core && cd $_
wget https://fastly.jsdelivr.net/gh/mx-space/core@master/docker-compose.yml
```

### 编辑环境变量

在当前目录(mx-space/core)下新建一个名为 **.env** 的文件并将其使用诸如vim等工具打开

将[这里](https://mx-space.js.org/docs/docker#%E9%85%8D%E7%BD%AE-core-%E5%90%AF%E5%8A%A8%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)生成的内容填入 **.env** 中

### (非必要)修改后端开放文端口

```yml
  app:
    container_name: mx-server
    image: innei/mx-server:latest
    command: sh ./docker-run.sh
    environment:
      - TZ=Asia/Shanghai
      - NODE_ENV=production
      - ALLOWED_ORIGINS
      - JWT_SECRET
      - ENCRYPT_KEY
      - ENCRYPT_ENABLE
    volumes:
      - ./data/mx-space:/root/.mx-space
    ports:
      - '2333:2333'
    depends_on:
      - mongo
      - redis
    links:
```

这是节选的一部分编排文件,其中

`- '2333:2333'`

冒号左边的端口对应了后端映射到外部的端口号

~~反正改左边的就行了~~(记得开放安全组)

### 容器,启动!

老夫直接 `docker compose up -d` 让容器跑起来

只要没出现ERROR就是启动成功了

然后,去`http://[IP]:后端端口/qaqdmin`初始化吧

## 安装前端

懒得写了，要不你去官方文档看看:[[Shiro 主题 | Mix Space (](https://mx-space.js.org/themes/shiro)
