+++
author = "Lolioy"
title = "腾讯云服务器 Docker 安装记录"
date = "2019-09-18"
description = ""
tags = [
    "docker",
    "腾讯云",
    "工具",
]
series = ["工具"]
featuredImage = "images/posts/server-bg.png"
+++

<!--more-->

最近买了台腾讯云服务器, 习惯了使用 `Docker` 部署服务, 第一时间当然是给自己的服务器装一个 `Docker`

## 配置软件源

由于是腾讯云的服务器, 所以配置国内软件源的时候肯定是优先选择腾讯云提供的软件源

腾讯软件源: https://mirrors.cloud.tencent.com/

找到合适的Linux发行版本, 我的是 `CentOS 7`: https://mirrors.cloud.tencent.com/help/centos.html

按照文档里面的说明, 直接替换

```shell
# 下载替换软件源
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.cloud.tencent.com/repo/centos7_base.repo

# 更新缓存
yum clean all
yum makecache
```

## 安装 Docker

- 首先清除一下旧版本和依赖

```shell
yum remove docker \
    docker-client \
    docker-client-latest \
    docker-common \
    docker-latest \
    docker-latest-logrotate \
    docker-logrotate \
    docker-engine
```

### 安装 `yum-utils`

```shell
yum install -y yum-utils
```

### 配置 `Docker` 仓库 && 安装 `Docker`

```shell
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

这一步很关键, 然而, 由于国内网络原因, 下载是真的慢, 所以我替换使用了腾讯云提供的仓库

```shell
sed -i 's+download.docker.com+mirrors.cloud.tencent.com/docker-ce+' /etc/yum.repos.d/docker-ce.repo
```

安装 `Docker`

```shell
yum install docker-ce docker-ce-cli containerd.io
```

### 到这里 `Docker` 就已经安装好了, 启动运行看一下

```shell
systemctl start docker
```

### 配置开机启动

```shell
systemctl enable docker
```

### 同样的问题, `Docker` 的默认仓库是搭建在国外服务器上的, 手动配置一下国内仓库

```shell
vim /etc/docker/daemon.json
```

注意配置文件的格式

```json
{
	"registry-mirrors": [
		"https://9903913c011242788ce2103eaaa4534d.mirror.swr.myhuaweicloud.com",
		"https://dockerhub.azk8s.cn",
		"https://docker.mirrors.ustc.edu.cn",
		"http://hub-mirror.c.163.com",
		"https://registry.docker-cn.com"
	]
}
```

## 结语

整个配置过程难度不大, 主要还是国内网络的问题, 需要替换软件源和仓库等等 ~~

**现在, 可以准备把项目扔到服务器上运行了 o(*￣▽￣*)ブ**