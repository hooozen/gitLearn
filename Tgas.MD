# 标签管理
标签相对 commit id 具有更好的标识度和语义化，可以方便团队交流和项目版本升级维护。

## 基本命令 
  
* 创建标签
``` git tag v1.0 ```
该标签会打在当前分支最新的 commit 上。

  
* 为历史提交追加标签  
``` git tag V0.9 [commit-id] ```
通过 commit-id 可以为任一历史 commit 追加标签
  
查看commit id 的命令回顾：
``` git log --pretty=oneline --abbrev-commit ```

  
* 查看标签
``` git tag ```
该命令查看所有的标签（按字母序排列）
  
``` git show v0.9 ```
查看指定标签的信息
  
  
## 其他命令

* 添加说明信息
``` git tag -a v0.1 -m "version 0.8 released" [commit-id] ```
使用 -a 指定标签名，-m 指定说明信息，则可创建带有说明信息的标签。
使用 `git show [tagname]` 命令查看时则可以看到说明信息了。
  
* 创建标签签名
``` git tag -s v0.7 -m "signed version 0.7 released" [commit-id] ```
使用 `-s` 参数则可以在创建标签时添加签名信息
需要注意的是，签名需要安装 gpg(Gnupg)，如果未安装则会报错。


## 删除和推送
标签默认存储在本地，除非手动推送，不会被提交到远程。
  
### 命令
  
* 命令 `git push origin <tagname>` 可以推送一个本地标签；
  
* 命令 `git push origin --tags` 可以推送全部未推送过的本地标签；
  
* 命令 `git tag -d <tagname>` 可以删除一个本地标签；
  
* 命令 `git push origin :refs/tags/<tagname>` 可以删除一个远程标签。


  
  
  
## 安装使用 Gnupg
  
* 安装
``` sudo apt install gnupg ```
  
* 生成 key
``` gpg --gen-key```
根据提示操作即可
  
* 查看 key
``` gpg --list-keys ``
正确输出密钥则证明密钥生成成功，则可使用 gpg 为标签签名
  
* 注意
如果生成密钥成功后仍提示签名失败，可尝试指定密钥
``` git tag -u [name] -s v0.7 -m "tag message" [commit-id] ```
`[name]` 为生成密钥时要求输入的真实姓名