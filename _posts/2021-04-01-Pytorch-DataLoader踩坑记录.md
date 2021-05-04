---
layout: post
title: Pytorch-Dataloader使用多个num-work
category: pytorch
author: 一个不懂数学的程序员
---

在pytorch里面可以使用numwork来加载数据（多线程），但是如果在加载数据的过程中发生错误，会没办法直接看清究竟发生什么问题。（这和多线程处理一样，会把真正错误信息淹没）。建议：一开始使用num_work=0来加载数据。

