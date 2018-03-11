      开始

          打开终端，切换到root用户(sudo -i,输入密码)，输入：free -m查看内存状态

          输入df -B M（或df -m）查看各分区当前使用情况

          选择一个较大的分区，建立分区文件：

      [root@lxt lxt]# dd if=/dev/zero of=/swapadd bs=1024 count=524288
      524288+0 records in
      524288+0 records out
      536870912 bytes (537 MB) copied，13.0709 秒，41.1 MB/秒

          /dev/zero 你先要分配空间的盘名；
          /swapadd 分配的名称
          bs=1024 单位
          count=524288 数量（按单位自己算）

      以上命令在根目录新建一个名为swapadd，大小为512M的虚拟内存文件,当然这里根据自身情况而定，win建议是分配实际内存的 1~1.5倍，实际上Linux其实用不了这么多，但是为了方便，还是建议分配和实际内存一样大的虚拟空间，要多大的空间可以按单位自己乘分配越大的空间，执行的速度越慢哦！

      4.执行以下命令启用虚拟内存

      [root@lxt /]# mkswap /swapadd
      Setting up swapspace version 1, size = 524284 KiB
      no label, UUID=a5c8b651-6f64-4414-bb5f-580b742acfce
      [root@lxt /]# swapon /swapadd

          若要想使开机时自启用，则需修改文件/etc/fstab中的swap行：
          /swapadd swap swap defaults 0 0

          删除swap：
              swapoff /swapadd
              rm -f /swapadd
          从fstab移除
              vi /etc/fstab
              删除对应的行
