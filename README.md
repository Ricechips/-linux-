# Linux

## 查找vi内固定行
ctrl + g 显示行数 <br>
命令模式   :n   (n)为想要跳转的行数 <br>
[系统加载进度条消失之术](https://www.cnblogs.com/silly-bird/p/10648169.html)

## 静态ip网络配置
/etc/sysconfig/network-scripts/ 找到网卡
```c
编辑  dhcp->static 
onboot=yes
IPADDR=
GATEWAY=
NETMASK=
DNS1=
service network restart
```
## qcow2硬盘扩容
qemu-img info xx.qcow2 <br>
qemu-img resize xx.qcow2 +3G 

## SCP上传文件到服务器 
scp -r /home/ root@192.168.xx.xx:/

## 查找文件
find / -name php.ini

## 大小写问题
setleds +caps

## 时间同步
```c
rpm -ivh http://mirrors.wlnmp.com/centos/wlnmp-release-centos.noarch.rpm
ntpdate ntp1.aliyun.com
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

## 文件权限 大小 所有者 组
r:4 w:2 x:1 <br>
chown 3000000:users /home

## 磁盘扩容(不是扩/根目录,扩根的教程太多了)
在原有的一个数据盘上进行扩容并保证数据不丢失<br>
不用pv,vg云云<br>
```c
umount /dev/sdb1
parted
p
unit s
p
rm 1
mkpart primary ext4 2048 x.xG
e2fsck -f /dev/sdb1
resize2fs /dev/sdb1
重新Mount
```

## Spice
spice-gtk-tools软件包<br>
spicy -h 127.0.0.1 -p 5900
