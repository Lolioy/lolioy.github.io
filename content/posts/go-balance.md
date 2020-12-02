+++
author = "Lolioy"
title = "Golang 实现负载均衡算法"
date = "2019-06-09"
description = "Golang Balance"
tags = [
    "go",
    "balance",
]
draft = true
+++

<!--more-->

## 常用的负载均衡算法

- 随机负载均衡

- 轮询负载均衡

- 加权轮询负载均衡

- 一致性 `HASH` 负载均衡

## `Golang` 实现

#### 随机负载均衡

```go
type ServerSet []string

type LoadBalance struct {
    Servers ServerSet
    Count int
    Cur int
    SumWeight int
}

func (lb *LoadBalance) Add(addr ...string) {
    if len(addr) > 0 && addr[0] != "" {
        lb.Servers = append(lb.Servers, addr)
        Count += len(addr)
    }
}
```
