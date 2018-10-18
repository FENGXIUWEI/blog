---
title: git的基本使用
date: 2018-10-18 09:01:13
tags:
- git
categories:
- git
---
#### 工作区，暂存区和版本库
工作区：就是你在电脑上看到的目录，比如目录下testgit里的文件（.git隐藏目录版本库除外）。或者以后需要再新建的目录文件等等都属于工作区的范围
版本库(Repository)：工作区有一个隐藏目录.git,这个不属于工作区，这是版本库。其中版本库里面存了很多东西，其中最重要的就是stage(暂存区)，还有Git为我们自动创建了第一个分支master,以及指向master的一个指针HEAD。
#### git提交文件到版本库的步骤
第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。
第二步：使用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支上。
#### git的基本操作
+ 填写用户名和邮箱
![git](/images/git/git_global.png)
注意：git config  --global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。
+ 通过命令 git init 把这个目录变成git可以管理的仓库
![git](/images/git/git_git.png)
+ 从现有仓库克隆`git clone [github仓库]`
![git](/images/git/git_clone.png)
+ 把项目文件夹下面的文件都添加进来`git add .`
![git](/images/git/git_add.png)
+ 准备提交暂存区中的更改的已跟踪文件`git commit -m "你的信息"`
![git](/images/git/git_commit.png)
+ 把本地仓库push到github上面`git push -u origin master`
![git](/images/git/git_push.png)
+ 进入github官方网站https://github.com/，本地信息已经提交到了github
![git](/images/git/git_github.png)

#### 常用命令
+ 克隆文件
`git clone git@github.com:XXX/yyyy.git //XXX为github的用户名，yyy为仓库名`
+ 提交
```python
git add mmm.sss //mmm为文件名称，sss为文件拓展名（常用git add .）
git commit -m "hhh" //hhh为git commit 提交信息，是对这个提交的概述
git log//用于查看提交日志
git push //更新GitHub上的仓库
```
+ 用git创建仓库
```python
mkdir nnn //仓库名
cd hhh
git init //初始化仓库
git status //查看仓库状态
touch README.md //创建READEME.md文件
git add ERADME.md //添加ERADME.md至暂存区
git commit -m "hhh" //如果想要提交信息记录的更详细，请不要加 -m
git log --pretty=short //加--pretty=short 只显示提交信息的第一行
git log ggg //ggg是指指定的文件或目录，用于查看指定的目录、文件的日志
git log -p //查看提交所带来的改动
git log -p ggg //查看指定文件的改动
git diff //可以查看工作树，暂存区，最新提交之间的差别
git diff HEAD //查看工作树与最新提交的差别
```
+ 分支操作
```python
git branch //显示分支一览表，同时确认当前所在的分支
git checkout -b aaa //创建名为aaa的分支，并且切换到aaa分支
git checkout - //切换到上一分支
```
+ 合并分支
```python
git checkout master //切换到master分支
git marge --no--ff aaa // 加--no--ff 参数可以在历史记录中明确地记录本次分支的合并
git log --graph //以图表形式查看分支
```
+ 更改提交的操作
```python
git reset //回溯历史版本
git reset --hrad //回溯到指定状态，只要提供目标时间点的哈希值
```
+ 推进历史
```python
git reflog //查看仓库的操作日志，找到要推历史的哈希值
git checkout master
git reset --hrad ddd //ddd为要推进历史的哈希值
```
+ 修改提交信息 git commit --amend
```python
压缩历史 git rebase -i 错字漏字等失误称作typo
根据以前的步骤在GitHub上创建仓库，应于本地的仓库名相同 GitHub上面创建的仓库的路径为git@github.com: 用户名/仓库名.git
git remote add eee git@github.com: 用户名/仓库名.git //添加远程仓库，并将git@github.com: 用户名/仓库名.git远程仓库的名称改为eee
git push -u eee master //推送至远程仓库 master分支下 -u 参数可以在推送的同时，将eee仓库的master分支设置为本地仓库的当前分
支的的upstream（上游）。添加这个参数，将来运行git pull命令从远程仓库获取内容时，本地仓库的这个分支就可以直接从eee的master
分支中获取内容
git checkout -b feature d eee/feature d //获取远程的feature d分支到本地仓库，-b参数后面是本地仓库中新建的仓库的名称
git pull eee feature d //将本地的feature d分支更新为最新状态
在GitHub上面查看两个分支之间的差别，只需要在地址栏中输入http://github.com/用户名/仓库名/分支1...分支2
```
#### 使用gitHub进行合作开发
+ Collaborators
![git](/images/git/git_collaborators.png)
+ Fork & Pull request
fork：在下载别人的 repo 之前，需要创建一个分支，它是别人项目的个人副本。分支是原始 repo 和个人副本之间的桥梁。在 repo 的右上角有一个 Fork 按钮，点击它创建一个分支。
![git](/images/git/git_Fork.png)
![git](/images/git/git_pullrequests.png)

