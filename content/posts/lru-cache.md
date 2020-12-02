+++
author = "Lolioy"
title = "LRU 缓存"
date = "2019-12-23"
description = "Golang LRU Cache"
tags = [
    "go",
    "cache",
]
draft = true
+++

<!--more-->

## 常见的缓存策略

- 先进先出策略 `FIFO` ( `First In, First Out` )

- 最少使用策略 `LFU` ( `Least Frequently Used` )

- 最近最少使用策略 `LRU` ( `Least Recently Used` )

## 代码实现 ( `Golang` )

```go
package cache

type LRUCache struct {

}

```