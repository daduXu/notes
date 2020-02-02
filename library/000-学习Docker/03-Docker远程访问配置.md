# Docker安装简介

![欢迎来到Coding的厨房！](amWiki/images/logo.png "欢迎来到Coding的厨房！")

为开发方便，部署及环境有清洁，选择使用了Docker！
下面是介绍一下我安装的过程。

## 系统:
- Centos8
- Docker
- MongoDB

## Docker 远程访问配置
首先，需要开启远程访问，然后，添加防火墙的访问规则，确保端口能被使用。
#### 1、开启docker远程访问
执行命令：`vi /lib/systemd/system/docker.service`
找到文件中的`ExecStart=`
修改：`ExecStart=/usr/bin/dockerd -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock --iptables=true`
>注：端口号是访问docker的，不是mongodb的端口号。
测试是否可以访问，http://ip:2375/info 就能看到docker的信息了。

#### 2、添加端口规则
由于centos8中使用的是自带的`firewalld`服务，方便使用，改为了传统的`iptables`
##### 停止firewalld服务
执行命令：`systemctl stop firewalld`
##### 禁用firewalld服务
执行命令：`systemctl mask firewalld`

##### 检查是否安装了 iptables
执行命令：`service iptables status`
##### 安装 iptables
执行命令：`yum install -y iptables`
##### 安装 iptables-services
执行命令：`yum install iptables-services`
>这里好像需要重启电脑（VM）

##### 添加端口规则
执行命令：`iptables -A INPUT -p tcp -m state --state NEW -m tcp --dport 27019 -j ACCEPT`
##### 保存生效端口规则
执行命令：`service iptables save`
##### 查看是否添加成功
执行命令：`cat /etc/sysconfig/iptables | grep 27019`
##### 服务重启
执行命令：`service iptables restart`

在电脑上使用mongodb连接工具，测试连接
# 成功
