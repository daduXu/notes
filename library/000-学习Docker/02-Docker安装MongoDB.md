# Docker安装简介

![欢迎来到Coding的厨房！](amWiki/images/logo.png "欢迎来到Coding的厨房！")

为开发方便，部署及环境有清洁，选择使用了Docker！
下面是介绍一下我安装的过程。

## 系统:
- Centos8
- Docker

## Docker MongoDB安装
#### 1、通过镜像安装
执行命令：`docker pull mongo:latest`

>使用以下命令来查看是否已安装了 mongo：
docker images

#### 2、运行容器，并映射服务器端口

运行方式有两种
- 开启用户验证
- 不带用户验证

>就是运行时，是否带有--auth参数

执行命令：`docker run -itd --name mongo -p 27017:27017 mongo`

#### 3、查看容器状态
执行命令：`docker ps -a`

>注： 安装与运行已经完成了，但外部使用还需要宿主机对外的端口暴露，要不没法远程访问。当然，不需要远程访问的另算。
