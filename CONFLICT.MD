# 分支冲突
如果在两个分支中分别更改了同一个文件，并提交。
当合并分支时便会发生冲突，git 会用

` <<<<<< HEAD
 some text in HEAD branch
 =======
 some text different from HEAD in some branch
 >>>>>> some `

提示冲突内容，手动修改冲突内容后 add 并 commit 修改即可解决冲突
冲突解决后，删除分支即可。