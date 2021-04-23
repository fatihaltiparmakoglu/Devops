# CASE

## CASE-1

## 1.1

Üzerinde centos işletim sistem olan bir sanal makine kurulduktan sonra paketleri güncellemek için aşağıdaki komut çalıştırılır.

``[root@test ~]# yum update``

Güncellenen paketlerin içerisinde herhangi bir kernel güncellemesi varsa aşağıdaki komut çalıştırılarak makine yeniden başlatılır.

``[root@test ~]# reboot``

## 1.2

Aşağıdaki komut ile kullanıcı oluşturulur.

``[root@test ~]# adduser fatih.altiparmakoglu``

Aşağıdaki komut ile oluşturduğumuz kullanıcıya parola atanır.

``[root@test ~]# passwd fatihaltiparmakoglu``

Kullanıcı oluşturulup parola atandıktan sonra bu oluşturduğumuz kullanıcının sudo ile işlemleri yapabilmesi için /etc/sudoers dosyasına eklenip yetkilendirmenin yapılması gerekmektedir. Aşağıdaki komut ile bu işlem yapılır.

``[root@test ~]# echo “fatih.altiparmakoglu ALL=(ALL) ALL” >> /etc/sudoers``

Bu adımlar tamamlandıktan sonra aşağıdaki komut ile oluşturduğumuz kullanıcıya geçilir.

``[root@test ~]# su - fatih.altiparmakoglu``

## 1.3

Aşağıdaki komut ile mevcut algılanmış disk partitionları görülür.

``[fatih.altiparmakoglu@test ~]$ sudo fdisk -l``

```
[fatih.altiparmakoglu@test ~]$ sudo fdisk -l

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

[fatih.altiparmakoglu@test ~]$
```

10 Gb disk eklendikten sonra aynı komutu çalıştırdığımızda yeni eklenen 10 Gb disk /dev/sdb şeklinde görülür.

```
[fatih.altiparmakoglu@test ~]$ sudo fdisk -l

Disk /dev/sda: 42.9 GB, 42949672960 bytes, 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x0009bec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM

Disk /dev/sdb: 10.7 GB, 10737418240 bytes, 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/centos-root: 37.6 GB, 37576769536 bytes, 73392128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/centos-swap: 4294 MB, 4294967296 bytes, 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

[fatih.altiparmakoglu@test ~]$
```

Bu yeni eklenen diski partition oluşturmak için aşağıdaki komut çalıştırılır.

``[fatih.altiparmakoglu@test ~]$ sudo fdisk /dev/sdb``

```
[fatih.altiparmakoglu@test ~]$ sudo fdisk /dev/sdb
Welcome to fdisk (util-linux 2.23.2).

Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Device does not contain a recognized partition table
Building a new DOS disklabel with disk identifier 0xd1fd8c8a.

Command (m for help): n
Partition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-20971519, default 2048):
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-20971519, default 20971519):
Using default value 20971519
Partition 1 of type Linux and of size 10 GiB is set

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
[fatih.altiparmakoglu@test ~]$
```

```
[fatih.altiparmakoglu@test ~]$ sudo fdisk -l

Disk /dev/sda: 42.9 GB, 42949672960 bytes, 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0x0009bec9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM

Disk /dev/sdb: 10.7 GB, 10737418240 bytes, 20971520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk label type: dos
Disk identifier: 0xd1fd8c8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    20971519    10484736   83  Linux

Disk /dev/mapper/centos-root: 37.6 GB, 37576769536 bytes, 73392128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/centos-swap: 4294 MB, 4294967296 bytes, 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

[fatih.altiparmakoglu@test ~]$

```

Ardından aşağıdaki komutlar ile oluşturduğumuz partition biçimlendirip, /bootcamp dizini oluşturup, bu oluşturulan dizine mount edilir.

```
[fatih.altiparmakoglu@test ~]$ sudo mkfs.ext4 /dev/sdb1
mke2fs 1.42.9 (28-Dec-2013)
Discarding device blocks: done
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
655360 inodes, 2621184 blocks
131059 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2151677952
80 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done
Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

[fatih.altiparmakoglu@test ~]$
```

``[fatih.altiparmakoglu@test ~]$ sudo mkdir /bootcamp``

``[fatih.altiparmakoglu@test ~]$ sudo mount /dev/sdb1 /bootcamp``

Mount edilen disk aşağıdaki "df -h" çıktısında /bootcamp dizinine mount edildiği görülür.

```
[fatih.altiparmakoglu@test ~]$ df -h
Filesystem               Size  Used Avail Use% Mounted on
devtmpfs                 3.9G     0  3.9G   0% /dev
tmpfs                    3.9G     0  3.9G   0% /dev/shm
tmpfs                    3.9G  8.8M  3.9G   1% /run
tmpfs                    3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/mapper/centos-root   35G  1.5G   34G   5% /	
/dev/sda1               1014M  193M  822M  19% /boot
tmpfs                    783M     0  783M   0% /run/user/0
/dev/sdb1                9.8G   37M  9.2G   1% /bootcamp
[fatih.altiparmakoglu@test ~]$
```

## 1.4

Aşağıdaki komut ile /opt/bootcamp dizini oluşturulur.

``[fatih.altiparmakoglu@test ~]$ sudo mkdir /opt/bootcamp``

Dizin oluşturulduktan sonra aşağıdaki komut ile /opt/bootcamp/bootcamp.txt dosyasının içine "merhaba trendyol" yazılmış olur.

``[fatih.altiparmakoglu@test ~]$ sudo echo "merhaba trendyol" | sudo tee /opt/bootcamp/bootcamp.txt``

## 1.5

Aşağıdaki komut ile /opt/bootcamp/bootcamp.txt dosyası /bootcamp diskine taşınmış olur.

``[fatih.altiparmakoglu@test ~]$ sudo find / -name "bootcamp.txt" -exec mv {} /bootcamp/ \;``



