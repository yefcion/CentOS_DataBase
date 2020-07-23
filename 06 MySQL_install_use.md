# Win10 上用 VirtualBox 安装 CentOS 使用 Docker 安装 mysql/redis 全过程记录



## 在 VirtualBox 上安装 CentOS7 系统

安装虚拟机 VirtualBox(VB)，安装过程简单不值得说

下载 [CentOS7.8 镜像](https://mirrors.tuna.tsinghua.edu.cn/centos/7.8.2003/isos/x86_64/)并安装系统。一堆 IOS 中，DVD 是完整版，mini 是精简版，由于是在虚拟机装个人建议装 mini 版，如果需要额外软件自己装就好了。

注意，装好 VB 后镜像列表里如果没有 64bit 版本，可能是因为电脑本机虚拟化没开 & win8 以上电脑启动了 Hyper-V 服务。前者到 BIOS 中开启 CPU 虚拟化，后者在 Windows 服务（任务管理器-服务-窗口最下打开服务按钮）中关闭 Hyper-V 主机服务即可。

安装 CentOS 的界面使图形界面，根据提示操作就可以，最后有设置 root 用户和密码的地方，设置一下并记住



## 配置虚拟机 和 CentOS 的网络关联

在虚拟机中使用 CenOS 体验极差，建议先配置 SSH，然后在本地 PC 使用远程工具 Mobaxterm 进行远程连接使用命令行操作。

首先在 PC cmd 命令行中 ipconfig 查看当前机器上的 ip，可以看到一条 VirtualBox Only 即为 VB 上系统的 ip

然后在 VB 中设置-全局设定-网络，NAT 穿越 - 高级，新增一条网络转发，第一个格子的 ip 填上面的 ip，第二格子 ip 填 127.0.0.1

（中间如果出现 ip 变化的情况就到 windows 的网络适配器中写固定 ip，不要动态获取）

之后就可以使用远程工具连接了，建议使用免费的 Mobaxterm，新建 Session，ip 是上面 win cmd 中 VB 的 ip，用户 root，端口号 22

（我使用时候默认开了 ssh 连接）



## 配置 CentOS 镜像源

更改 yum 镜像源为：清华镜像

```bash
# 备份原镜像
sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak

sudo echo  > /etc/yum.repos.d/CentOS-Base.repo

vim /etc/yum.repos.d/CentOS-Base.repo

# -------------------------------------
# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the
# remarked out baseurl= line instead.
#
#


[base]
name=CentOS-$releasever - Base
baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/os/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

#released updates
[updates]
name=CentOS-$releasever - Updates
baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/updates/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7



#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras
baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/extras/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7



#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus
baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos/$releasever/centosplus/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
# -------------------------------------------------------

# 更新软件包缓存

sudo yum makecache
```

> 注：可能会出现 gpgkey could not found 的报错，原因是上面脚本中 gpgkey 路径不对，根据自己系统中的的路径改一下
>
> gpgkey 的路径是 `/etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7`，把上面脚本中的 4 处 file:/// 都改掉



精简版的 CentOS 软件少的可怜，推荐安装一些必备的软件

```bash
# 查看 网卡配置，之前使用 ip addr
yum install ifconfig

# 文本编辑，乌干达儿童感谢你
yum install vim

# 端口检查
yum install telnet
```



## 在 CentOS 中安装 docker 

```bash
# 使用安装脚本
# curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
curl -sSL https://get.daocloud.io/docker | sh

# 启动 docker
sudo systemctl start docker

# 验证是否正确安装 Docker Engine-Community
sudo docker run hello-world


# 镜像加速
vim /etc/docker/daemon.json

{"registry-mirrors":["https://prll5wtk.mirror.aliyuncs.com"]}

# 重启 docker 服务
sudo systemctl deamon-reload
sudo systemctl restart docker

# 检查加速器是否生效
docker info
```



## 在 docker 中装 mysql

```bash
# 查看 mysql 可用版本
docker search mysql 

# 拉取 mysql 镜像
docker pull mysql:5.7.4

# 查看本地镜像
docker images

# 运行容器
docker run -itd --name mysql_574 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root

# 查看已运行的容器
docker ps

# 进入容器
docker exec -it mysql_574 bash
```

mysql 连不上可能的原因 16001

1. CentOS 3306 端口没开

2. MySQL 用户授权

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root' WITH GRANT OPTION; 

3. VirtualBox 端口转发

4. 开通 2375 端口



## 在 docker 中装 redis

```bash
# 查看 redis 可用版本
docker search redis 

# 拉取 redis 镜像
docker pull redis:3.2.9

# 查看本地镜像
docker images

# 运行容器
docker run -itd --name redis_329 -p 6379:6379 redis

# 查看已运行的容器
docker ps

# 进入容器
docker exec -it redis_329 bash
```

