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


û��ʹ��----------
�޸� RVM �� Ruby ��װԴ�� Ruby China �� Ruby ���������,��������߰�װ�ٶ�
go back to ataidou user
sudo chmod 777 ~/.rvm/user/db 
$ echo "ruby_url=https://cache.ruby-china.org/pub/ruby" > ~/.rvm/user/db 

face issue commincate with peer��35��
yum update curl
----------------
curl --ciphers ecdhe_ecdsa_aes_128_gcm_sha_256 https://openhatch.org/
-----------

sudo yum install -y git mysql-server mysql-client libmysqlclient-dev libxslt1-dev libssl-dev zlib1g-dev imagemagick libmagickcore-dev libmagickwand-dev openjdk-9-jre-headless libcairo2-dev libjpeg8-dev libpango1.0-dev libgif-dev curl pdftk enscript libsqlite3-dev phantomjs build-essential redis-server npm

root�°�װ
rvm install 2.5.1 


6. (�쳯�ع�����gem source�ĳ��Ա������Ѿ�ֹͣ�ˣ������rails��װ�ٶȣ���ruby-china

    $ gem source -r https://rubygems.org/
    $ gem source -a https://gems.ruby-china.com


gem install bundler
curl -o- -L https://yarnpkg.com/install.sh | bash [-s -- --version 1.6.0]



7 my SQL setup

http://dev.mysql.com/doc/mysql-yum-repo-quick-guide/en/
wget http://repo.mysql.com/mysql57-community-release-el7-10.noarch.rpm
rpm -Uvh mysql57-community-release-el7-10.noarch.rpm
 yum install  -y  mysql-community-server

����������mysql
service mysqld start
�鿴MySQL����״̬

[root@localhost ~]# systemctl status mysqld.service
��Ҫ�ҳ�root������

[root@localhost ~]# grep "password" /var/log/mysqld.log
2018-11-21T13:49:58.489648Z 1 [Note] A temporary password is generated for root@localhost: ivnlewW8Vj!n
Ĭ�ϵ������½
mysql -uroot -p

ALTER USER 'root'@'localhost' IDENTIFIED BY 'zuliang98SS.';
# ���������һ�����⣬���������ù��ڼ򵥻ᱨ��
��ν��ERROR 1819 (HY000): Your password does not satisfy the current policy requirements�أ� ����ֱ���ṩ���������ĩ����ϸ��˵��

�����޸�����ȫ�ֲ�����
���ȣ��޸�validate_password_policy������ֵ

mysql> set global validate_password_policy=0;
���޸�����ĳ���

set global validate_password_length=1;
�ٴ�ִ���޸�����Ϳ�����

ALTER USER 'root'@'localhost' IDENTIFIED BY 'root123';��ALTER�ȿ���д��Сд��
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'zuliang98S';

����һ���������Yum Repository,�Ժ�ÿ�� yum ���������Զ����£���Ҫ�����ж�ص�

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'zuliang98S' WITH GRANT OPTION;

[root@localhost ~]# yum -y remove mysql57-community-release-el7-10.noarch

8 ���������
https://blog.csdn.net/zs_4336/article/details/80159315
https://blog.csdn.net/qq_28959531/article/details/78405400

su
/usr/bin/vmhgfs-fuse .host:/ /mnt/hgfs -o subtype=vmhgfs-fuse,allow_other
cd /mnt/hgfs
ls

9�����û�root Ȩ��
gpasswd -a ataidou root
sudo chmod -R 777 /home/ataidou/.rvm/   �����ļ���

10 code org

sudo yum install mysql-devel
