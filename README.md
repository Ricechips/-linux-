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
