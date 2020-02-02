# Docker安装简介

![欢迎来到Coding的厨房！](amWiki/images/logo.png "欢迎来到Coding的厨房！")

为开发方便，部署及环境有清洁，选择使用了Docker！
下面是介绍一下我安装的过程。

## 系统:
- Centos8


## 一、Docker安装

### 使用 Docker 仓库进行安装 Docker Engine-Community
#### 1、安装所需的软件包。yum-utils 提供了 yum-config-manager ，并且 device mapper 存储驱动程序需要 device-mapper-persistent-data 和 lvm2。
执行命令：`sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2`

#### 2、使用以下命令来设置稳定的仓库。
执行命令：`sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo`

#### 3、安装，
执行命令：`sudo yum install docker-ce docker-ce-cli containerd.io`
>注：提示要是版本强制出问题，就选择不使用最佳选择的参数。
如果提示您接受 GPG 密钥，请选是。

#### 4、启动 Docker。
执行命令：`sudo systemctl start docker`
#### 5、通过运行 hello-world 映像来验证是否正确安装了 Docker Engine-Community 。
执行命令：`sudo docker run hello-world`
