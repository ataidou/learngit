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
    git clone https://github.com/someaccount/someproject.git


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

修改 RVM 的 Ruby 安装源到 Ruby China 的 Ruby 镜像服务器,这样能提高安装速度
go back to ataidou user
sudo chmod 777 ~/.rvm/user/db 
$ echo "ruby_url=https://cache.ruby-china.org/pub/ruby" > ~/.rvm/user/db 
rvm install 2.2.0 


6. (天朝特供）把gem source改成淘宝镜像以提高rails安装速度

    $ gem source -r https://rubygems.org/
    $ gem source -a https://ruby.taobao.org



