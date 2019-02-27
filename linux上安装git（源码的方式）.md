## linux上安装git（源码的方式）

1.查看自己的linux版本（本人的linux 是centos 6.8）

​	cat /etc/redhat-release  

2.如果版本过低的话可以先升级版本

​	yum  -y update

3.安装依赖的包

​	yum -y install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker

4.下载git源码并解压

​	wget https://github.com/git/git/archive/v2.3.0.zip

​	unzip v2.3.0.zip

5.编译安装到/usr/local/git（**注意：路径必须切到解压路径里面**）

​	cd git-2.3.0 (**注意点**)

​	make prefix=/usr/local/git all

​	make prefix=/usr/local/git install

6.配置git的环境变量 （不然git命令没法使用）

​	vim /etc/profile

​	export PATH=/usr/local/git/bin:$PATH      (在该上面文件最后面追加该配置)

​	source /etc/profile

7.然后再次使用git --version 查看git版本，发现输出2.3.0，表明安装成功。