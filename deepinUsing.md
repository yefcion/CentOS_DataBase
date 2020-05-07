# 软件相关
```shell
# 安装软件
sudo apt-get install <name>

# 卸载软件
sudo apt-get --pruge remove <name>

# 更新软件
sudo apt-get update

# 软件列表
dpkg --list
Software List
```




# 系统相关软件升级

安装方式：
到火狐官网 下载最新版本烦人火狐浏览器，得到的是一个压缩包，解压得到一个文件夹（文件夹名firefox），将文件夹改名为firefox-zh，然后用管理员身份打开根目录下的文件夹 /usr/lib/，将其中的文件夹firefox-zh改名为firefox-zh-old（防止操作失败，如此改名权当备份），然后复制前面下载解压并改名得到的文件夹firefox-zh复制到/usr/lib/中，搞定。

# 安装包安装
NutStore 坚果云
地址：https://www.jianguoyun.com/s/downloads/linux
安装方式：双击安装
https://www.jianguoyun.com/s/downloads/linux

Electron-ssr 代理软件
地址：https://www.jianguoyun.com/p/Datu08sQn7KEBxjv6aAC
安装方式：双击安装


Deepin系统安装软件的方法总结 2019-7-22 19:47 
https://bbs.deepin.org/forum.php?mod=viewthread&tid=181002




# 修改默认编辑器为 vim
1、修改配置
echo export EDITOR=/usr/bin/vim >> ~/.bashrc 
2、删除 nano 编辑器
sudo apt-get remove nano 




# 安装 pip3 
sudo apt install  python3-pip
