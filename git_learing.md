# Git学习
## 创建版本库
1. git init
$ git add readme.txt
2. git add
$ git commit -m "wrote a readme file"
## 基本操作
1. git status 查看仓库当前的状态
2. git diff 查看修改内容
$ git diff readme.txt
## 版本回退
1. git log 查看历史
2. git log --pretty=oneline 简约版
3. git reset --hard HEAD^ 回退到上个版本
4. git reset --hard 1094a 回退到commit id对应放入版本
5. git reflog 查看版本记录
ps： 当回退版本后，找不到新版本的commit id时使用查找需要的commit id
6. git checkout -- file  撤销修改(缓存前)
$ git checkout -- readme.txt
7. git reset HEAD <file>  把暂存区的修改撤销掉（unstage），重新放回工作区
++ git checkout -- file
$ git reset HEAD readme.txt
$ git checkout -- readme.txt
8. git rm 删除文件
$ git rm test.txt
9. git checkout 删错了恢复
$ git checkout -- test.txt
ps： git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。
### 修改操作小结
1. 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
2. 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
3. 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
## 创建合并分支
1. 查看分支：git branch
2. 创建分支：git branch <name>
3. 切换分支：git checkout <name>
4. 创建+切换分支：git checkout -b <name>
5. 合并某分支到当前分支：git merge <name>
6. 删除分支：git branch -d <name>
## 解决冲突
1. 查看分支合并情况： git log --graph --pretty=oneline --abbrev-commit
2. 当merge发生冲突时，Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，需要手动修改文件。
## 分支管理
1. 分支合并时，git默认会用Fast forward模式，但在这种模式下，删除分支会丢失分支信息，所以需要强制禁用Fast forward模式
2. 使用--no-ff方式的git merge，合并需要创建新的commit
$ git merge --no-ff -m "merge with no-ff" dev
## Bug分支
1. 修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。
##  Feature分支
1. 开发一个新feature，最好新建一个分支；
2. 如果要丢弃一个没有被合并过的分支，可以通过git branch -D <name>强行删除。
## 多人协作
1. 查看远程库信息，使用git remote -v；
2. 本地新建的分支如果不推送到远程，对其他人就是不可见的；
3. 从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；
4. 在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
5. 建立本地分支和远程分支的关联，使用git branch --set-upstream branch-name origin/branch-name；
6. 从远程抓取分支，使用git pull，如果有冲突，要先处理冲突。
## Rebase（有坑，慎用，会回退不了版本）
1. rebase操作可以把本地未push的分叉提交历史整理成直线；
2. rebase的目的是使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比。
## 创建标签
1. 命令git tag <tagname>用于新建一个标签，默认为HEAD，也可以指定一个commit id；
2. 命令git tag -a <tagname> -m "blablabla..."可以指定标签信息；
3. 命令git tag可以查看所有标签。
## 操作标签
1. 命令git push origin <tagname>可以推送一个本地标签；
2. 命令git push origin --tags可以推送全部未推送过的本地标签；
3. 命令git tag -d <tagname>可以删除一个本地标签；
4. 命令git push origin :refs/tags/<tagname>可以删除一个远程标签。

