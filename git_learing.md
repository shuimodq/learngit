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
## 修改操作小结
1. 场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
2. 场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD <file>，就回到了场景1，第二步按场景1操作。
3. 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。
### 创建合并分支
1. git checkout -b 创建并切换 = git branch + git checkout
$ git checkout -b dev
2. 


