CASE

CASE1

1.1

Üzerinde centos işletim sistem olan bir sanal makine kurulduktan sonra paketleri güncellemek için aşağıdaki komut çalıştırılır.

``[root@test ~]# yum update``

Güncellenen paketlerin içerisinde herhangi bir kernel güncellemesi varsa aşağıdaki komut çalıştırılarak makine yeniden başlatılır.

``[root@test ~]# reboot``

1.2

Aşağıdaki komut ile kullanıcı oluşturulur.

``[root@test ~]# adduser fatih.altiparmakoglu``

Aşağıdaki komut ile oluşturduğumuz kullanıcıya parola atanır.

``[root@test ~]# passwd fatihaltiparmakoglu``

Kullanıcı oluşturulup parola atandıktan sonra bu oluşturduğumuz kullanıcının sudo ile işlemleri yapabilmesi için /etc/sudoers dosyasına eklenip yetkilendirmenin yapılması gerekmektedir. Aşağıdaki komut ile bu işlem yapılır.

``[root@test ~]# echo “fatih.altiparmakoglu ALL=(ALL) ALL” >> /etc/sudoers``

Bu adımlar tamamlandıktan sonra aşağıdaki komut ile oluşturduğumuz kullanıcıya geçilir.

``[root@test ~]# su - fatih.altiparmakoglu``

1.3

Aşağıdaki komut ile mevcut algılanmış disk partitionlarımızı görürüz.

``[fatih.altiparmakoglu@test ~]$ sudo fdisk -l``

`[fatih.altiparmakoglu@test ~]$ sudo fdisk -l

Disk /dev/sda: 42.9 GB, 42949672960 bytes, 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x0009bec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM

Disk /dev/mapper/centos-root: 37.6 GB, 37576769536 bytes, 73392128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/centos-swap: 4294 MB, 4294967296 bytes, 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

[fatih.altiparmakoglu@test ~]$`




