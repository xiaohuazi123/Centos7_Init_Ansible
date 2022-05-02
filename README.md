# Centos7_Init_Ansible
Centos7初始化



# 本次介绍如何利用ansible一键初始化centos7。

本文介绍的运行环境是CentOS 7.6：
```
[root@localhost ~]# cat /etc/redhat-release 
CentOS Linux release 7.6.1810 (Core) 
[root@localhost ~]# uname -a
Linux localhost.localdomain 3.10.0-957.el7.x86_64 #1 SMP Thu Nov 8 23:39:32 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

## 1. 安装ansbile  
直接用yum安装ansible即可：
```
yum -y install epel-release 
yum install -y ansible

```

查看版本号，确认安装成功：
```
[root@localhost ~]# ansible --version
ansible 2.9.27
  config file = /etc/ansible/ansible.cfg
  configured module search path = [u'/root/.ansible/plugins/modules', u'/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python2.7/site-packages/ansible
  executable location = /usr/bin/ansible
  python version = 2.7.5 (default, Oct 30 2018, 23:45:53) [GCC 4.8.5 20150623 (Red Hat 4.8.5-36)]

```
这就OK了。  
  
## 2. 配置ansible
修改 `/etc/ansible/hosts` 文件，把要初始化的服务器IP加进去，例如：
```

[servers]
192.168.1.99


[all:vars]
ansible_ssh_pass=123456

```
**提醒**
- 请填内网IP地址，默认使用内网IP地址
- 如果同时还要初始化本机，也请填写本机内网IP地址

上面这个主机列表，默认使用同一个密码，方便批量初始化，初始化完毕之后，可以用其他第三方工具去修改主机密码。
