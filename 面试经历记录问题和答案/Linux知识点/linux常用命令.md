# linux简介

Linux 是一套免费使用和自由传播的类 Unix 操作系统，是一个基于 POSIX 和 UNIX 的多用户、多任务、支持多线程和多 CPU 的操作系统

## Linux 的发行版

Linux 的发行版说简单点就是将 **Linux 内核与应用软件**做一个打包。

![img](https://www.runoob.com/wp-content/uploads/2014/06/1511849829609658.jpg)

目前市面上较知名的发行版有：Ubuntu、RedHat、CentOS、Debian、Fedora、SuSE、OpenSUSE、Arch Linux、SolusOS 等。

![img](https://www.runoob.com/wp-content/uploads/2014/06/wKioL1bvVPWAu7hqAAEyirVUn3c446.jpg-wh_651x-s_3197843091.jpg)

**知名发行的版本：** ubuntn,centos,Redhat,openSUSE,Fedora

# linux启动过程

- 内核的引导。
- 运行 init。
- 系统初始化。
- 建立终端 。
- 用户登录系统。

## Linux系统有7个运行级别(runlevel)：

- 运行级别0：系统停机状态，系统默认运行级别不能设为0，否则不能正常启动
- 运行级别1：单用户工作状态，root权限，用于系统维护，禁止远程登陆
- 运行级别2：多用户状态(没有NFS)
- 运行级别3：完全的多用户状态(有NFS)，登陆后进入控制台命令行模式
- 运行级别4：系统未使用，保留
- 运行级别5：X11控制台，登陆后进入图形GUI模式
- 运行级别6：系统正常关闭并重启，默认运行级别不能设为6，否则不能正常启动

# Linux 系统目录结构

# Linux磁盘管理



**linux常用命令**

curl http://192.168.6.128:8080   访问一个网站

**[关于防火墙的命名](https://www.cnblogs.com/wangjinyu/p/11679917.html)：**   一、防火墙的开启、关闭、禁用命令

​                                          （1）设置开机启用防火墙：systemctl enable firewalld.service

​                                         （2）设置开机禁用防火墙：systemctl disable firewalld.service

​                                         （3）启动防火墙：systemctl start firewalld

​                                         （4）关闭防火墙：systemctl stop firewalld

​                                          （5）检查防火墙状态：systemctl status firewalld 

​                                     二、使用firewall-cmd配置端口

​                                          （1）查看防火墙状态：firewall-cmd --state

​                                          （2）重新加载配置：firewall-cmd --reload

​                                          （3）查看开放的端口：firewall-cmd --list-ports

​                                          （4）开启防火墙端口：firewall-cmd --zone=public --add-port=8080/tcp --permanent

　　命令含义：

　　–zone #作用域

　　–add-port=9200/tcp #添加端口，格式为：端口/通讯协议

　　–permanent #永久生效，没有此参数重启后失效

　 　**注意：添加端口后，必须用命令firewall-cmd --reload重新加载一遍才会生效**

​                                       （5）关闭防火墙端口：firewall-cmd --zone=public --remove-port=9200/tcp --permanent

 

查看Tomcat的日志

1. 执行输出命令 ：tail -f catalina.out



**查看运行的端口**

ps  命令用于查看当前正在运行的进程。grep 是搜索

例如： ps -ef | grep java

表示查看所有进程里CMD 是java 的进程信息。

**kill 命令用于终止进程。** 例如： kill -9 [PID]

-9 表示强迫进程立即停止。