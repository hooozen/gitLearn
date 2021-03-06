# 分支
  
## 常用操作
  
``` git checkout -b dev ```
创建并切换到 dev 分支，相当于执行了下面两条命令
```
 git branch dev 
 git checkout dev 
```
  
` git log --graph `  

查看分支合并示意图，同时可以使用 `--pretty=oneline` 参数简化显示内容，使用 `--abbrev-commit` 参数缩写 commit id



` git branch ` 

查看当前分支，该命令会列出所有分支，在当前分支前会有一个 * 号
  
  
` git merge dev `

合并 dev 分支到当前分支
  
  
` git branch -d dev `

合并 dev 到 master 后即可把 dev 分支删除掉
  
  
  
## 分支命令小结

` git branch ` 查看分支
  
` git branch <name> ` 创建分支
  
` git checkout <name> ` 切换分支
  
` git checkout -b <name> ` 创建并切换分支
  
` git merge <name> ` 合并指定分支到当前分支
  
` git branch -d <name> ` 删除指定分支
  
## 分支管理策咯

### 快速合并

一般情况下合并分支，Git 会使用 `Fast forward` 模式，
这种模式下分支历史不会记录分支合并记录，即使用 `git log --graph` 无法查看合并历史记录
在分支被删除后就会丢掉分支信息。


### 禁止快速合并

在合并分支时使用 `--no-ff` 参数会禁用 `Fast forward` 模式

` git merge --no-ff -m "somte info" dev `

这样 Git 会在 merge 时生成一个新的 commit，从分支历史上就可以查看分支信息
  
因为此时 Git 会自动生成一个新的 commit，所以记得使用 -m 添加描述信息



## 分支策略

在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master 分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在 dev 分支上，也就是说，dev 分支是不稳定的，到某个时候，比如1.0版本发布时，再把 dev 分支合并到 master 上，在 master 分支发布1.0版本；

你和你的小伙伴们每个人都在 dev 分支上干活，每个人都有自己的分支，时不时地往 dev 分支上合并就可以了。