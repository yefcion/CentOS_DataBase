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
