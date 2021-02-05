# GIT学习笔记

## 1.1关于版本控制

> 版本控制是一种记录一个或若干文件内容变化,以便将来查阅特定版本修订情况的系统

1. 老本地版本控制系统		`简单单一,无法协同工作`
2. 集中化版本控制系统        `单点故障`
3. 分布式版本控制系统

## 1.2 Git简史

> 由于和 `BitKeeper `关系断裂,`Linus Torvalds`开发出了Git

* 速度
* 简单的设计
* 对非线性开发模式的强力支持(允许成千上万并行开发的分支)
* 完全分布式
* 有能力高效管理超大规模项目



## 1.3 Git是什么

* 对待数据方式:直接记录快照,而非差异比较
* 近乎所有操作都是本地执行
* Git保证完整性
* Git一般只添加数据

### 三种状态:  已提交(committed)、已修改(modified)、已暂存(staged)

* 已修改表示修改了文件但没有保存到数据库中
* 已暂存表示对一个已修改的文件的当前版本做了标记,使之包含再下次提交的快照中
* 已提交表示数据已经安全地保存在本地数据库中

### 三个阶段:  工作区、暂存区、Git目录

![工作区、暂存区以及 Git 目录。](https://git-scm.com/book/en/v2/images/areas.png)

* 工作区是对项目的某个版本独立提取出来的内容
* 暂存区(索引)是一个文件，保存了下次将要提交的文件列表信息，一般在 Git 仓库目录中
* Git 仓库目录是 Git 用来保存项目的元数据和对象数据库的地方

### 基本的Git工作流程

1. 在工作区中修改文件
2. 将你想要下次提交的更改选择性地暂存，这样只会将更改的部分添加到暂存区
3. 提交更新，找到暂存区的文件，将快照永久性存储到 Git 目录



## 1.4 初次运行Git前的配置

### 设置用户名和邮件地址

~~~shell
$ git config --global user.name "John Doe" 
$ git config --global user.email johndoe@example.com
~~~

## 1.5 GIT基础

### 在已存在目录中初始化仓库

```shell
$ git init
$ git add *.c
$ git add LICENSE
$ git commit -m 'initial project version'
```

### 克隆现有的仓库

```shell
$ git clone https://github.com/libgit2/libgit2
```

### 记录每次更新到仓库

* 工作目录下文件状态:  **已跟踪** 和 **未跟踪**

![Git 下文件生命周期图。](https://git-scm.com/book/en/v2/images/lifecycle.png)

### 检查当前文件状态

```shell
$ git status
$ git status -s
```

### 跟踪新文件和暂存已经修改的文件

~~~ shell
$ git add 
~~~

### 忽略文件

```shell
$cat .gitignore
*.[oa] #忽略.o和.a结尾的文件
*~     #忽略.~结尾的文件
```

```shell
# 忽略所有的 .a 文件
*.a
# 但跟踪所有的 lib.a，即便你在前面忽略了 .a 文件
!lib.a
# 只忽略当前目录下的 TODO 文件，而不忽略 subdir/TODO
/TODO
# 忽略任何目录下名为 build 的文件夹
build/
# 忽略 doc/notes.txt，但不忽略 doc/server/arch.txt
doc/*.txt
# 忽略 doc/ 目录及其所有子目录下的 .pdf 文件
doc/**/*.pdf
```

### 查看已暂存和未暂存的修改

当前做的哪些更新尚未暂存? 有哪些更新已暂存并准备好下次提交?

>git diff 可以通过文件补丁的格式更加具体显示哪些行发生了变化

~~~shell
$ git diff
$ git diff --cached
$ git diff --staged
~~~

### 提交更新

~~~shell
$ git commit
$ git commit -m 'first commit'
~~~

### 移除文件

~~~shell
$ git rm 
$ git rm --cached #保留文件但不想让Git继续跟踪
~~~

### 移动文件

~~~shell
$ git mv file_from filr_to
~~~

### 查看提交历史

~~~shell
$ git log
$ git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
~~~

### 撤销操作

~~~shell
$ git commit --amend
#有时候我们提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了
~~~

### 取消暂存的文件

~~~shell
$ git reset HEAD filename
#工作目录里文件尚未修改相对安全一点
~~~

### 撤销对文件的修改

~~~shell
$ git checkout -- filename
#文件在本地修改都会消失，是一个非常危险的操作
~~~

### 远程仓库的使用

~~~shell
$ git clone git@github.com:vagrant2046/learngit.git
#查看远程仓库
$ git remote -v
#添加远程仓库
$ git remote add name https://github.com/vagrant2046/git
#从远程仓库中抓取和拉取
  #git fetch 将数据下载到你的本地仓库但不自动合并或修改
$ git fetch <remote>
  #git pull 自动抓取并合并
$ git pull <remote>
#推送到远程仓库
$ git push origin master
#查看某个远程仓库
$ git remote show origin
#远程仓库重命名与移除
$ git remote rename pb paul
$ git remote remove pb paul
~~~

### 打标签

~~~shell
$ git tag
$ git show v1.4
$ git tag -a v1.4 -m "my version 1.4"
$ git tag v1.4-lw
$ git tag -a v1.2 9fceb02
~~~

### Git别名

~~~shell
$ git config --global alias.co checkout
$ git config --global alias.br branch
$ git config --global alias.ci commit
$ git config --global alias.st status
$ git config --global alias.unstage 'reset HEAD --'
~~~

## 1.6 Git分支

### 分支基本操作

~~~shell
#创建分支
$ git branch testing
#切换分支
$ git checkout testing
#简写
$ git checkout -b testing
#分支合并回master分支
$ git merge bugfix
#删除分支
$ git branch -d bugfix
#遇到冲突的分支合并
<<<<<<< HEAD:index.html
<div id="footer">contact : email.support@github.com</div>
=======
<div id="footer">
 please contact us at support@github.com
</div>
>>>>>>> iss53:index.html
# =======解决冲突必须使用上下部分的一个或者可以自行合并这些内容
~~~

### 分支管理

~~~shell
$ git branch
$ git branch -v
$ git branch --merged
$ git branch --no-merged
$ git bracnh -d testing
~~~

### 分支开发工作流

长期分支

> 只在 `master` 分支上保留完全稳定的代码——有可能仅仅是已经发布或即将发布的代码。 
>
> 他们还有一些名为 `develop` 或者 `next` 的平行分支，被用来做后续开发或者测试稳定性——这些分支不必保持绝对稳定，但是一旦达到稳定状态，它们就可以被合并入 `master` 分支了。 
>
> 这样，在确保这些已完成的主题分支（短期分支，比如之前的 `iss53` 分支）能够通过所有测试，并且不会引入更多 bug 之后，就可以合并入主干分支中，等待下一次的发布。

![趋于稳定分支的工作流（“silo”）视图。](https://git-scm.com/book/en/v2/images/lr-branches-2.png)

主题分支

> 主题分支对任何规模的项目都适用。 主题分支是一种短期分支，它被用来实现单一特性或其相关工作。

远程分支

> 远程引用是对远程仓库的引用（指针），包括分支、标签等等

> 远程跟踪分支是远程分支状态的引用。它们是你无法移动的本地引用。

~~~shell
#推送分享的分支到远程
$ git push origin serverfix
#别人拉取
$ git fetch origin
#建立远程跟踪分支之上
$ git checkout -b serverfix origin/serverfix
$ git checkout --track origin/serverfix
#删除远程分支
$ git push origin --delete serverfix
#已有的本地分支跟踪刚拉取下来的分支
$ git branch -u origin/serverfix
#查看设置的所有跟踪分支
$ git branch -vv
~~~

### 变基

> 在 Git 中整合来自不同分支的修改主要有两种方法：`merge` 以及 `rebase`

> 使用 `rebase` 命令将提交到某一分支上的所有修改都移至另一分支上，就好像“重新播放”一样

~~~shell
#切换到experiment分支，然后将它变基到master分支上
$ git checkout experiment
$ git rebase master
~~~

![将 `C4` 中的修改变基到 `C3` 上。](https://git-scm.com/book/en/v2/images/basic-rebase-3.png)

~~~shell
$ git checkout master
$ git merge experiment
~~~

![`master` 分支的快进合并。](https://git-scm.com/book/en/v2/images/basic-rebase-4.png)

> 很明显最终结果没有任何区别，但是变基使得提交历史更加简洁
>
> **如果提交存在于你的仓库之外，而别人可能基于这些提交进行开发，那么不要执行变基。**
>
> 总的原则是，只对尚未推送或分享给别人的本地修改执行变基操作清理历史， 从不对已推送至别处的提交执行变基操作，这样，你才能享受到两种方式带来的便利

## 1.7 ssh-agent 管理多个密钥

>1. 我的电脑 -> 右键管理 -> 服务 -> OpenSSH ->自动开启
>
>2. GIT BASH 创建~/.brashrc
>
>    ```shell
>    env=~/.ssh/agent.env
>    agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }
>    agent_start () {
>        (umask 077; ssh-agent >| "$env")
>        . "$env" >| /dev/null ; }
>    agent_load_env
>    # agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
>    agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)
>    if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
>        agent_start
>        ssh-add ~/.ssh/one_rsa # 添加你自己的私钥
>    elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
>        ssh-add ~/.ssh/one_rsa # 添加你自己的私钥
>    fi
>    unset env
>    ```
>
>    
>
>    3.添加密钥到ssh-agent
>
>    ~~~shell
>    #检查密钥是否被加载
>    ssh-add -l
>    #添加密钥到ssh-agent
>    ssh-add ~/.ssh/private_key
>    ~~~
>
>    4.创建自己的密钥
>
>    ~~~shell
>    ssh-keygen -f king -C king
>    ssh-keygen -f githubxxx -C one@github
>    ssh-keygen -f giteexxxx -C one@gitee
>    ~~~
>
>    5.复制密钥到服务器上
>
>    ~~~shell
>    ssh-copy-id -i .ssh/xxx.pub root@1.1.1.1 -p 22
>    ~~~
>
>    6.多个密钥对应不同github（**有坑，计算机名称和用户名不能一样**）
>
>    ```shell
>    touch ~/.ssh/config
>    #debugtalk
>    	Host debugtalk
>    	    HostName github.com
>    	    User git
>    	    IdentityFile ~/.ssh/id_rsa
>    
>    # DJI
>    	Host djileolee
>    	    HostName github.com
>    	    User git
>    	    IdentityFile ~/.ssh/dji_id_rsa
>    ```

## 1.8 Git 简单工作流



![微信截图_20201204142247.png](https://i.loli.net/2020/12/04/u7nDwS5rFolUgOH.png)

> 第一步：根据需求，从`master`拉出新分支，不区分功能分支或补丁分支。
>
> 第二步：新分支开发完成后，或者需要讨论的时候，就向`master`发起一个[pull request](https://help.github.com/articles/using-pull-requests/)（简称PR）。
>
> 第三步：Pull Request既是一个通知，让别人注意到你的请求，又是一种对话机制，大家一起评审和讨论你的代码。对话过程中，你还可以不断提交代码。
>
> 第四步：你的Pull Request被接受，合并进`master`，重新部署后，原来你拉出来的那个分支就被删除。（先部署再合并也可。）

## 1.9 Git速查手册

![速查手册](http://www.git-tower.com/learn/cheat-sheets/git-cn/git-cheat-sheet-large02-cn.png)

![](http://www.git-tower.com/learn/cheat-sheets/git-cn/git-cheat-sheet-large01-cn.png)