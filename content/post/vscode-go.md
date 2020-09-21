+++
author = "Lolioy"
title = "VSCode 配置 Golang 环境"
date = "2020-06-11"
description = "vscode go 插件配置"
tags = [
    "study",
    "vscode",
    "go",
]
+++

<!--more-->

`VSCode`和`Golang` 安装就不说了，网上教程一大把。

## GoProxy 配置

> 由于国内网络环境限制，建议先配置`GoProxy`环境变量，当然不配置也行，你能正常访问 https://golang.org/ 的话问题不大。
> 
> 推荐使用`go mod`管理项目

在安装好`Go`运行环境后，`Windows`系统可以打开`cmd`或者`powershell` (`macOS`和`Linux`系统打开终端)，分别输入以下命令
```shell
# 启用 go mod
go env -w GO111MODULE=on
# 设置 Go Proxy 代理
go env -w GOPROXY=https://goproxy.io,direct
```

## VScode 安装 Go 插件

![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/151950a22fc34c859a69b71f529ab4f5~tplv-k3u1fbpfcp-zoom-1.image)

## VSCode 安装 Go 工具包

Go 工具包包含了一些格式化、代码检查等功能

1. `Ctrl` + `Shift` + `P` (`Windows`环境)，或者选择 "查看" -> "命令面板"

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9f30d5d31f94468c8632dbd4807440ab~tplv-k3u1fbpfcp-zoom-1.image)

2. 输入 `go isntall`

3. 选择 `Go: Install/Update Tools` 项

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/bf98a7cd5c82437eafa9a347a298b6ea~tplv-k3u1fbpfcp-zoom-1.image)

4. 选择全部安装

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f6af3ae194404934a89376f181402a03~tplv-k3u1fbpfcp-zoom-1.image)

5. 这时候会弹出 "输出" 框，等待安装完成即可

![](https://p9-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/14e40c6c18b24aaa80060add1c0bcbe4~tplv-k3u1fbpfcp-zoom-1.image)
![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d517407fc96a437985ef307ab48f0bc7~tplv-k3u1fbpfcp-zoom-1.image)

## Vscode Go 插件配置

1. 打开`VSCode`设置面板

![](https://p1-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/d9fbe9b2b4214e0f9fbd5a24b57a4903~tplv-k3u1fbpfcp-zoom-1.image)

2. 定位到`Go`插件项

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/f25b41352c784d608b3e623fa7ad18d5~tplv-k3u1fbpfcp-zoom-1.image)

3. 修改格式化`Go`代码工具，我习惯使用的是`goimports`，大家可以根据自己的喜好进行选择

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/561900e5594449049de219f6451b5fc8~tplv-k3u1fbpfcp-zoom-1.image)

4. 启用代码提示（个人习惯，可以不启用）

![](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/8484f2e9cae94406abde0446a7f50035~tplv-k3u1fbpfcp-zoom-1.image)

5. 启用`Go Server`，启用后可以开启代码跳转、格式化、自动完成、代码诊断等功能

![](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/3bce571c29d741c0bc9b05431458159a~tplv-k3u1fbpfcp-zoom-1.image)

> 还可以设置其他配置项，感兴趣的同学可以到官方文档自行了解 https://github.com/golang/vscode-go/blob/master/docs/settings.md

## 结语

到这里`VSCode`基本上可以满足我们日常开发`Go`的需求了