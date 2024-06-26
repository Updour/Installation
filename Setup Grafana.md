## Installasi Grafana dari repository RPM

* [Website Grafana](https://grafana.com/docs/grafana/latest/setup-grafana/installation/redhat-rhel-fedora/)

*  import gpg key:
        ```wget -q -O gpg.key https://rpm.grafana.com/gpg.key```
* perintah ke dua
         ```sudo rpm --import gpg.key```
*  buat file baru :
       ```sudo touch /etc/yum.repos.d/grafana.repo```
*  buka file yang telah di buat:
        ```sudo nano /etc/yum.repos.d/grafana.repo```
*  masukan potongan kode ini ke dalam file tersebut:

   ```
        [grafana]
        name=grafana
        baseurl=https://rpm.grafana.com
        repo_gpgcheck=1
        enabled=1
        gpgcheck=1
        gpgkey=https://rpm.grafana.com/gpg.key
        sslverify=1
        sslcacert=/etc/pki/tls/certs/ca-bundle.crt
   ```
*  lakukan installasi 
        ```sudo dnf install grafana ```
* klik Y lalu enter
* tunggu hingga proses install selesai 
* beberapa services
        
        * start services
        
        sudo /bin/systemctl start grafana-server.service
        
        * enabled services
        
        sudo /bin/systemctl enable grafana-server.service
        
        * restart services
        sudo /bin/systemctl daemon-reload
        
        * stop services
        
        sudo /bin/systemctl stop grafana-server.service
