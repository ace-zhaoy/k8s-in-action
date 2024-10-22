# 安装

1. ### 脚本安装

```shell
# 安装最新版
wget -qO- https://get.docker.com/ | sh

# 安装指定版本
wget -qO- https://get.docker.com/ | sh -s -- --version 26.1

#从阿里云安装指定版本
wget -qO- https://get.docker.com/ | sh -s -- --mirror Aliyun --version 25.0
```
版本号可以从[Release](https://docs.docker.com/engine/release-notes)或[这里](https://download.docker.com/linux/static/stable/x86_64/)查看

2. ### 非root用户加入docker组
```shell
sudo usermod -aG docker $(whoami)

sudo reboot
```
