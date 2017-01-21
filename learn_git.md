# learn_git

- 分布式版本控制系统

## 创建版本库(repository)
`mkdir learn_git` 新建文件夹
`cd learn_git` 切换目录
`pwd` 显示当前路径

----

`git init` 把当前目录变成Git可以管理的仓库
对这个文件夹内的文件进行操作之后
`git add readme.md` add操作添加文件到仓库
`git commit -m "readme file added"` commit操作提交文件到仓库
> git commit命令，-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。
>
> ![git-repo](http://www.liaoxuefeng.com/files/attachments/001384907702917346729e9afbf4127b6dfbae9207af016000/0)
>
> 工作区(working directory) 
>
> 版本库(repository)， 包含暂存区(stage)和当前分支(master)
>
> add是将working directory文件添加到stage，commit将stage提交到master
>
> 
>
> 

## 版本控制

`git status` 显示仓库当前状态，哪些文件有改动

`git diff readme.md` 显示具体改动

> 一般确认改动是什么之后再commit

> 多次commit（多个版本）之后，想要回退到某个版本

`git log` 查看历史版本信息（版本号，作者信息，修改日期，版本说明）

> $ git log
> commit 5b7b171dec30ccbcc390ccd09dd88e85e5385346  **（版本号）**
> Author: HaipengLi <si_shen_shang@163.com>
> Date:   Sat Jan 21 14:23:12 2017 +0800
>
>     change for the first time
>
> commit 2b069c7755e8000222196d9a6c829e94e80f16cc
> Author: HaipengLi <si_shen_shang@163.com>
> Date:   Sat Jan 21 13:23:56 2017 +0800
>
>     wrote a diary
> 

也可用`git log --pretty=oneline`查看精简版信息（仅有版本号和版本说明）

> 5b7b171dec30ccbcc390ccd09dd88e85e5385346 change for the first time
> 2b069c7755e8000222196d9a6c829e94e80f16cc wrote a diary

`git reset --hard HEAD^` 回退到当前版本的前一个

> HEAD 为当前版本指针，^代表前一个，^^代表前前一个，HEAD~100代表100个之前的

回退之后，如果还想撤回回退，则需要采用`git reset --hard 5b7b17 ` （只需要输入版本号前几位即可）,最新版本的版本号除了可以爬楼看以外，还可以使用`git reflog` 查看

> 2b069c7 HEAD@{0}: reset: moving to HEAD^
> 5b7b171 HEAD@{1}: commit: change for the first time
> 2b069c7 HEAD@{2}: commit (initial): wrote a diary

## 撤销修改（三个场景）

> Git管理的是修改，而不是文件

----

### c1: 还未add

> 情形： 对当前working directory修改不满意，想要放弃修改，即恢复上一次commit或者是add的状态（取最新）

`git checkout -- learn_git.md` 将最近一个add或者commit的文件恢复到working directory中，即放弃当前对working directory中某文件的修改

----

### c2: added, 还未commit

`git reset HEAD learn_git.md` 可以将master中已经commit的文件恢复到stage。之后可用`git checkout -- learn_git.md` 将文件再恢复到working directory

---
### c3: commited
只能采用版本回退，即`git reset --hard HEAD^`

## 删除文件

`git rm python_learning_di` 删除某文件在stage中