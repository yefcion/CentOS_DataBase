

## Update mirror source

```shell
# update mirror source
sudo  pacman-mirrors -i -c China -m rank
# then tick USTC

# 更新
pacman -Syu 
# 更新源数据库
pacman -Syy

# update software
sudo pacman -Syyu

# install vscode
yaourt -S visual-studio-code-bin
# install nutstore
sudo pacman -S nutstore



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
# update pip source with tsu
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

