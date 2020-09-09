# PCR-Chatbot

Linux下搭载（指令主要以centos及ubuntu下为主）

前期环境部署

1.Docker容器安装：（详细可查看https://docs.docker.com/engine/install/debian/）
   在新主机上首次安装Docker Engine之前，需要设置Docker存储库。之后，您可以从存储库安装和更新Docker。
	 1.检测系统是否已是否安装yum工具（centos）:
       终端输入yum即可，已经安装，会显示yum的参数；否则返回无效参数
		   输入rpm -qa | grep yum已安装yum时，返回yum的安装包（版本）
	 2.安装yum-utils软件包（提供yum-config-manager 实用程序）并设置稳定的存储库（centos）；
	       sudo yum install -y yum-utils
			   sudo yum-config-manager \--add-repo \https://download.docker.com/linux/centos/docker-ce.repo	
			 安装DOCKER引擎：
			   sudo yum install docker-ce docker-ce-cli containerd.io
			 （如果提示您接受GPG密钥，请验证指纹是否匹配 060A 61C5 1B55 8A7F 742B 77AA C52F EB6B 621E 9F35，如果是，则接受它。）
		 更新apt软件包索引并安装软件包以允许apt通过HTTPS使用存储库（ubuntu）；
		     sudo apt-get update
			   sudo apt-get install \apt-transport-https \ca-certificates \curl \gnupg-agent \software-properties-common
			 添加Docker的官方GPG密钥：
			   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
			 
2.安装最新版本python：
   1.查看当前系统python版本：
	     python --version
			 python3 --version
	 2.更新至最新版本
	   yum大概率不支持最新python（centos）；前往python官网（https://www.python.org/）获取最新版本python下载链接
		 	   sudo wget https://www.python.org/ftp/python/3.8.5/Python-3.8.5.tgz
		 	 (下载速度慢可ctrl+z停止，直接本地下载后上传至服务器;
			 或者安装openssl相关包（原因可自行google））
			   yum install openssl openssl-devel
			 下载好后，解压
			   tar -zxvf Python-3.8.5.tgz
		   安装所需依赖包
			   yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc  libffi-devel
			 进入解压后文件夹
			   cd Python-3.8.5.tgz
			 编译及设置安装路径
			   ./configure --prefix=/usr/local/bin/python3
       安装
			   make && make install
		   再次查看python版本
			   python3 -V
			 不同即更改软链接（相当于windows快捷方式）
			   rm -rf /usr/bin/python3  （删除原先软链接）
				 ln -s /usr/local/bin/python3/bin/python3 /usr/bin/python3  （创建新软链接）
			 再次查看python版本号，同上指令
	  安装python3（ubuntu）
		   查看当前最新版本后
				 sudo apt install python3.8
				 
3.安装维持多会话软件（推荐screen）（相关指令baidu）
         yum install screen  （centos）
				 sudo apt-get install screen  （ubuntu）

4.安装git
        yum install git  （centos）
			  apt-get install git (ubuntu)
				
*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*以上配置后可录制一个快照*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*/*	
简单借用现有docker镜像
5.启动docke（重要...）
        systemctl start docker  

6.详细可查看教程（发现有大佬写了详细的0.0）
        https://yobot.win/install/docker/ 
				
				
一步步配置（他人写的教程）
        https://blog.michikawachin.art/index.php/2020/08/21/centos7-%e4%b8%8b%e7%9a%84%e5%85%ac%e4%b8%bb%e8%bf%9e%e7%bb%93%e7%be%a4%e8%81%8a%e6%9c%ba%e5%99%a8%e4%ba%ba%e9%83%a8%e7%bd%b2%e6%95%99%e7%a8%8b/
			
