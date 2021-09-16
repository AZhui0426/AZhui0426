### Linux命令行图形化界面切换

https://blog.csdn.net/qq_40597878/article/details/82321915



### Linux开启SSH

https://www.cnblogs.com/kinwing/p/11134179.html



### Linux开关防火墙

[(3条消息) Linux关闭防火墙命令_baidu_36124158的博客-CSDN博客_linux关闭防火墙](https://blog.csdn.net/baidu_36124158/article/details/90603496)

[Linux防火墙开放某端口号 - Watcher123 - 博客园 (cnblogs.com)

[](https://www.cnblogs.com/Azi-mi/p/10514952.html)

### Linux查看端口占用情况

https://www.runoob.com/w3cnote/linux-check-port-usage.html



### Linux_ftp

#### vsftpd的使用

参考：

[vsftpd的安装和使用_Aaron_Run的博客-CSDN博客_vsftpd](https://blog.csdn.net/qq_36938617/article/details/89077845)

[史上最详细的vsftpd配置文件讲解_juxiezuo_0722的博客-CSDN博客_vsftpd配置文件](https://blog.csdn.net/juxiezuo_0722/article/details/82586025)

[vsftpd - Community Help Wiki (ubuntu.com)](https://help.ubuntu.com/community/vsftpd)

！！配置作用以链接3中的信息为主！！



检查是否安装vsftpd

```rpm -qa | grep vsftpd
rpm -qa | grep vsftpd
```

安装vsftpd

```
yum -y install vsftpd
```

卸载vsftpd

```
yum remove vsftpd
```

启动/重启vsftpd

```
service vsftpd start/restart
```

开启vsftpd自启动

```
chkconfig vsftpd on
```

出现-bash: ftp: command not found如何解决？

安装ftp指令集

```
yum -y install ftp
```



目前使用到的配置

```
# 修改客户端登录，提示的欢迎信息
# You may fully customise the login banner string:
ftpd_banner=Welcome to blah FTP service.
#把本地账户指向创建的ftpfile文件夹
local_root=/ftpfile
#添加匿名账户访问ftpfile目录
anon_root=/ftpfile
#ftp服务器用到的是本地的时间
use_localtime=YES

To chroot users
To jail / chroot users (not the VSFTPD service), there are three choices. Search for "chroot_local_users" on the file and consider one of the following: Code:
# 建议使用配置1
# 1. All users are jailed by default:
chroot_local_user=YES
chroot_list_enable=NO

# 2. Just some users are jailed:
chroot_local_user=NO
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the jailed users.

# 3. Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the "free" users.

# ftp端口号
listen_port=4444
# 最小数据传输端口，与最大值共同决定最大线程数
pasv_min_port=61001
# 最大数据传输端口，与最大值共同决定最大线程数
pasv_max_port=62000

# 本地用户使用的文件夹路径
local_root=/ftpfile
# 匿名用户使用的文件夹路径
anon_root=/ftpfile
# 默认是GMT时间，改成使用本机系统时间
use_localtime=YES
```

