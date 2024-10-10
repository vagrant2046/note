- #git #技术
- 1.学习资料:
  collapsed:: true
	- 官方网站：https://git-scm.com
	- 交互互动：https://learngitbranching.js.org
- 1.起步
  collapsed:: true
	- 什么是版本控制 ？
		- 记录一个或若干文件内容变化
		- 将来可查阅特定版本修订情况的系统
	- 发展历程
		- 本地版本控制系统->集中化的版本控制系统->分布式版本控制系统
- 2.Git简史
  collapsed:: true
	- Linus Torvalds 因为 BitKeeper 收回于2005年开发
	- Git是什么？
	  collapsed:: true
		- 与其他系统的区别
			- 1.直接记录快照，而非差异比较
			- 2.近乎所有的操作都是本地执行
			- 3.Git保证完整性
			- 4.Git一般只添加数据
	- 三种状态
	  collapsed:: true
		- 已提交（committed）
			- 数据已经安全地保存在本地数据库
		- 已修改（modified）
			- 修改了文件，但还没保存到数据库中
		- 已暂存（staged）
			- 对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中
	- 工作目录、暂存区域、Git仓库
	  collapsed:: true
		- 工作区是对项目的某个版本独立提取出来的内容
		- 暂存区是一个文件，保存了下次将要提交的文件列表信息，一般在 Git 仓库目录中
		- Git 仓库目录是 Git 用来保存项目的元数据和对象数据库的地方
	- 基本工作流程
	  collapsed:: true
		- 1.在工作区修改文件
		- 2.将你想要下次提交的更改选择性地暂存，这样只会将更改的部分添加到暂存区
		- 3.提交更新，找到暂存区的文件，将快照永久性存储到 Git 目录
	- 初次运行Git前的配置
	  collapsed:: true
		- git config 工具来设置
			- `/etc/gitconfig` 文件
				- 系统级别设置
			- `~/.gitconfig` 或 `~/.config/git/config` 文件
				- 当前用户
			- `.git/config`
				- 该仓库
		- 设置用户名和邮箱
			- ```
			  git config --global user.name "John Doe"
			  git config --global user.email johndoe@example.com
			  #查看配置信息
			  git config --list
			  ```
			-
