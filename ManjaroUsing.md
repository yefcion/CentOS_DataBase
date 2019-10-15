

## Update mirror source

```shell
# update mirror source
sudo  pacman-mirrors -i -c China -m rank
# then tick USTC


# update software
sudo pacman -Syyu
```

```shell
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"




# shell changes
https://www.jianshu.com/p/bcb6df649514
```



```shell
# teamviewer
sudo teamviewer --daemon enable
sudo teamviewer daemon stop 
sudo teamviewer daemon start

https://blog.csdn.net/seek_of/article/details/82810476

# install nutstore
sudo pacman -S nutstore

yay -S deepin-wine-wechat


1、配置国内源
$ sudo  pacman-mirrors -i -c China -m rank  # 勾选科大源(USTC那个)

2、升级系统
$ sudo pacman -Syy && sudo pacman -Syu

3、安装Vim
$ sudo pacman -S vim

4、添加Archlinuxcn源
$ sudo vim /etc/pacman.conf # 打开文件
# 在文件末尾添加以下两行
[archlinuxcn]
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch

5、安装archlinuxcn签名钥匙(导入 GPG key，否则的话key验证失败会导致无法安装软件)
$ sudo pacman -Syy && sudo pacman -S archlinuxcn-keyring

6、安装yaourt
$ sudo pacman -S yaourt



```





```shell
pacman -Sc 清空并且下载新数据
pacman-mirrors -gb testing -c China //更新源
or
pacman-mirrors -c China -g //更新源
pacman -Syu 更新
pacman -Syy 更新源数据库
pacman -Syyu 安装更新
```

