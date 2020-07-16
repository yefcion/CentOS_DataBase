## 安装 MySQL

采取在 Win10 安装 Ubuntu，然后在 Ubuntu 中安装 MySQL 的思路。

[win10应用商店安装Ubuntu全攻略及问题解决](https://blog.csdn.net/yefcion/article/details/79958252#comments_12808790)

安装完成后可以发现 Ubuntu 和 wWin 的 IP 地址是一样的

### 更新镜像源

```shell
# 查看 Ubuntu 版本
cat /etc/issue

# 更换清华镜像
cd /etc/apt
# 备份原本镜像源
sudo cp sources.list sources.list.bak
# 给文件写权限
sudo chmod 777 sources.list

vim sources.list

# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse

# 更新清华源
sudo apt-get update
# 更新软件
sudo apt-get  upgrade
```

### 安装 mysql

```shell
# 1.卸载干净
# 2.安装 dba
# 3.解决问题
sudo add-apt-repository ppa:rafaeldtinoco/lp1871129
sudo apt update
sudo apt install libc6=2.31-0ubuntu8+lp1871129~1 libc6-dev=2.31-0ubuntu8+lp1871129~1 libc-dev-bin=2.31-0ubuntu8+lp1871129~1 -y --allow-downgrades
sudo apt-mark hold libc6
```



## docker 安装 mysql
mysql 连不上原因 16001

1.CentOS 3306 端口没开

2.MySQL 用户授权

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root' WITH GRANT OPTION; 

3.VirtualBox 端口转发