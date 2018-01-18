# SoftWare Description
* Git is a distributed version control system.
* Git is free software distributed under the GPL.

## 基本命令
* git status # 查看当前状态
* git diff # 查看修改内容
* git reset --hard HEAD^ # 回退到上一个版本
* git reset --hard HEAD^^ # 回退到上上个版本
* git reset --hard HEAD~n # 回退到倒数第 n 个版本
* git log # 查看历史提交记录 --pretty=online 简略信息
* git reflog # 查看历史操作记录 可以查看每次提交的 commit id
* git reset --hard [commint id] # 回退/恢复至指定 commit id 的版本

## 工作区 暂存区 分支
* 修改是在工作区，add 后文件提交到暂存区，commit 后暂存区内容提交到分支
* add 命令将文件内容从工作去提交到暂存区
* commit 命令将暂存区的文件一次性提交到分支

* git diff HEAD -- fileName # 查看当前分支和当前文件内容的不同

* git checkout -- fileName # 撤销工作区的更改(包括删除操作)


## 远程仓库


* ssh-keygen -t rsa -C "name@email.com" # 生成 SSH key，windows 使用 git bash 执行该命令 # 生成 SSH key，windows 使用 git bash 执行该命令。文件生成在用户目录下的 .ssh 文件夹

* git remote add origin [url] # 添加远程仓库命名为 origin 

* git push -u origin master # 将本地分支推送到 origin 远程仓库。当第一次推送时，使用 -u 将本地仓库和远程仓库关联起来

* git push origin master # 将本地分支推送到指定远程仓库分支 

* git clone [url] # 从 url 克隆远程仓库至本地


## 分支

` git checkout -b dev `
创建并切换到 dev 分支，相当于执行了下面两条命令
` git branch dev `
` git checkout dev `

` git branch ` 
查看当前分支，该命令会列出所有分支，在当前分支前会有一个 * 号

` git merge dev `
合并 dev 分支到当前分支

` git branch -d dev `
合并 dev 到 master 后即可把 dev 分支删除掉

### 分支命令小结
` git branch ` 查看分支
` git branch <name> ` 创建分支
` git checkout <name> ` 切换分支
` git checkout -b <name> ` 创建并切换分支
` git merge <name> ` 合并指定分支到当前分支
` git branch -d <name> ` 删除指定分支