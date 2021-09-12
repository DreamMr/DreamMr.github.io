---
layout: post
title: Docker搭建deeplearning环境
category: Docker
author: 一个不懂数学的程序员
excerpt_separator: 。
---

基于Docker18.06 构建deeplearning镜像。

```dockerfile
FROM nvidia/cuda:10.0-base
RUN apt-get update -y && apt-get install -y software-properties-common \
&& apt-get install python3.6 -y && cd /usr/bin && ln -s python3.6m python && apt-get install python3-pip -y \
&& cd /usr/bin && ln -s pip3 pip
```

该镜像依赖nvidia/cuda:10.0-base作为基础镜像，并安装python3.6。

构建镜像命令：

```shell
docker build -t python3.6_nvidia:v1 .
```

构建完成后可以使用命令：

```
docker image ls
```

查看该镜像是否存在。

后续可以基于改镜像作为基础镜像安装其他deeplearning 包。

docker18中使用gpu要使用runtime参数：

```
docker run --runtime=nvidia python3.6_nvidia:v1
```

