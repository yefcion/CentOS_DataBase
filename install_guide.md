# Install Guide

## 切换 软件镜像源

镜像源信息存在文件 sources.list 中，实际上就是修改文件。

首先复制其他镜像源，如下提供清华和阿里镜像源，二选一即可
```shell
# 清华大学源
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse

# 阿里云源
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```

系统中操作

```shell
mv /etc/apt/sources.list /etc/apt/sources.list_bak      # 备份原本镜像源
vim /etc/apt/sources.list                               # 编辑 sources.list 文件
# 删除文件内容，将上面复制的内容粘贴进去，保存退出即完成镜像切换
sudo update software                                    # 升级已安装所有软件
```





## 安装、配置输入法
> 注：由于自带的 ibus 输入法不能成功设置中文，这里使用 fcitx 输入法
首先安装 fcitx 和相关依赖包
sudo apt-get install fcitx fcitx-config-gtk fcitx-googlepinyin

安装完之后设置fcitx为默认输入法

```shell
im-config					# 弹出图形界面进行设置
```

然后重启电脑（或者注销重新登录）

设置输入法

```shell
fcitx-configtool			# 弹出图形界面
```


添加 pinyin 输入法


## 配置 Git
安装 git 和 ssh

```shell
sudo apt-get install git ssh
```

设置用户名和密码

```shell
git config --global user.name "UserName"    # 设置用户名
git config --global user.email email@server # 设置邮箱
git config --global  --list                 # 查看当前用户配置

ssh-keygen -t rsa -C "yefcion@163.com" 		# 生成 SSH KEY
```


生成 ssh key 过程中，会让你填写 passphrase，连按三次回车跳过即可。

打开 id_rsa.pub 文件，将内容复制到剪贴板(SSH KEY 公钥，用于 GitHub 身份验证)。

登录 GitHub，打开 Personal settings 页面，选择 SSH and GPG keys 选项，按图设置将复制的 key 粘贴进去。

![设置](https://cdn.jsdelivr.net/gh/yefcion/PicData@master/img/20190906230017.png)



## 配置 Java 开发环境
下载 JDK 文件，[下载地址](http://www.oracle.com/technetwork/java/javase/downloads/index.html)


编辑配置文件

## 安装 Java IDE
下载 IDEA Ultimate 安装包，[下载地址](https://www.jetbrains.com/idea/download/#section=linux)

打开下载路径，解压 JDK 文件，并放到安装目录

```shell
cp <ideaIU.tar.gz> /usr/java        # 将 ideaIU.tar.gz 拷贝到安装路径 /usr/java 下
cd /usr/java
tar -zxvf ideaIU.tar.gz             # 解压安装包得到 idea-IU 文件夹
sudo chmod 755 -R idea-IU/          # 赋予权限
cd idea-IU/bin                      # 打开启动目录
./idea.sh                           # 启动安装脚本
```

下面是图形安装界面，按需设置。然后到激活窗口
选择激活方式 `Activ Code`
打开网址 http://idea.lanyus.com/ 到页面最下面点击`获得注册码`，复制注册码，并粘贴到 idea 的激活框里

大功告成。



## Tips：
安装 .deb 文件

```shell
dpkg -i <package>
```

安装 .appimages 文件

```shell
./<package>.appimages
```

回桌面快捷键 Win + D 设置