- 3.Git基础
  collapsed:: true
	- 初始化仓库
	  collapsed:: true
		- ```git
		  git init
		  ```
	- 其他服务器克隆仓库
	  collapsed:: true
		- ```git
		  git clone https://github.com/libgit2/libgit2
		  ```
	- 检查当前状态
	  collapsed:: true
		- ```git
		  git status
		  ```
	- 添加跟踪新文件
	  collapsed:: true
		- ```git
		  git add
		  ```
	- 忽略文件
	  collapsed:: true
		- 建立`.gitignore`文件
		- ```
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
	- 查看已暂存和未暂存的修改
	  collapsed:: true
		- ```git
		  git status
		  #未暂存的文件更新了哪些部分
		  git diff 
		  #查看已暂存的将要添加到下次提交里的内容
		  git diff --staged
		  git diff --cached
		  ```
	- 提交更新
	  collapsed:: true
		- ```git
		  git commit
		  git commit -m
		  git commit -a # -a 就是git add所有文件了
		  ```
	- 移除文件
	  collapsed:: true
		- ```git
		  git rm * #删除并取消跟踪
		  git rm --cached #取消跟踪但不删除
		  ```
	- 移动文件
	  collapsed:: true
		- ```git
		  git mv file_from file_to
		  相当于运行了下面三个命令
		  mv file_from file_to
		  git rm file_from
		  git add file_to
		  ```
	- 查看历史
	  collapsed:: true
		- ```git
		  git log
		  git log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
		  ```
	- 撤销操作
	  collapsed:: true
		- ```GIT
		  git commit --amend
		  #这个命令会将暂存区中的文件提交。 如果自上次提交以来你还未做任何修改（例如，在上次提交后马上执行了此命令）， 那么快照会保持不变，而你所修改的只是提交信息。
		  #下面操作在提交完成后发现还有文件没有提交，可以添加后 git commit --amend，放入到上一次的提交
		  git commit -m 'initial commit'
		  git add forgotten_file
		  git commit --amend
		  ```
	- 取消暂存的文件
	  collapsed:: true
		- ```git
		  git reset HEAD <file>
		  ```
	- 撤销对文件的修改
	  collapsed:: true
		- ```git
		  git checkout -- <file>
		  ```
	- 远程仓库的使用
	  collapsed:: true
		- ```git
		  #查看远程仓库信息
		  git remote
		  #查看远程仓库信息详细
		  git remote -v
		  #查看更加详细的远程仓库信息
		  git remote show <remote>
		  #添加远程仓库
		  git remote add newname https://github.com/xxx/xx
		  #从远程仓库拉取
		  git fetch pb
		  #推送到远程仓库
		  git push <remote> <branch>
		  #查看某个远程仓库
		  git remote show <remote>
		  #远程仓库的重命名和移除
		  git remote rename <remote> <newname>
		  #移除远程仓库
		  git remote remove <remote>
		  ```
	- 打标签
	  collapsed:: true
		- ```git
		  #查看标签
		  git tag
		  
		  #查看指定标签
		  git tag -l “v1.8.5*”
		  
		  #标签分为轻量标签和附注标签
		  #轻量标签很像一个不会改变的分支——它只是某个特定提交的引用。
		  git tag v1.4-lw
		  
		  #附注标签是存储在 Git 数据库中的一个完整对象， 它们是可以被校验的，其中包含打标签者的名字、电子邮件地址、日期时间， 此外还有一个标签信息，并且可以使用 GNU Privacy Guard （GPG）签名并验证。
		  git tag -a v1.0 -m 'my version 1.0'
		  #查看
		  git show v1.4
		  
		  #后期打标签
		  git tag -a v1.2 9fceb02
		  
		  #共享标签
		  git push origin v1.5
		  
		  #一次性推送多个标签
		  git push origin --tags
		  
		  #删除标签
		  git tag -d v1.4-lw
		  #删除远程分支标签
		  git push origin :refs/tags/v1.4-lw
		  git push origin --delete <tagname>
		  
		  #检出标签
		  git checkout 2.0.0
		  ```
	- GIT别名
	  collapsed:: true
		- ```gitbash
		  git config --global alias.co checkout
		  git config --global alias.br branch
		  git config --global alias.ci commit
		  git config --global alias.st status
		  git config --global alias.lg=log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
		  ```
- 4.Git分支
  collapsed:: true
	- 定义：
	  collapsed:: true
		- 分支（branch）是指项目的一个独立的开发路线，是代码历史的并行版本。
		- 分支是代码的一个指针，指向某个提交（commit）
	- 为什么？
	  collapsed:: true
		- 独立开发
			- 可以在一个新分支上进行功能开发或者修复bug，不影响主分支的稳定性
		- 并行工作
			- 团队成员可以在不同分支上工作，最终通过合并（merge）将他们的工作整合在一起
		- 实验和回滚
			- 可以在分支上做一些实验性工作，不满意可以轻松删除分支，不影响其他部分代码
	- 分支的新建与合并
	  collapsed:: true
		- ```git
		  #创建并切换到branchname分支
		  git checkout -b branchname
		  #等价于
		  git branch branchname
		  git checkout branchname
		  #合并
		  git checkout master
		  git merge branchname
		  #冲突解决
		  vim flile
		  #手动解决冲突后
		  git add 
		  git commit
		  git merge branchname
		  #删除分支
		  git branch -d branchname
		  ```
	- 分支管理
	  id:: 6705df1f-b60c-48a6-855a-ccad350a5998
	  collapsed:: true
		- ```git
		  #查看分支列表
		  git branch
		  #查看每个分支最新提交
		  git branch -v
		  #查看已经合并和未合并的
		  git branch --merged
		  git branch --no-merged
		  #未被合并的分支删除不掉
		  ```
	- 分支开发工作
	  collapsed:: true
		- 长期分支
			- 使用多个长期分支通常很有帮助
				- master分支   保留完全稳定的代码
				- develop分支  后续开发或者测试稳定性
		- 主题分支
			- 短期分支，用来实现单一特性或者其他工作
	- 远程分支
	  collapsed:: true
		- 什么叫远程分支？
			- 指存储在远程仓库中的分支
			- 本地仓库通过 `fetch` 或 `pull` 来获取它们的更新
			- 本地和远程分支之间可以建立追踪关系，从而保持两者的同步
		- 跟踪远程分支
			- 克隆远程仓库
				- 当你首次克隆一个远程仓库时，GIT会自动跟踪分支
			- 创建并跟踪远程分支
				- ```git
				  git checkout -b <local-branch-name> <remote-name>/<remote-branch-name>
				  git checkout -b feature-login origin/feature-login
				  ```
			- 将本地分支与远程分支关联
				- ```git
				  #关联
				  git branch --set-upstream-to <remote-name>/<remote-branch-name>
				  
				  #将本地的 feature-login 分支与 origin/feature-login 关联：
				  git branch --set-upstream-to origin/feature-login
				  
				  #或者
				  git checkout --track origin/feature-login
				  ```
			- 查看跟踪关系
				- ```git
				  git branch -vv
				  ```
			- 拉取
				- ```git
				  #抓取数据，但不修改工作目录
				  git fetch
				  #抓取数据并合并
				  git merge
				  ```
			- 删除
				- ```git
				  git push origin --delete <branchname>
				  ```
	- 分支变基
	  collapsed:: true
		- Git中整合来自不同分支的修改主要两种方法
			- merge
			- rebase
		- 什么叫rebase
			- 将一个分支的变量重新应用到另一个分支的基础之上
			- 通俗的来讲叫做“调整基底”
		- 为什么要使用rebase
			- 保持历史记录的整洁
			- 在合并之前同步分支
		- rebase的风险
			- 如果提交存在于你的仓库之外，而别人可能基于这些提交进行开发，那么不要执行变基
			- 如果你已经将某个分支推送到远程仓库且已经有协作就不要使用rebase
			- 不要对已经共享的提交进行rebase
- 5.服务器上的Git
  collapsed:: true
	- 协议
	  collapsed:: true
		- 本地协议
		- HTTP协议
		- SSH协议
		- Git协议
		-
	- 导出裸版本
		- ```git
		  git clone --bare my_project my_project.git
		  ```
- 6.分布式Git-分布式工作流
	-
	-
-