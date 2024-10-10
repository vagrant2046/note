- #技术 #开发环境 #lnmp
- 单机环境
	- debian12
		- apt源安装
			- ```bash
			  #step1 更新系统
			  sudo apt update
			  sudo apt upgrade -y
			  
			  #step2 安装 Nginx
			  sudo apt install nginx -y
			  #把nginx加入到命令行path
			  vim  ~/.bashrc
			  export PATH=$PATH:/usr/sbin
			  source ~/.bashrc
			  #查看nginx 是否安装成功
			  nginx -v
			  #启动并开机启动nginx
			  sudo systemctl start nginx
			  sudo systemctl enable nginx
			  
			  #step3 安装php
			  sudo apt install php php-fpm php-mysql -y
			  
			  #step4 安装mysql
			  #Debian 10 以后的系统默认使用了 MariaDB 数据库,软件源中没有 mysql
			  apt install gnupg
			  wget https://dev.mysql.com/get/mysql-apt-config_0.8.32-1_all.deb
			  sudo dpkg -i mysql-apt-config_0.8.32-1_all.deb
			  sudo apt-get update
			  #开始安装mysql
			  sudo apt install mysql-server -y
			  #mysql一些安全设置
			  sudo mysql_secure_installation
			  mysql -V
			  sudo systemctl start mysql
			  sudo systemctl enable mysql
			  #配置虚拟主机
			  sudo vim /etc/nginx/sites-available/example.com
			  #输入
			  server {
			      listen 80;
			      server_name example.com www.example.com;
			  
			      root /var/www/example.com/html;
			      index index.html index.htm;
			  
			      location / {
			          try_files $uri $uri/ =404;
			      }
			      location ~ \.php$ {
			          include snippets/fastcgi-php.conf;
			          fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
			          fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
			          include fastcgi_params;
			      }
			  }
			  #启用虚拟主机配置
			  sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/
			  #测试
			  sudo nginx -t
			  #重新加载
			  sudo systemctl reload nginx
			  ```
		- 编译安装
			- PHP 5.3.29  、MYSQL 5.5.42、nginx 1.8.0
			- ```BASH
			  #PHP编译安装
			  sudo apt update
			  sudo apt upgrade
			  #安装依赖
			  sudo apt install build-essential autoconf bison re2c libxml2-dev
			  sudo apt install libbz2-dev libcurl4-openssl-dev libjpeg-dev libpng-dev libxpm-dev libfreetype6-dev libmcrypt-dev default-libmysqlclient-dev libreadline-dev 
			  #一些软链接
			  sudo ln -s /usr/lib/x86_64-linux-gnu/libssl.so  /usr/lib
			  sudo ln -s  /usr/include/x86_64-linux-gnu/curl  /usr/include/curl
			  sudo ln -s  /usr/include/x86_64-linux-gnu/curl  /usr/include/curl/curl
			  #由于旧版本的php对openssl版本有要求
			  wget https://www.openssl.org/source/old/1.0.2/openssl-1.0.2u.tar.gz
			  tar -xvzf openssl-1.0.2u.tar.gz
			  ./config --prefix=/usr/local/openssl-1.0.2 --openssldir=/usr/local/openssl-1.0.2
			  make
			  sudo make install
			  #配置编译选项
			  ./configure \
			  --prefix=/usr/local/php5.3 \
			  --with-config-file-path=/usr/local/php5.3/etc \
			  --with-mysqli \
			  --with-zlib \
			  --enable-mbstring \
			  --enable-soap \
			  --enable-calendar \
			  --with-curl=/usr/local/openssl-1.0.2 \
			  --with-openssl=/usr/local/openssl-1.0.2 \
			  --with-mcrypt \
			  --with-bz2 \
			  --with-gd
			  #编译和安装
			  make
			  sudo make install
			  #太低版本还是建议使用docke吧
			  
			  
			  ```
			- ln -s /usr/lib/x86_64-linux-gnu/libssl.so  /usr/lib
			  sudo ln -s  /usr/include/x86_64-linux-gnu/curl  /usr/include/curl
			  sudo ln -s  /usr/include/x86_64-linux-gnu/curl  /usr/include/curl/curl
			- default-libmysqlclient-dev
			-
-
- 高可用环境
-