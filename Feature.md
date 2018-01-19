# Feature 分支

## 场景描述

开发过程中会有很多新功能添加进来。

在主分支上进行修改是不合适的，因为新的功能稳定性不够好，并且不一定最终要发布。所以应该在分支上进行开发，开发完成后再合并到主分支，最后删除该分支。

## 推荐流程

1. 准备开发新 Feature



2. 新建分支进行开发 

`git checkout -b feature-vulcan`



3. 开发完毕，提交更改 
```
add .
commit -m 'add feature vulcan
```


4. 切回 dev 分支

`git checkout dev`



#### 情况一 该功能被分析可以添加到分支

5. 合并 feature-vulcan 分支

`git merge --no-ff -m "add feature vulcan" feature-vulcan`



6. 删除分支，完成工作

`git branch -d feature-vulcan`



#### 情况二 该新功能被抛弃

5. 删除被抛弃的 feature-vulcan 分支

`git branch -d feature-vulcan`



6. 此时会发现删除失败，因为分支还没有被合并，需要强制删除

`git branch -D feature-vulcan`
