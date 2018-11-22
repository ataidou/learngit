GuildLine to set up github
1 SSH key :
  need to generate at locally, and past to github profile 
  o. $ git config --global user.name "superGG1990"
     $ git config --global user.email "superGG1990@163.com"
  a. ssh-keygen 
  b. open ~/.ssh/id_dsa.pub, and paste to github.com's profile SSH
2.github slowly
  in china. a. VPN. b. use "151.101.74.249 github.global.ssl.fastly.net"
  http://tool.chinaz.com/dns/  to get DNS from web URL.
  add to last line to C:\Windows\System32\drivers\etc\HOST
3. clone  a. https b. SSH.
    git clone git@github.com:someaccount/someproject.git
    git clone https://github.com/code-dot-org/code-dot-org.git


CentOS7 set up.
1. VMWare workstations
2  CentOS7 vitrual machine

start to update
 
1 更新操作系统

  --add user to sudoers
 
  su 
  chmod u+w /etc/sudoers”
  gedit /etc/sudoers
  find  Allow root to ruan any commands anywhere
  在root  ALL=(ALL)  ALL 下面另起一行，输入“xx ALL=(ALL)  ALL”(xx表示你的用户名)，然后保存退出

  sudo yum update

2. 安装EPEL software

    $ yum install epel-release

    $ yum repolist


2 从yum安装git
yum –y install git
 创建用户:
   git config --global user.name "你的名字"
   git config --global user.email "你的邮箱"
 创建秘钥
   ssh-keygen -t rsa -C "你的邮箱"
    home/ataidou/.ssh/id_rsa.pub to copy "ssh-rsa"
将公钥加入服务器列表（服务器)
   vi /root/.ssh/authorized_keys   <-copy ssh-rsa"
go to github.com profiling copy ss-rsa to profiling ssh

3. 安装一些工具和库

    $ yum install curl-devel nano sqlite-devel libyaml-devel
    // rvm安装会使用的包
     yum install gcc-c++ patch readline readline-devel zlib zlib-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison iconv-devel

4 install RVM （查官网）

   gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
   \curl -sSL https://get.rvm.io | bash -s stable
   source ~/.bashrc
   source /home/ataidou/.rvm/scripts/rvm

   su -- setup again
source /etc/profile.d/rvm.sh

   rvm reload

5. set up Ruby


没有使用----------
修改 RVM 的 Ruby 安装源到 Ruby China 的 Ruby 镜像服务器,这样能提高安装速度
go back to ataidou user
sudo chmod 777 ~/.rvm/user/db 
$ echo "ruby_url=https://cache.ruby-china.org/pub/ruby" > ~/.rvm/user/db 

face issue commincate with peer（35）
yum update curl
----------------
curl --ciphers ecdhe_ecdsa_aes_128_gcm_sha_256 https://openhatch.org/
-----------

sudo yum install -y git mysql-server mysql-client libmysqlclient-dev libxslt1-dev libssl-dev zlib1g-dev imagemagick libmagickcore-dev libmagickwand-dev openjdk-9-jre-headless libcairo2-dev libjpeg8-dev libpango1.0-dev libgif-dev curl pdftk enscript libsqlite3-dev phantomjs build-essential redis-server npm

root下安装
rvm install 2.5.1 


6. (天朝特供）把gem source改成淘宝镜像（已经停止了）以提高rails安装速度，用ruby-china

    $ gem source -r https://rubygems.org/
    $ gem source -a https://gems.ruby-china.com


gem install bundler
curl -o- -L https://yarnpkg.com/install.sh | bash [-s -- --version 1.6.0]



7 my SQL setup

http://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/
wget http://repo.mysql.com/mysql57-community-release-el7-10.noarch.rpm
rpm -Uvh mysql57-community-release-el7-10.noarch.rpm
 yum install  -y  mysql-community-server

、首先启动mysql
service mysqld start
查看MySQL运行状态

[root@localhost ~]# systemctl status mysqld.service
需要找出root的密码

[root@localhost ~]# grep "password" /var/log/mysqld.log
2018-11-21T13:49:58.489648Z 1 [Note] A temporary password is generated for root@localhost: ivnlewW8Vj!n
默认的密码登陆
mysql -uroot -p

ALTER USER 'root'@'localhost' IDENTIFIED BY 'zuliang98SS.';
# 这里会遇到一个问题，新密码设置过于简单会报错
如何解决ERROR 1819 (HY000): Your password does not satisfy the current policy requirements呢？ 这里直接提供解决方案文末有详细的说明

必须修改两个全局参数：
首先，修改validate_password_policy参数的值

mysql> set global validate_password_policy=0;
再修改密码的长度

set global validate_password_length=1;
再次执行修改密码就可以了

ALTER USER 'root'@'localhost' IDENTIFIED BY 'root123';（ALTER等可以写成小写）
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'zuliang98S';

还有一个问题就是Yum Repository,以后每次 yum 操作都会自动更新，需要把这个卸载掉

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'zuliang98S' WITH GRANT OPTION;

[root@localhost ~]# yum -y remove mysql57-community-release-el7-10.noarch

8 虚拟机共享
https://blog.csdn.net/zs_4336/article/details/80159315
https://blog.csdn.net/qq_28959531/article/details/78405400

su
/usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs -o subtype=vmhgfs-fuse,allow_other
cd /mnt/hgfs
ls

9，给用户root 权限
gpasswd -a ataidou root
sudo chmod -R 777 /home/ataidou/.rvm/   所有文件夹

10 code org

sudo yum install mysql-devel
