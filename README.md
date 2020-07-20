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

## 透传USB
virsh attach-device $domain_name usb.xml
```c
脚本
#!bin/sh
lsusb > junk2.txt
diff junk.txt junk2.txt > junk3.txt
sed -n '4p' junk3.txt | awk '{print $5}' > junk4.txt
I = $(cat junk4.txt) 
expr substr "$I" 2 2 > junk5.txt
I1 = $(cat junk5.txt)
echo "<hostdev mode='subsystem' type='usb' managed='yes'>
      <source>
        <vendor id='0x15d9'/>
        <product id='0x0a4e'/>
        <address bus='2' device='$I1'/>
      </source>
      </hostdev>"> device.xml
virsh attach-device win10-2 device.xml    
```

##
/usr 全名為 unix software resource 縮寫，放置系統相關軟體、服務（注意不是 user 的縮寫喔！)<br>
{n}dd {n}：刪除游標所在的那一行往下數 {n} 行
watch -n 1 pkill -USR1 -x dd 拷贝u盘进度条
