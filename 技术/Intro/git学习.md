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

#### 当前做的哪些更新尚未暂存? 有哪些更新已暂存并准备好下次提交?

>git diff 可以通过文件补丁的格式更加具体显示哪些行发生了变化