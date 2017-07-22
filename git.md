# git

* `mkdir 目录名`：新建目录，目录名一般为仓库名，或者项目名。
* `cd 目录名`：进入仓库
* `git init`：将这个仓库交给git管理
* `git log`：查看commit日志
* `git status`：查看git状态
* `git add`：将文件放在暂存区
* `git commit`：将暂存区文件提交到本地
* `git remote add origin 仓库地址`：给本地仓库添加远程仓库
* `git remote rm origin`：删除远程仓库（origin 上边添加的时候就命名的origin）
* `git push -u origin master`：第一次将文件提交到远程仓库，需要指定仓库分支（当前为origin/master分支）
* `git push`：将文件提交的远程仓库
* `git checkout -- file`：让这个文件回到最近一次git commit或git add时的状态。`--`很重要，如果没有它，就变成切换到另一个分支了。
* `git reset HEAD file`：将暂存区中关于file的修改撤销掉，这些修改还在工作区
* `git reset --mixed commitID`：重置HEAD到另外一个commit,并且重置index（暂存区）以便和HEAD相匹配，工作区的内容不变。（--mixed为默认的，可以不带）
* `git reset --hard commitID`：重置HEAD到另外一个commit,并且重置index以便和HEAD相匹配，工作区的内容也恢复到commitID
* `git reset --soft commitID`：重置HEAD到另外一个commit其它不变

> 其实就是--soft 、--mixed以及--hard是三个恢复等级。使用--soft就仅仅将头指针恢复，已经add的缓存以及工作空间的所有东西都不变。如果使用--mixed，就将头恢复掉，已经add的缓存也会丢失掉，工作空间的代码什么的是不变的。如果使用--hard，那么一切就全都恢复了，头变，add的缓存消失，代码什么的也恢复到以前状态。

* `git revert commitID`：将commitID的修改恢复，然后创建一个新的提交。相当于只撤销了commitID的提交，然后又commit一次。
* `git rm file`：当我们删除一个文件后，需要使用此命令把版本库的也删除，然后再commit
* `git branch dev`：创建dev分支
* `git branch -d dev`：删除dev分支
* `git branch -D dev`：强行删除dev分支，即使有修改没有被提交
* `git branch`：查看所有分支
* `git checkout dev`：切换到dev分支
* `git checkout -b dev`：创建dev分支并切换到dev相当于：`git branch dev 与 git checkout dev`两条命令
* `git merge dev`：命令用于合并指定分支到当前分支，将dev分支合并到当前分支
* `git merge --no-ff -m "merge with no-ff" dev`：在merge时生成一个新的commit，因此需要`-m ""`。这样的话，如果我们删除了dev，依然能在tree上看到dev。 `--no-ff`代表不使用快速提交
* `git stash`：将当前分支保存现场，虽然当前分支的改变没有提交，但是此操作后依然可以切换到其它分支
* `git stash apply`：恢复现场，但是之前的保存没有删除
* `git stash drop`：将保存的内容删除
* `git stash pop`：恢复现场并删除保存的内容
* `git stash list`：查看stash的内容
* `git remote -v`：查看远程仓库名称，显示可以抓取和推送的远程地址，如果没有push权限则不会显示push地址。
* `git push origin master`：推送到远程master分支，origin，需要与添加的一致。`git push origin dev`推送到dev分支
* `git branch --set-upstream dev origin/dev`：将本地dev分支track到远程origin/dev。这样他们就建立了关系，这样我们才能`git pull`,`git push`
* `git tag <name>`：在当前分支创建tag
* `git tag v1.0 65235`：指定commit版本打tag，将65235打 v1.0 tag
* `git tag -a v0.1 -m "version 0.1 released" 65235`：打标签，指定说明文字，-a 指定标签名，-m 指定文字
* `git tag`：查看标签
* `git show v1.0`：查看v1.0的标签
* `git tag -d v0.1`：删除v0.1标签
* `git push origin v1.0`：将v1.0推送到远程
* `git push origin --tags`：一次性推送全部尚未推送到远程的本地标签
* 删除远程标签：`git tag -d v1.0`然后`git push origin :refs/tags/v1.0`，需要两步操作


