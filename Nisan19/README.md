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
