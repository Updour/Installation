## Installasi Apache 
1. Instal Apache (httpd) menggunakan dnf.
        
        sudo dnf install httpd -y

2. Enable Apache Service

        sudo systemctl enable httpd.service
3. Start Apache Service

        sudo systemctl start httpd.service
4. Reload Apache (Jika Diperlukan)

        sudo systemctl reload httpd.service
5. Cek Status Apache

        sudo systemctl status httpd.service
7. 


## Installasi Mysql
1. Update sistem operasi:

        sudo dnf update

2. Install MySQL Server:

        sudo dnf install mysql-server -y

3. Mulai dan aktifkan MySQL:

        sudo systemctl start mysqld
        sudo systemctl enable mysqld

4. Amankan instalasi MySQL:

        sudo mysql_secure_installation

5. Masuk ke MySQL sebagai root:

        sudo mysql -u root -p

6. Buat pengguna baru:

        CREATE USER 'ruut'@'localhost' IDENTIFIED BY 'new_PassW0rd';

7. Berikan hak akses penuh:

        GRANT ALL PRIVILEGES ON *.* TO 'ruut'@'localhost' WITH GRANT OPTION;

8. Berikan hak akses ke satu database:
    
        GRANT ALL PRIVILEGES ON database_name.* TO 'ruut'@'localhost';
9. Segarkan hak akses:

        FLUSH PRIVILEGES;
10. Periksa hak akses pengguna:

        SHOW GRANTS FOR 'ruut'@'localhost';
11. Buat database baru:
    
        CREATE DATABASE test_database;


## Error yang biasa kita temui
1. Masuk ke MySQL

        mysql -u root -p
2. Berikan Hak Akses SELECT pada Tabel Tertentu
    
        GRANT SELECT ON rocky.clients TO 'ruut'@'localhost';
3. Berikan Hak Akses SELECT pada Tabel Lainnya

        GRANT SELECT ON rocky.users TO 'ruut'@'localhost';
4. Flush Privileges

        FLUSH PRIVILEGES;

    

## Mengecek Status Docker 

1.  Menampilkan docker yang sedang berjalan 

        docker ps
2.  Menampilakn docker yang sedang tersimpan

        docker images
3.  Menhentikan docker yang sedang berjalan 

        docker stop pmm-server
4.  Restart docker

        docker start pmm-server
5.  Stop docker 

        docker rm pmm-server


 
