# Deepin 安装后相关配置

## 命令行 安装软件

```shell
# 安装软件
sudo apt-get install <name>	
# 卸载软件
sudo apt-get --pruge remove <name>
# 查看软件列表
dpkg --list					
```



## 安装包 安装软件

NutStore 坚果云
地址：https://www.jianguoyun.com/s/downloads/linux
安装方式：双击安装
https://www.jianguoyun.com/s/downloads/linux

Electron-ssr 代理软件
地址：https://www.jianguoyun.com/p/Datu08sQn7KEBxjv6aAC
安装方式：双击安装

Deepin系统安装软件的方法总结 2019-7-22 19:47 
https://bbs.deepin.org/forum.php?mod=viewthread&tid=181002




## 系统相关 软件升级

###  FireFox 火狐
到火狐官网 下载最新版火狐浏览器，得到 firefox.gz.tar 压缩包

解压得到一个文件夹 firefox，将文件夹改名为 firefox-zh

然后用管理员身份打开根目录下的文件夹 /usr/lib/，将其中的文件夹 firefox-zh 改名为 firefox-zh 作为备份

最后将前面改名得到的文件夹 firefox-zh 复制到 /usr/lib/ 中，搞定




## 修改默认编辑器为 vim
1、修改配置

```shell
echo export EDITOR=/usr/bin/vim >> ~/.bashrc 
```



2、删除 nano 编辑器

```shell
sudo apt-get remove nano 
```

