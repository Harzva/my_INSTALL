方法一：

打开terminal，运行如下命令，因为SSD是非转动盘，如果返回结果为0说明是SSD硬盘，如果返回结果为1，说明是转动盘HDD类的硬盘。 
```
[root@foundation83 Desktop]# cat /sys/block/sda/queue/rotational   #表明sda这块硬盘是固态硬盘(SSD)
0
[root@foundation83 Desktop]# cat /sys/block/sdb/queue/rotational   #表明sdb这块硬盘是固态硬盘(SSD)
1
```
方法二：

还可以运行下面命令，同样是根据SSD是非转动盘的属性来区分，返回结果为1，说明不是SSD。
```
[root@foundation83 Desktop]# lsblk -d -o name,rota
NAME  ROTA
sda      0   #sda是固态硬盘(SDD)
sdb      1
loop0    1
loop1    1
```
 
4、lsusb查看USB接口设备信息
#查看硬盘大小
```
# fdisk -l |grep Disk
```
#查看磁盘空间占用情况
```
# df -h
```
