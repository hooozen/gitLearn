# Bug 分支

## 问题背景

开发过程中难免遇到 Bug，有了 Bug 就得即使修复。

但是如果此时开发者正在开发的分支还有工作没有完成，不能 commit 代码。

并且当前分支有未 commit 的内容时，Git 是不允许切换分支的，它会提醒类似下面的内容：

```
error: Your local changes to the following files would be overwritten by checkout:
        Bug.MD
Please commit your changes or stash them before you switch branches.
Aborting
```

但是 Bug 需要立刻修复，你需要切换到 master 分支新建新的 Bug 分支修复 Bug 后将分支合并到 master，而前分支的工作未完成，无法直接切换到 master 分支。

## 解决方法

` git stash `

使用该命令能将当前工作现场“储藏”起来，此后便可以顺利切换到 master 分支了。

当 Bug 修复完毕，再次切换到之前的工作分支，会发现之前未 commit 内容都不见

此时只需要使用 `git stash list` 查看存储的工作现场。

使用 `git stash apply` 恢复上一次“储藏”的工作现场，或者使用 `git stash pop` 弹出上一次“储藏”的工作现场，然后就能继续对修复 Bug 之前的内容进行开发了。

### git stash 命令总结

` git stash `

将当前工作区内容暂存起来，便于切换到其他分支


` git stash list `

查看曾存储的工作现场


#### 恢复工作现场

由于从其他分支再切换回来时，原来未 commit 的内容都会消失，所以需要将之前存储的工作现场恢复出来


` git stash apply `

恢复最后存储的工作现场


` git stash pop `

弹出最后存储的工作现场，和 `git stash apply` 命令的区别是，该命令恢复工作现场的同时会删除记录，即使用 `git stash list` 无法查询到该工作现场了。


` git stash apply stash@{0} `

当存储了多个工作现场时，可以使用该命令恢复指定的工作现场。序号使用 `git stash list` 查看。

## 修复 master 分支上 Bug 的推荐流程

0. 假设当前工作分支为 dev

1. 将当前工作区暂存起来 `git stash`

2. 切换到 master 分支 `git checkout master`

3. 新建并切换到临时分支以进行 Bug 修复 `git checkout -b 'issue-101'`

4. 在 issue-101 分支上对 Bug 进行修复

5. Bug 修复完成后 add 并 commit 修改

6. 切换到 master 分支 `git checkout master`

7. 合并 issue-101 分支到 master 分支已完成 Bug 的修复 `git merge --no-ff -m 'fix issue 101' issue-101`

8. 删除 issue-101 临时分支 `git branch -d 'issue-101'`

9. 切换会 dev 分支 `git checkout dev`

10. 恢复之前存储的工作现场 `git stash pop`