origion config

Git push远程仓库总是需要账号密码
https://blog.csdn.net/sysu_cm/article/details/60348366

use ssh way
coupy the ssh link


## add ssh
ssh-keygen -t rsa -C "yefcion@163.com"


先 pull 了一个项目之后
添加了一个文件 add 后 pull 没反应
            commit 后依然没反应
修改了一个文件 add 后 pull 没反应
            commit 后依然没反应

当云端和本地更改了同一个文件时，本地 pull 会引发冲突
需要在本地修改冲突内容在重新 add commit push


# 分支相关的 git 使用
## 新建并转到该分支
git branch -b win			# 新建并转到 win 分支

git branch win				# 创建 win 分支

git checkout win			# 转到 win 分支

git merge win               # 把 win 分支合到当前分支

git branch -d win           # 删除分支 win


我的 Git 使用说明
### Git 相关
git config --list				# 列出所有 Git 当时能找到的配置  
git config --global user.name 许传浩10261177  
git config --global user.email xu.chuanhao@zte.com.cn  
git config <key>				# 来检查 Git 的某一项配置  
ssh-keygen -t rsa -C "xu.chuanhao@zte.com.cn" 		# 生成 ssh-key 填到 gerrit 上的对应位置

git status						# 检查当前文件状态  
git diff						# 查看尚未暂存的文件更新了哪些部分  
git add <filename>				# 添加 <> 文件  
git add .
git commit -m '说明'			# commit 并填写修改说明  
git commit -a -m ""				# 无需 add 直接提交  
git commit -amend				# 覆盖上一次提交  

git log 						# 会按提交时间列出所有的更新  
git log --stat					# 简洁显示  
git log --pretty=format:"%an"	# 查看日志中，提交作者名称  

git reset --hard <commit-ID>	# 回到指定版本

git branch						# 查看当前分支
git branch -a					# 查看所有分支
git checkout <分支名>			# 切换分支（origin 后面部分）








https://www.cnblogs.com/hcxy/p/7414705.html
git pull与本地修改冲突

1、先将本地修改存储起来，注意一定要先 add

$ git stash

这样本地的所有修改就都被暂时存储起来 。

 $ git stash list                 可以看到保存的信息：

git stash暂存修改

其中stash@{0}就是刚才保存的标记。

2、pull内容

暂存了本地修改之后，就可以pull了。

$ git pull
3、还原暂存的内容

$ git stash pop stash@{0}
系统提示如下类似的信息：

Auto-merging c/environ.c
CONFLICT (content): Merge conflict in c/environ.c
意思就是系统自动合并修改的内容，但是其中有冲突，需要解决其中的冲突。

4、解决文件中冲突的的部分

打开冲突的文件，会看到类似如下的内容：

 


git冲突内容


其中Updated upstream 和=====之间的内容就是pull下来的内容，====和stashed changes之间的内容就是本地修改的内容。碰到这种情况，git也不知道哪行内容是需要的，所以要自行确定需要的内容。

 

解决完成之后，就可以正常的提交了。

 

5 删除stash。git stash drop <stash@{id}>  如果不加stash编号，默认的就是删除最新的，也就是编号为0的那个，加编号就是删除指定编号的stash。git  stash clear 是清除所有stash,整个世界一下子清净了！
