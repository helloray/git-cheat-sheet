# Git Cheat Sheet 中文版 [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

-----------------

<p align="center">
    <img alt="Git" src="../Img/git-logo.png" height="190" width="455">
</p>

------------------

# Other Available Languages:
1. [Arabic Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-ar.md)
2. [English Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/README.md)
3. [Hindi Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-hi.md)
4. [Turkish Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-tr.md)
5. [Spanish Git Cheat Sheet](https://github.com/arslanbilal/git-cheat-sheet/blob/master/other-sheets/git-cheat-sheet-es.md)

Git cheat sheet 让你不用再去记所有的git命令。

欢迎贡献内容、更新语法错误，也欢迎添加你母语版本的Git cheat sheet。

---------------------

Git Cheat Sheet 中文版
=====================

### 索引
* [基础](#基础)
* [配置](#配置)
* [配置文件](#配置文件)
* [创建](#创建)
* [本地修改](#本地修改)
* [搜索](#搜索)
* [提交历史](#提交历史)
* [分支与标签](#分支与标签)
* [更新与发布](#更新与发布)
* [合并与变基](#合并与变基)
* [撤销](#撤销)
* [Git Flow](#git-flow)

---

### 基础
-----------------

<p align="center">
    <img alt="Git" src="../Img/git-basic.png" height="170" width="586">
</p>

------------------
* Workspace：工作区
* Index / Stage：暂存区
* Repository：仓库区（或本地仓库）
* Remote：远程仓库

---

### 配置

##### 列出当前配置：
```
$ git config --list
```

##### 列出repository配置：
```
$ git config --local --list
```

##### 列出全局配置：
```
$ git config --global --list
```

##### 列出系统配置：
```
$ git config --system --list
```

##### 设置用户名：
```
$ git config --global user.name “[firstname lastname]”
```

##### 设置用户邮箱：
```
$ git config --global user.email “[valid-email]”
```

##### 设置git命令输出为彩色：
```
$ git config --global color.ui auto
```

##### 设置git使用的文本编辑器设：
```
$ git config --global core.editor vi
```

---------

### 配置文件

##### Repository配置对应的配置文件路径[--local]：
```
<repo>/.git/config
```

##### 用户全局配置对应的配置文件路径[--global]：
```
~/.gitconfig
```

##### 系统配置对应的配置文件路径[--local]：
```
/etc/gitconfig
```

----------

### 创建

##### 复制一个已创建的仓库:

```bash
# 通过SSH
$ git clone ssh://user@domain.com/repo.git

# 通过HTTP
$ git clone http://domain.com/user/repo.git

# 通过HTTP，包含子模块
$ git clone --recursive http://domain.com/user/repo.git

# 通过HTTP，获得裸版本库，裸版本库可用于搭建GIT服务器
$ git clone --bare http://domain.com/user/repo.git

# 通过HTTP ，获得裸版本库，并包含所有分支（镜像方式）
$ git clone --mirror http://domain.com/user/repo.git

```

##### 创建一个新的本地仓库:
```
# 创建新的本地仓库
$ git init

# 创建新的本地裸仓库
$ git init --bare
```

---

### 本地修改

##### 检查当前文件状态：
```
$ git status
```

##### 查看尚未暂存的文件更新了哪些部分：
```
$ git diff
```

##### 查看已暂存的文件更新了哪些部分：
```
$ git diff --staged
$ git diff --cached
```

##### 把某几个文件添加到暂存区：
```
$ git add  <file1> <file2> ...
```

##### 添加指定目录到暂存区，包括子目录
```
$ git add <dir>
```

##### 把当前所有修改添加到暂存区：
```
$ git add .
```

##### 交互式分块暂存
```
$ git add -p
```

##### 提交本地的所有修改（跳过暂存区，可以省略git add）：
```
$ git commit -a
```

##### 删除工作区文件，并且将这次删除放入暂存区
```
$ git rm <file1> <file2> ...
```

##### 停止追踪指定文件，但该文件会保留在工作区
```
$ git rm --cached <file>
```

##### 改名文件，并且将这个改名放入暂存区
```
$ git mv <file-original> <file-renamed>
```

##### 提交暂存区：
```
$ git commit
```

##### 附加消息提交：
```
$ git commit -m 'message here'
```

##### 提交本地的所有修改并附加消息：
```
$ git commit -am 'message here'
```

##### 提交，并将提交时间设置为之前的某个日期:
```
$ git commit --date="`date --date='n day ago'`" -am "Commit Message"
```

##### 修改上次提交
<em><sub>请勿修改已发布的提交记录!</sub></em>
```
$ git commit --amend
```

##### 修改上次提交的committer date：
```
$ GIT_COMMITTER_DATE="date" git commit --amend
```

##### 修改上次提交的author date：
```
$ git commit --amend --date="date"
```

##### 把当前分支中未提交的修改先储藏，再移动到其他分支：
```
$ git stash
$ git checkout branch2
$ git stash pop
```

##### 将 stashed changes 应用到当前分支：
```
$ git stash apply
```

##### 删除最新一次的 stashed changes：
```
$ git stash drop
```

---
### 搜索

##### 从当前目录的所有文件中查找文本内容：
```
$ git grep "Hello"
```

##### 在某一版本中搜索文本：
```
$ git grep "Hello" v2.5
```

---
### 提交历史

##### 从最新提交开始，显示所有的提交记录（显示hash， 作者信息，提交的标题和时间）：
```
$ git log
```

##### 显示所有提交（仅显示提交的hash和message）：
```
$ git log --oneline
```

##### 显示某个用户的所有提交：
```
$ git log --author="username"
```

##### 显示某个文件的所有修改：
```
$ git log -p <file>
```

##### 仅显示远端<remote/master>分支与远端<origin/master>分支提交记录的差集：

```
$ git log --oneline <origin/master>..<remote/master> --left-right
```

##### 谁，在什么时间，修改了文件的什么内容：
```
$ git blame <file>
```

##### 显示reflog：
```
$ git reflog show 
```

##### 删除reflog：
```
$ git reflog delete
```

---
### 分支与标签

##### 列出所有的本地分支：
```
$ git branch
```

##### 列出所有的远端分支：
```
$ git branch -r
```

##### 列出所有的本地及远端分支：
```
$ git branch -a
```

##### 切换分支：
```
$ git checkout <branch>
```

##### 切换到上一个分支：
```
$ git checkout -
```

##### 创建并切换到新分支：
```
$ git checkout -b <branch>
```

##### 创建并切换到新分支且与远程分支建立跟踪关系：
```
$ git checkout -b <branch> <remote-branch>
# 1.6.2 以上版本的 Git，还可以用 --track 选项简化
$ git checkout --track <remote-branch>
```

##### 基于当前分支创建新分支，但依然停留在当前分支：
```
$ git branch <new-branch>
```

##### 新建一个分支，指向指定commit
```
$ git branch <branch> <commit>
```

##### 新建一个分支，与指定的远程分支建立追踪关系：
```
$ git branch --track <new-branch> <remote-branch>
```

##### 建立追踪关系，在现有分支与指定的远程分支之间
```
$ git branch --set-upstream <branch> <remote-branch>
```

##### 本地分支更名：
```
$ git branch -m <old_branch> <new_branch>
```

##### 删除本地分支:
```
$ git branch -d <branch>
```

##### 强制删除一个本地分支：
<em><sub>将会丢失未合并的修改！</sub></em>

```
$ git branch -D <branch>
```


##### 给当前版本打标签：
```
$ git tag <tag-name>
```

##### 给当前版本打标签并附加消息：
```
$ git tag -a <tag-name>
```

---
### 更新与发布

##### 列出当前配置的远程仓库：
```
$ git remote -v
```

##### 显示远程仓库的信息：
```
$ git remote show <remote>
```

##### 添加新的远程仓库：
```
$ git remote add <remote> <url>
```

##### 下载远程仓库，但不合并(可利用git branch -r查看，再利用git merge合并)：
```
$ git fetch <remote>
```

##### 取回远程仓库的变化，并与本地分支合并：
```
$ git pull <remote> <branch>
```

##### 以rebase方式将远程仓库与本地合并：
```
$ git pull --rebase <remote> <branch>
```

##### 上传本地指定分支到远程仓库：
```
$ git push <remote> <branch>
```

##### 删除远程端分支：
```
#有种方便记忆这条命令的方法：记住我们不久前见过的 git push [远程名] [本地分支]:[远程分支] 语法，如果省略 [本地分支]，那就等于是在说“在这里提取空白然后把它变成[远程分支]”
$ git push <remote> :<branch> (since Git v1.5.0)
or
git push <remote> --delete <branch> (since Git v1.7.0)
```

##### 发布标签:
```
$ git push --tags
```

---
### 合并与变基(Rebase)

##### 将某分支合并到当前分支中：
```
$ git merge <branch>
```

##### 选择一个commit，合并进当前分支
```
$ git cherry-pick <commit>
```

##### 将当前分支变基到branch分支中(将当前分支的base变为branch, 再将与之相异的提交依次重演出来):
<em><sub>请勿变基已发布的提交!</sub></em>
```
$ git rebase <branch>
```

##### 退出变基:
```
$ git rebase --abort
```

##### 解决冲突后继续变基：
```
$ git rebase --continue
```

##### 比较merge和rebase:
```
在feature分支上发出合并指令git merge master：
这样会把master分支的提交合到feature自己身上，然后再创建一次合并提交，当前分支仍是feature

在master分支上发出合并指令git merge feature：
这样会把feature分支的提交合到master自己身上，然后再创建一次合并提交，当前分支仍是master

在master分支上发出变基指令git rebase feature：
这样会把master分支异于feature分支的提交接在feature之后，当前分支仍是master

在feature分支上发出变基指令git rebase master：
这样会把feature分支异于master分支的提交接在master之后，当前分支仍是feature

比较几种合代码的情况:
如果要进行merge操作的话，最好是在主分支上执行merge，把次分支的代码合进来；
如果要进行rebase操作的话，最好是在次分支上进行，把自己变基合入主分支。
次分支变基完成后，通常还需要转到主分支再次merge
$ git checkout master
$ git merge feature

```


##### 使用配置好的merge tool 解决冲突：
```
$ git mergetool
```

##### 在编辑器中手动解决冲突后，标记文件为`已解决冲突`：
```
$ git add <resolved-file>
```

```
$ git rm <resolved-file>
```

##### 合并提交：
```
$ git rebase -i <commit-just-before-first>
```

把上面的内容替换为下面的内容：

原内容：
```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>
```

替换为：
```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>
```

---
### 撤销

##### 放弃工作目录下的所有本地修改：
```
$ git reset --hard HEAD
```

##### 移除暂存区的所有文件（i.e. 撤销上次`git add`）:
```
$ git reset HEAD
```

##### 放弃某个文件的所有本地修改：
```
$ git checkout HEAD <file>
```

##### 恢复某个commit的指定文件到暂存区和工作区
```
$ git checkout [commit] [file]
```

##### 重置一个提交（通过创建一个与之相反的新提交）
```
$ git revert <commit>
```

##### 将HEAD重置到指定的版本，并抛弃该版本之后的所有修改：
```
$ git reset --hard <commit>
```

##### 用远端分支强制覆盖本地分支：
```
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature
```

##### 将HEAD重置到上一次提交的版本，并将之后的修改标记为未添加到缓存区的修改：
```
$ git reset <commit>
```

##### 将HEAD重置到上一次提交的版本，并保留未提交的本地修改：
```
$ git reset --keep <commit>
```

##### 删除添加`.gitignore`文件前错误提交的文件：
```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"
```

---

## Git-Flow

### 索引
* [安装](#安装)
* [开始](#开始)
* [特性](#特性)
* [做一个release版本](#做一个release版本)
* [紧急修复](#紧急修复)
* [Commands](#commands)

---

### 安装

- 你需要有一个可以工作的 git 作为前提。
- Git flow 可以工作在 OSX, Linux 和 Windows之下

##### OSX Homebrew:

```
$ brew install git-flow
```

##### OSX Macports:

```
$ port install git-flow
```

##### Linux:

```
$ apt-get install git-flow
```

##### Windows (Cygwin):

安装 git-flow, 你需要 wget 和 util-linux。

```
$ wget -q -O - --no-check-certificate https://github.com/nvie/gitflow/raw/develop/contrib/gitflow-installer.sh | bash
```

----


### 开始

- 为了自定义你的项目，Git flow 需要初始化过程。
- 使用 git-flow，从初始化一个现有的 git 库内开始。
- 初始化，你必须回答几个关于分支的命名约定的问题。建议使用默认值。

```
git flow init
```

---


### 特性

- 为即将发布的版本开发新功能特性。
- 这通常只存在开发者的库中。

##### 创建一个新特性:

下面操作创建了一个新的feature分支，并切换到该分支

```
git flow feature start MYFEATURE
```

##### 完成新特性的开发:

完成开发新特性。这个动作执行下面的操作：
1. 合并 MYFEATURE 分支到 'develop'
2. 删除这个新特性分支
3. 切换回 'develop' 分支

```
git flow feature finish MYFEATURE
```

##### 发布新特性:

你是否合作开发一项新特性？
发布新特性分支到远程服务器，所以，其它用户也可以使用这分支。

```
git flow feature publish MYFEATURE
```

##### 取得一个发布的新特性分支:

取得其它用户发布的新特性分支。

```
git flow feature pull origin MYFEATURE
```

##### 追溯远端上的特性:

通过下面命令追溯远端上的特性

```
git flow feature track MYFEATURE
```

---


### 做一个release版本

- 支持一个新的用于生产环境的发布版本。
- 允许修正小问题，并为发布版本准备元数据。

##### 开始创建release版本:

- 开始创建release版本，使用 git flow release 命令。 
- 'release' 分支的创建基于 'develop' 分支。 
- 你可以选择提供一个 [BASE]参数，即提交记录的 sha-1 hash 值，来开启动 release 分支。
- 这个提交记录的 sha-1 hash 值必须是'develop' 分支下的。 

```
git flow release start RELEASE [BASE]
```

创建 release 分支之后立即发布允许其它用户向这个 release 分支提交内容是个明智的做法。命令十分类似发布新特性：

```
git flow release publish RELEASE
```

(你可以通过 
`git flow release track RELEASE` 命令追溯远端的 release 版本)

##### 完成 release 版本:

完成 release 版本是一个大 git 分支操作。它执行下面几个动作：
1. 归并 release 分支到 'master' 分支。
2. 用 release 分支名打 Tag
3. 归并 release 分支到 'develop'
4. 移除 release 分支。


```
git flow release finish RELEASE
```

不要忘记使用`git push --tags`将tags推送到远端

---


### 紧急修复

紧急修复来自这样的需求：生产环境的版本处于一个不预期状态，需要立即修正。有可能是需要修正 master 分支上某个 TAG 标记的生产版本。

##### 开始 git flow 紧急修复:

像其它 git flow 命令一样, 紧急修复分支开始自：

```
$ git flow hotfix start VERSION [BASENAME]
```


VERSION 参数标记着修正版本。你可以从 `[BASENAME]开始，`[BASENAME]`为finish release时填写的版本号

##### 完成紧急修复:

当完成紧急修复分支，代码归并回 develop 和 master 分支。相应地，master 分支打上修正版本的 TAG。

```
git flow hotfix finish VERSION
```

---


### Commands
<p align="center">
    <img alt="Git" src="../Img/git-flow-commands.png" height="270" width="460">
</p>
<hr>

### Git flow schema

<p align="center">
    <img alt="Git" src="../Img/git-flow-commands-without-flow.png">
</p>
<hr>
