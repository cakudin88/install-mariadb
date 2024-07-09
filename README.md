# install-mariadb
INSTALL MARIADB BIAR BISA DIREMOTE
Setting MariaDB Server
Buka file konfigurasi MariaDB menggunakan nano.

sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf
Cari bind-address ganti nilainya dari 127.0.0.1 menjadi 0.0.0.0 atau langsung menggunakan IP address dari server.

bind-address = 127.0.0.1, server hanya menerima koneksi TCP/IP yang masuk melalui 127.0.0.1.
bind-address = 149.28.159.140, server hanya menerima koneksi TCP/IP yang masuk melalui IPv4 yang diisikan.
bind-address = 0.0.0.0, server menerima koneksi TCP/IP yang masuk melalui semua IPv4 yang ada pada interface jaringan.
Dapat memasang lebih dari satu bind-address seperti gambar di bawah ini.
cara setting akses remote database mariadb

Kemudian restart service

sudo systemctl restart mysql
sudo systemctl restart mysql
Membuat user dan database jika belum ada.

mysql -u root -p

MariaDB [(none)]> CREATE DATABASE mydb;
MariaDB [(none)]> CREATE USER 'musa'@'%' IDENTIFIED BY 'rahasia';
MariaDB [(none)]> GRANT ALL PRIVILEGES ON mydb.* TO 'musa'@'%';
MariaDB [(none)]> FLUSH PRIVILEGES;
mysql -u root -p
 
MariaDB [(none)]> CREATE DATABASE mydb;
MariaDB [(none)]> CREATE USER 'musa'@'%' IDENTIFIED BY 'rahasia';
MariaDB [(none)]> GRANT ALL PRIVILEGES ON mydb.* TO 'musa'@'%';
MariaDB [(none)]> FLUSH PRIVILEGES;
Login ke database dengan user root.
Membuat database mydb.
Membuat user musa@ip-address-apapun dengan password rahasia.
Memberikan semua hak akses untuk database mydb dengan semua tabel yang ada kepada user musa@ip-address-apapun.
Reload hak akses.
