title: linux-disk-manage
date: 2015-03-09 17:36:32
tags:
  - linux
  - system
  - disk
categrioes: linux
---
####查看硬盘使用情况
* df 命令
说明: 查看已挂载磁盘的总容量、使用容量、剩余容量等
常用选项有:
-i 可查看 inode 使用情况。
-k -m 分别表示为使用K，M为单位表示。
-h 使用合适的单位显示，例如G

* du 命令
说明: 用来查看某个目录所占空间大小
常用选项有:
-s 汇总显示
-k -m 分别表示为使用K，M为单位表示。

####扩展硬盘容量
> 分为使用LVM管理磁盘和不使用LVM管理磁盘两种情况，本次介绍的是没有使用 LVM 管理磁盘的情况。

1. 使用 fdisk 命令查看和修改磁盘的信息。

* 查看磁盘信息
	fdisk -l [Device]

```
$ fdisk -l /dev/sda
Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders, total 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017b73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    16007167     8002560   83  Linux
/dev/sda2        16007168    78125055    31058944   83  Linux
```

* 修改磁盘信息
	fdisk [Device]
``` shell
# fdisk /dev/sda
Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
```

2. 使用 mkfs.ext2/ mkfs.ext3 / mkfs.ext4 命令格式化分区。

> 根据需求选择合适的命令进行格式化。
	mkfs.extX [partition]

```shell
# mkfs.ext4 /dev/sda1
```

3. 使用 e2label 命令查看和修改分区的Label。
查看

修改

4. 使用 mount 挂载分区。
强制卸载，挂载和卸载的时候注意不要再挂载目标目录

5. 修改 /etc/fstab 文件添加开机自动挂载分区。
####