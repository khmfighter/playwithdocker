准备docker-ce和docker-compose环境

##docker-ce部分##

1、依赖安装

yum install -y checkpolicy audit-libs  audit audit-libs-python python-IPy  setools-libs libsemanage libsemanage-python  libcgroup policycoreutils policycoreutils-python container-selinux libtool-ltdl libseccomp wget

2、下载docker

wget https://download.docker.com/linux/centos/7/x86_64/stable/Packages/docker-ce-17.12.0.ce-1.el7.centos.x86_64.rpm

3、安装docker

rpm -ivh docker-ce-17.12.0.ce-1.el7.centos.x86_64.rpm

4、启动docker

systemctl start docker

5、开机启动docker

systemctl enable docker

##docker-compose部分##

使用pip insall docker-compose进行安装
