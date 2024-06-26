## Install grafana 
1. masuk ke dalam web resmi 

           https://grafana.com/docs/grafana/latest/setup-grafana/installation/redhat-rhel-fedora/
2. Impor GPG Key 

           wget -q -O gpg.key https://rpm.grafana.com/gpg.key
           sudo rpm --import gpg.key
3. Buat Repository Baru Grafana 

           sudo touch /etc/yum.repos.d/grafana.repo
4. Buka file grafana.repo
   
           sudo nano /etc/yum.repos.d/grafana.repo
5. Tambahkan Konfigurasi Repository
   
           [grafana]
           name=grafana
           baseurl=https://rpm.grafana.com
           repo_gpgcheck=1
           enabled=1
           gpgcheck=1
           gpgkey=https://rpm.grafana.com/gpg.key
           sslverify=1
           sslcacert=/etc/pki/tls/certs/ca-bundle.crt
5. Instal Grafana

           sudo dnf install grafana 
6. klik Y lalu enter sampai selesai 
7. Kelola Layanan Grafana
   
        * start services
   
                sudo /bin/systemctl start grafana-server.service
   
        * enabled services
   
                sudo /bin/systemctl enable grafana-server.service
   
        * restart services
   
                sudo /bin/systemctl daemon-reload
   
        * stop services
   
                sudo /bin/systemctl stop grafana-server.service

