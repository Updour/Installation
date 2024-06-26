## Install pgadmin4 website | Front end
1. Lakukan update package os 

        sudo dnf update -y
2. Pull pgadmin4 

        sudo docker pull dpage/pgadmin4

3. Initialisasi Port, Username, dan Password 

* -p adalah port 
* PGADMIN_DEFAULT_EMAIL adalah alamat email yang akan digunakan sebagai akun administrator  
* PGADMIN_DEFAULT_PASSWORD  adalah password yang akan digunakan sebagai akun administrator  

        sudo docker run -p 5050:80 \
        -e PGADMIN_DEFAULT_EMAIL=user@domain.com \
        -e PGADMIN_DEFAULT_PASSWORD=supersecret \
        -d dpage/pgadmin4
        793d40ddac0c4cf670495333bc47af88717b98476844396627c853f2a2f8a1fe

4. Tambahkan port ke dalam pengawasan firewall 

        sudo firewall-cmd --zone=public --add-port=5050/tcp --permanent
5. Reload firewall

        sudo firewall-cmd --reload

6. Buka browser dan akses 
        
        http://localhost:5050


## Install postgree server | Back end
1. Install EPEL Repository

        sudo dnf install epel-release 

2. Install PostgreSQL Repository

       sudo dnf install https://download.postgresql.org/pub/repos/yum/reporpms/EL-8-x86_64/pgdg-redhat-repo-latest.noarch.rpm

3. Install PostgreSQL Server

        sudo dnf install postgresql-server

4. Konfirmasi Instalasi
        
        klik Y sampe proses installasi selesai

5. Enable PostgreSQL Service
        
        sudo postgresql-setup --initdb

6. Enable PostgreSQL Service

        sudo systemctl enable postgresql

7. Start PostgreSQL Service
        
        sudo systemctl start postgresql


## Tambah database baru 
1. Buka terminal baru & Masuk ke PostgreSQL 

        sudo -u postgres psql       `

2. masuk ke postgree

        sudo -u postgres psql
3. setup user baru 

        CREATE ROLE ruut WITH LOGIN PASSWORD 'password';
4. Berikan Akses untuk Membuat Database

        ALTER ROLE nama_pengguna CREATEDB;
5. Berikan Hak Akses ke Database Tertentu

        GRANT ALL PRIVILEGES ON DATABASE tb_ssh TO ruut;
6. Keluar dari PostgreSQL

        \q
        
## Install GUI database 
1. Unduh Paket DBeaver

         https://dbeaver.io/download/?start&os=linux&arch=x86_64&dist=rpm
2. Pilih Paket DBeaver

        Linux RPM package (installer)
3. Pergi ke folder Download
4. Pilih file yang di download
        
        dbeaver-ce-24.1.1-stable.x86_64.rpm
5. Double klik pada file tersebut
6. Klik install

##  Mengatasi error "connection failed 5432"
ini di karenakan port dan localnya belum ke buka untuk di open

1. Cek Status PostgreSQL

        sudo systemctl status postgresql
2.  Start PostgreSQL Jika Tidak Aktif

        sudo systemctl start postgresql
3. Periksa Port PostgreSQL

        sudo ss -tlnp | grep 5432
4. Setup postgresql.conf

        sudo nano /var/lib/pgsql/data/postgresql.conf
5. Pastikan baris berikut ada dan tidak dikomentari:

        listen_addresses = 'localhost'
        port: 5432
6. Setup pg_hba.conf

        sudo nano /var/lib/pgsql/data/pg_hba.conf
7. Pastikan baris berikut ada:

        host    all             all             127.0.0.1/32            md5
8. Restart PostgreSQL

        sudo systemctl restart postgresql
9. Periksa Firewall

        sudo firewall-cmd --zone=public --add-port=5432/tcp --permanent
        sudo firewall-cmd --reload
        
