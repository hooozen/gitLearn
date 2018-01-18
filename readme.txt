Git is a distributed version control system.
Git is free software distributed under the GPL.

git status # 查看当前状态
git diff # 查看修改内容
git reset --hard HEAD^ # 回退到上一个版本
git reset --hard HEAD^^ # 回退到上上个版本
git reset --hard HEAD~n # 回退到倒数第 n 个版本
git log # 查看历史提交记录 --pretty=online 简略信息
git reflog # 查看历史操作记录 可以查看每次提交的 commit id
git reset --hard [commint id] # 回退/恢复至指定 commit id 的版本

# 修改是在工作区，add 后文件提交到暂存区，commit 后暂存区内容提交到分支
add 命令将文件内容从工作去提交到暂存区
commit 命令将暂存区的文件一次性提交到分支


git diff HEAD -- fileName # 查看当前分支和当前文件内容的不同

git checkout -- fileName # 撤销工作区的更改(包括删除操作)


#### 远程库

git remote add origin [url] # 添加远程仓库命名为 origin 

git push -u origin master # 将本地分支推送到 origin 远程仓库。当第一次推送时，使用 -u 将本地仓库和远程仓库关联起来

git push origin master # 将本地分支推送到指定远程仓库分支 
