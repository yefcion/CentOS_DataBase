# 软件相关
```shell
# 安装软件
sudo apt-get install <name>

# 卸载软件
sudo apt-get --pruge remove <name>

# 更新软件
sudo apt-get update
sudo apt-get upgrade

# 软件列表
dpkg --list
Software List
```




# 系统相关软件升级

安装方式：
到火狐官网，下载最新版本火狐浏览器，得到的是一个压缩包，解压得到一个文件夹（文件夹名firefox），将文件夹改名为firefox-zh，然后用管理员身份打开根目录下的文件夹 /usr/lib/，将其中的文件夹firefox-zh改名为firefox-zh-old（防止操作失败，如此改名权当备份），然后复制前面下载解压并改名得到的文件夹firefox-zh复制到/usr/lib/中，搞定。

# 安装包安装
NutStore 坚果云

地址：https://www.jianguoyun.com/s/downloads/linux

下载 Ubuntu 版本

安装方式：https://www.cnblogs.com/gaodp/p/12840020.html


Sublime Text3
官方安装教程：
http://www.sublimetext.com/docs/3/linux_repositories.html

install package
```bash
import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```


Electron-ssr 代理软件
地址：https://www.jianguoyun.com/p/Datu08sQn7KEBxjv6aAC
安装方式：双击安装


Deepin系统安装软件的方法总结 2019-7-22 19:47 
https://bbs.deepin.org/forum.php?mod=viewthread&tid=181002




# 修改默认编辑器为 vim
```shell
# 1、修改配置
echo export EDITOR=/usr/bin/vim >> ~/.bashrc 
# 2、删除 nano 编辑器
sudo apt-get remove nano 
```




# 安装 pip3 
```shell
sudo apt install  python3-pip
```

软件列表：
 - 火狐/Chrome
 - VSCode
 - Sublime
 - 坚果云
 - Typora
 - electron-ssr
 - 自带输入法很好，不需要换