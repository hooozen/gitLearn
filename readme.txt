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

add 命令将文件内容提交到暂存区
commit 命令将暂存区的文件一次性提交到分支