- #vagrant #技术  #环境搭建
- 1.参考文档
  collapsed:: true
	- [官方文档](https://developer.hashicorp.com/vagrant/docs)
	- [熟练使用vagrant](https://www.junmajinlong.com/virtual/index/#vagrant)
- 2.vagrant简介
	- 用于管理和构建虚拟机环境的工具
	- 提供易于配置、可重复和便携式的开发环境
	- 跨操作系统，提供一致的开发环境
- 3.安装
	- vagrant 安装
		- [Vagrant downloads page](https://developer.hashicorp.com/vagrant/install)
	- VirtualBox 安装
		- [VirtualBox downloads page](https://www.virtualbox.org/wiki/Downloads)
	- vagrant和VirtualBox版本有兼容要求
		- V2.4.1 支持4.0.x, 4.1.x, 4.2.x, 4.3.x, 5.0.x, 5.1.x, 5.2.x, 6.0.x, 6.1.x and 7.0.x
		- [参考链接](https://developer.hashicorp.com/vagrant/docs/providers/virtualbox)
	- 安装后一些设置
		- 如果C盘比较小可以设置
		- VirtualBox
			- 管理-常规-默认虚拟电脑位置
		- vagrant
			- vagrant在执行子命令box add、init、up等命令时，都可能会去下载所需的虚拟机镜像文件，即Box image。
			- 这些镜像文件默认放在`~/.vagrant.d`目录(Linux)或`C:\USERS\<NAME>\.vagrant.d\`目录(Windows)下，这些镜像文件一般至少都几百兆，大的镜像可能几个G，所以放在家目录或C盘会占用大量空间。
			- Windows设置`VAGRANT_HOME`环境变量方式或者
			- ```shell
			  setx VAGRANT_HOME "e:/tmp/.vagrant.d"
			  #查看是否设置成功
			  #cmd中echo %VAGRANT_HOME%
			  #powershell中$env:VAGRANT_HOME
			  ```
- 4.创建虚拟机
	- ```shell
	  vagrant init hashicorp/bionic64
	  vagrant up #启动
	  vagrant destroy #销毁
	  ```
- 5.常用命令
	- | 子命令 | 功能说明 |
	  | ---- | ---- | ---- |
	  | box | 管理box镜像(box是创建虚拟机的模板) |
	  | init | 初始化项目目录，将在当前目录下生成Vagrantfile文件 |
	  | up | 启动虚拟机，第一次执行将创建并初始化并启动虚拟机 |
	  | reload | 重启虚拟机 |
	  | halt | 将虚拟机关机 |
	  | destroy | 删除虚拟机(包括虚拟机文件) |
	  | suspend | 暂停(休眠、挂起)虚拟机 |
	  | resume | 恢复已暂停(休眠、挂起)的虚拟机 |
	  | snapshot | 管理虚拟机快照(hyperv中叫检查点) |
	  | status | 列出当前目录(Vagrantfile所在目录)下安装的虚拟机列表及它们的状态 |
	  | global-status | 列出全局已安装虚拟机列表及它们的状态 |
	  | ssh | 通过ssh连接虚拟机 |
	  | ssh-config | 输出ssh连接虚拟机时使用的配置项 |
	  | port | 查看各虚拟机映射的端口列表(hyperv不支持该功能) |
- 6.查看虚拟机状态
	- ```shell
	  vagrant status
	  vagrant global-status
	  id       name      provider    state      directory
	  ------------------------------------------------
	  2f592    default   virtualbox  running    V:/vagrant_test
	  ```
	- 这里的ID方便vgarant管理，区分不同虚拟机而设置的标识符
		- ```shell
		  vagrant up 2f2
		  vagrant halt ef5
		  vagrant ssh 2f5
		  ```
- 7.添加虚拟机模板
	- ```powershell
	  #第一种直接添加官方镜像box
	  vagrant init debian/bookworm64
	  #url方式
	  vagrant box add centos-7 https://mirrors.ustc.edu.cn/ubuntu-cloud-images/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box
	  #本地方式
	  vagrant box add centos_7 V:\vagrant_imgs\CentOS-7-x86_64-Vagrant-2004_01.VirtualBox.box
	  ```
	- | 子命令 | 功能说明 |
	  | ---- | ---- | ---- |
	  | add | 安装box |
	  | list | 列出已安装的box。已安装的box存放在`$HOME/.vagrant.d/`或`$VAGRANT_HOME/.vagrant.d/` |
	  | outdated | 检查是否有新版本的box |
	  | prune | 删除已有新版本的box |
	  | remove | 删除指定的box |
	  | repackage | 重新打包指定的box |
	  | update | 更新box到最新版(不会删除并新建box，而是直接在当前box上更新) |
	- vagrant 上面几个name
		- vagrant status 或 vagrant global-status 显示的name
			- config.vm.define
		- virtualbox中显示的虚拟机名称
			- vb.name
		- 虚拟机启动后ssh进入的主机名
			- config.vm.hostname
		- ```ruby
		  Vagrant.configure('2') do |config|
		    config.vm.box = "king/debian12"
		    config.vm.define "debian12_king"
		    config.vm.hostname = "debian12king"
		    config.vm.provider :virtualbox do |vb|
		      vb.name = "debian12_king"
		    end
		  end
		  ```
- 8.初始化虚拟机的时候可以一并执行
  collapsed:: true
	- 比如下载的官方debian镜像源往往需要替换成国内镜像
	- ```ruby
	  Vagrant.configure("2") do |config|
	    config.vm.box = "debian/bookworm64"
	    config.vm.define "debian_bookworm64"
	    config.vm.hostname = "king-vm"
	    
	    config.vm.provider :virtualbox do |vb|
	      vb.name = "debian_bookworm64"
	    end
	    
	    config.vm.provider :hyperv do |h|
	      h.vmname = "debian_bookworm64"
	    end
	  
	    # 单行命令，且每次vagrant up/reload都执行
	    config.vm.provision "shell", run: "always", inline: "echo hello world"
	  
	    # 多行命令，且只有第一次vagrant up初始化启动vm时执行
	    config.vm.provision "shell", inline: <<-SHELL
	    	# step1 备份
	  	sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
	      # step2 写入阿里云镜像源
	   sudo echo 'deb https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib
	  deb-src https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib
	  deb https://mirrors.aliyun.com/debian-security/ bookworm-security main
	  deb-src https://mirrors.aliyun.com/debian-security/ bookworm-security main
	  deb https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib
	  deb-src https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib
	  deb https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib
	  deb-src https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib
	  ' > /etc/apt/sources.list
	  	#step3 
	      sudo apt update
	      sudo apt upgrade
	      # step3 install packages
	      sudo apt install curl wget vim
	    SHELL
	  end
	  ```
- 9.批量创建机器
  collapsed:: true
	- 可以解决部署集群，多服务器需求
	- 官方案例
		- ```ruby
		  Vagrant.configure("2") do |config|
		  config.vm.provision "shell", inline: "echo Hello"
		    config.vm.define "WEB" do |web|
		    web.vm.box = "apache"
		  end
		    config.vm.define "DB" do |db|
		    db.vm.box = "mysql"
		  end
		  end
		  ```
		- ```ruby
		  (1..3).each do |i|
		    config.vm.define "node-#{i}" do |node|
		      node.vm.provision "shell",
		        inline: "echo hello node #{i}"
		    end
		  end
		  ```
	- 使用vagrant批量创建lnmp虚拟机
		- 安装5个虚拟机，都是debian12系统
			- 1个nginx节点
			- 2个php节点
				- 负载均衡
			- 3个mysql节点
				- 一个主从，另外两个备份
		- 配置示例
			- todo
- 10.配置虚拟网络
  collapsed:: true
	- 端口转发
		- ```ruby
		  Vagrant.configure("2") do |config|
		    # 虚拟机80端口 <=> 宿主机8080端口
		    config.vm.network "forwarded_port", guest: 80, host: 8080
		  
		    # 端口映射时，指定绑定的IP地址
		    config.vm.network "forwarded_port", 
		       guest: 111,  guest_ip: "192.168.1.3", 
		       host: 10111, host_up: "192.168.1.5"
		  
		    # 指定协议
		    config.vm.network "forwarded_port", guest: 222, host: 20222, protocol: "tcp"
		  
		    # 宿主机上端口冲突时，自动修正为其他可用端口
		    config.vm.network "forwarded_port", guest: 333, host: 30333, auto_correct: true
		  
		    # 可指定宿主机上端口冲突时，自动修正时允许的端口范围
		    config.vm.usable_port_range = 8000..8999
		  end
		  ```
		- 配置 private_network
			- ```RUBY
			  Vagrant.configure("2") do |config|
			  config.vm.box = "generic/centos7"
			    config.vm.define "test1" do |t|
			    	t.vm.hostname = "test1"
			    	t.vm.network "private_network", ip: "192.168.50.11"
			    	t.vm.network "private_network", ip: "192.168.100.111"
			    	t.vm.provider "virtualbox" do |vb|
			      vb.name = "test1"
			    end
			  end
			  
			  config.vm.define "test2" do |t|
			    t.vm.hostname = "test2"
			    t.vm.network "private_network", ip: "192.168.100.22"
			    t.vm.network "private_network", ip: "192.168.100.222"
			    t.vm.provider "virtualbox" do |vb|
			      vb.name = "test2"
			    end
			  end
			  end
			  ```
- 11.目录同步
  collapsed:: true
	- ```ruby
	  # 将宿主机项目目录挂载到虚拟机的/vagrant目录
	  config.vm.synced_folder ".", "/vagrant"
	  
	  # 将宿主机项目目录内的src子目录挂载到虚拟机的/src/website目录
	  config.vm.synced_folder "src/", "/srv/website"
	  
	  # 禁用挂载项：不要在vagrant up或reload时自动挂载
	  config.vm.synced_folder "src/", "/srv/website", disabled: true
	  
	  # 修改虚拟机上挂载目录的owner和group
	  # 不指定owner/group时，它们的owner默认是vagrant ssh所使用的用户，
	  # 即一般情况下是vagrant用户
	  config.vm.synced_folder "src/", "/srv/website",
	    owner: "root", group: "root"
	  
	  # 指定同步的方式，支持的方式有：nfs、rsync、smb、virtualbox
	  # 同步方式和provider有关，有些同步方式在某种provider上无效
	  config.vm.synced_folder ".", "/vagrant", type: "nfs"
	  
	  # VirtualBox存在与sendfile相关的错误，该错误可能会导致文件损坏或无法更新 
	  #在 Nginx 中需要
	  sendfile off;
	  ```
- 12.使用hostmanager插件自动管理DNS解析
  collapsed:: true
	- ```shell
	  $ vagrant plugin install vagrant-hostmanager
	  ```
	- ```ruby
	  Vagrant.configure("2") do |config|
	  
	    # 激活hostmanager插件
	    config.hostmanager.enabled = true
	    # 在宿主机上的hosts文件中添加虚拟机的主机名解析信息
	    config.hostmanager.manage_host = true
	    # 在各自虚拟机中添加各虚拟机的主机名解析信息
	    config.hostmanager.manage_guest = true
	    # 不忽略私有网络的地址
	    config.hostmanager.ignore_private_ip = false
	    config.vm.define 'vm1' do |node|
	      node.vm.hostname = 'vm1'
	      node.vm.network :private_network, ip: '192.168.42.42'
	    end
	    config.vm.define 'vm2' do |node|
	      node.vm.hostname = 'vm2'
	    end
	  end
	  ```
	- vagrant up 后相当于再host里面添加了
	- ```shell
	  ## vagrant-hostmanager-start
	  192.168.42.42  vm1
	  
	  172.25.190.89  vm2
	  
	  ## vagrant-hostmanager-end
	  ```
- 13.打包自己基础box
  collapsed:: true
	- ```shell
	  #先压缩
	  apt clean
	  apt autoremove
	  dd if=/dev/zero of=/EMPTY bs=1M
	  rm -f /EMPTY
	  #再打包
	  vagrant package --output xxx.box
	  ```
- 14.错误
  collapsed:: true
	- vagrant@127.0.0.1: Permission denied (publickey).
	- ```shell
	  #查看信息
	  vagrant ssh-config
	  #排查
	  vagrant ssh -- -v
	  #错误信息
	  Permissions for 'D:/env/.vagrant.d/boxes/debian12-test/0/virtualbox/vagrant_private_key' are too open.
	  #解决
	  #原因是windows上的key权限太大了，我们找到对应key
	  #右键-属性-安全-高级-禁用继承（从此对象中删除所有已继承的权限）-应用-编辑（组或者用户名）-添加你当前账户-应用
	  ```