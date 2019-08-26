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
