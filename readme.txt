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
 
1 ���²���ϵͳ

  --add user to sudoers
 
  su 
  chmod u+w /etc/sudoers��
  gedit /etc/sudoers
  find  Allow root to ruan any commands anywhere
  ��root  ALL=(ALL)  ALL ��������һ�У����롰xx ALL=(ALL)  ALL��(xx��ʾ����û���)��Ȼ�󱣴��˳�

  sudo yum update

2. ��װEPEL software

    $ yum install epel-release

    $ yum repolist


2 ��yum��װgit
yum �Cy install git
 �����û�:
   git config --global user.name "�������"
   git config --global user.email "�������"
 ������Կ
   ssh-keygen -t rsa -C "�������"
    home/ataidou/.ssh/id_rsa.pub to copy "ssh-rsa"
����Կ����������б�������)
   vi /root/.ssh/authorized_keys   <-copy ssh-rsa"
go to github.com profiling copy ss-rsa to profiling ssh

3. ��װһЩ���ߺͿ�

    $ yum install curl-devel nano sqlite-devel libyaml-devel
    // rvm��װ��ʹ�õİ�
     yum install gcc-c++ patch readline readline-devel zlib zlib-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison iconv-devel

4 install RVM ���������

   gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
   \curl -sSL https://get.rvm.io | bash -s stable
   source ~/.bashrc
   source /home/ataidou/.rvm/scripts/rvm

   su -- setup again
source /etc/profile.d/rvm.sh

   rvm reload

5. set up Ruby

�޸� RVM �� Ruby ��װԴ�� Ruby China �� Ruby ���������,��������߰�װ�ٶ�
go back to ataidou user
sudo chmod 777 ~/.rvm/user/db 
$ echo "ruby_url=https://cache.ruby-china.org/pub/ruby" > ~/.rvm/user/db 
rvm install 2.2.0 


6. (�쳯�ع�����gem source�ĳ��Ա����������rails��װ�ٶ�

    $ gem source -r https://rubygems.org/
    $ gem source -a https://ruby.taobao.org



