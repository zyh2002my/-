# Git版本控制

## 1 版本控制

​        版本控制是指对软件开发过程中各种程序代码、配置文件及说明文档等文件变更的管理，是软件配置管理的核心思想之一。

​        版本控制最主要的功能就是追踪文件的变更。它将什么时候、什么人更改了文件的什么内容等信息忠实地了记录下来。每一次文件的改变，文件的版本号都将增加。除了记录版本变更外，版本控制的另一个重要功能是并行开发。软件开发往往是多人协同作业，版本控制可以有效地解决版本的同步以及不同开发者之间的开发通信问题，提高协同开发的效率。并行开发中最常见的不同版本软件的错误(Bug)修正问题也可以通过版本控制中分支与合并的方法有效地解决。

## 2 版本控制工具

**cvs：**是一个c/s结构的版本控制软件，主要用于开源的软件管理，是多个开发人员通过一个版本控制中心系统来记录文件版本，从而达到保证文件同步的目的，是一种很老的集中式版本控制工具。由于之前CVS编码的问题，现在大多数软件开发公司都使用SVN代替了CVS。

**svn：**是一个开放源代码的版本控制系统，通过采用分支管理系统的高效管理，简而言之就是用于多个人共同开发同一个项目，实现共享资源，实现最终集中式的管理。

集中式版本管理工具：

缺点：代码集中于SVN服务器上，一旦发生问题，很难挽回

优点：代码集中于SVN服务器上，不会发生个别新手污染代码的情况

**Git：**是一个开源的分布式版本控制系统，可以有效、高速地处理从很小到非常大的项目版本管理。

## 3 Git命令

-  需要把当前的目录转换为git仓库

```
git init
```

- 创建Git项目提交身份

```
配置局部身份：
git config user.name 名称 ——》 设置提交名
git config user.email 123@qq.com ——》设置提交邮箱
cat .git/config——》查看局部提交身份

配置全局身份：
git config --global user.name 名称 ——》设置全局提交名
git config --global user.email 123@qq.com ——》设置全局提交邮箱
git ~/.gitconfig——》查看全局提交身份
```

- 查看当前版本的状态

```
git status 
```

- 把文件修改或者添加到仓库，多个文件名字用空格隔开

```
git add 1.txt    【git add .  提交所有文件】
```

- 将文件提交到本地库，并添加描述

```
git commit -m '描述内容'
```

- 查看工作目录和暂存区域之间的差异

```
git diff
```

- 显示工作版本和HEAD的差别【在.git中，有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD】

```
git diff HEAD
```

- 查看提交的log

```
git log --pretty =oneline 
```

- 回滚到上一个版本【HEAD^  回滚上一个版本，上上个就是head^^ ，如果100个，就是head~100】

```
git reset --hard
```

commit ID是一个shall算出来的串，不像是svn的1，2，3,因为git 是分布式的。每一个commit都是存档，如果要回滚的话，只能从 commit来回滚 ，最上面的是最新的修改对于已经回滚的 commit ，如果关机了，可以通过 `git reflog` 来找commitID ，查看命令log。

- 创建分支

```
git branch 分支名称
```

- 查看分支

```
git branch -v
```

- 切换分支

```
git checkout 分支名称
```

- 合并分支

```
git merge 分支名称
```

- 在合并分支是有可能线上的版本与你本地缓存区的版本不一致，或者多人同时提交时，造成合并冲突。流程如下：

```
以将online合并到master上为例。文件名（1.txt）
1，进行合并
	git merge online
2，进入冲突文件，进行手动的代码调整
	vim 1.txt——调整代码
3，进行add将冲突文件添加到缓冲区
	git add 1.txt
4，进行commit提交，注意不要指定具体提交的文件名称
	git commit -m “描述”
冲突解决完成
```

- 在上面第二步vim 打开的是一个文件编辑器，命令如下。

```
cat 1.txt 查看文件
cat>>1.txt 编辑文件，使用ctrl + z退出编辑模式
或者：
vim 1.txt 进入编辑器，按i进行编辑，esc后wq保存并退出，q退出，q!强制退出
```

- 将当前分支推送到远程，-u把远程和本地的master关联起来

```
git push -u origin master
```

- 克隆远程到本地

```
git clone <远程地址>
```

- 查看合并分支图


```
git log --graph
```

- 删除分支


```
git branch -d <分支名称>
```

- 查看保存的工作现场

```
git stash list

Git把stash内容存在某个地方了，但是需要恢复一下，有两个办法：
一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；
另一种方式是用git stash pop，恢复的同时把stash内容也删了
```

## 4 Git多人协作

- ##### 当我们第一次想要向远程提交文件。

1. 克隆项目

```
git clone 项目ip
```

2. 创建新的分支，用来同步新的数据

```
git branch <分支名称>
```

3. 给更新的远程库起别名[此步可选择不写，仅仅是为了之后同步方便(不用再复制网址)]

```
git remote add <别名>  <远程地址>
```

4. 切换分支，来同步数据库

```
git  checkout 分支名称
```

5. pull 远程库的项目

```
git pull 远程库地址 // git pull 别名
```

6. 切换到master

```
git checkout master
```

7. 合并分支

```
git merge 分支名
```

8. 更改合并产生的冲突【没有冲突，忽略此步】

```
vim 冲突文件
```
9. 确认master分支下的为最新版本

```
git add .
```
10. 添加此次修改的描述

```
git commit -m  ‘描述内容’
```
11. 更新到远程库

```
git push origin master
```

- ##### 再次提交时，就不需要如此麻烦，我们直接push就可以了

1. 首先，可以试图用git push origin <branch-name>推送自己的修改；

```
git push origin master  
```

2. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

```
git  checkout 分支名称
git pull 远程库地址 // git pull 别名
git checkout master
git merge 分支名
```

3. 如果合并有冲突，则解决冲突，并在本地提交；

```
vim 冲突文件
```

4. 没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

```
git push origin master
```

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令

```
git branch --set-upstream-to <branch-name> origin/<branch-name>。
```

Git分支十分强大，在团队开发中应该充分应用。
合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

* master分支是主分支，因此要时刻与远程同步；

* dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；

* bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；

* feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。









