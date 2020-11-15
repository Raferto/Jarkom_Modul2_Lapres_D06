# Jarkom_Modul2_Lapres_D06

 - **Rafid Ferdianto - 05111840000032**
 - **Abdur Rohman - 05111840000100**

## Soal
 ### Keterangan
  3 buah server yang berada di MALANG, MOJOKERTO dan PROBOLINGGO. Server MALANG akan digunakan sebagai DNS Server Master, MOJOKERTO akan digunakan sebagai DNS Server Slave dan PROBOLINGGO akan digunakan sebagai Web Server. Selain 3 server terdapat 2 klien yang digunakan untuk testing yaitu GRESIK dan SIDOARJO. Untuk menyambungkan semua jaringan tersebut diberi router di SURABAYA.

### Soal 1
  **Membuat website utama dengan alamat http://semerud06.pw**
  
  - Pertama pada uml **Malang**, dibuat domain dengan menambahkan zone **semerud06.pw**, pada file **/etc/bind/named.conf.local**
  ![s1](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_conf1.png)
  
  - Selanjutnya dibuat bind yang mengarah pada ip **probolinggo**, pada file **/etc/bind/jarkom/semerud06.pw**
  ![s1](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_semeru.png)
  
  - Screenshot Test
  ![s1](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/1.png)
  
### Soal 2
  **Membuat alias dengan alamat http://www.semerud06.pw**
  
  - Caranya adalah pada uml **Malang**, ditambahkan **CName** dengan nama **www** yang mengarah ke **semerud06.pw.**, pada file **/etc/bind/jarkom/semerud06.pw**
  ![s2](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_semeru.png)
 
  - Screenshot Test
  ![s2](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/2.png)
  
### Soal 3
  **Membuat subdomain http://penanjakan.semeruyyy.pw yang diatur DNS-nya pada MALANG dan mengarah ke IP Server PROBOLINGGO**
  
  - Caranya adalah pada uml **Malang**, ditambahkan record **A** dengan nama **penanjakan** mengarah ke IP **probolinggo** pada file **/etc/bind/jarkom/semerud06.pw**
  ![s3](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_semeru.png)
  
  - Screenshot Test
  ![s3](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/3.png)
  
### Soal 4
  **Reverse domain utama**
  
  - Caranya adalah pada uml **Malang**, dibuat zone **79.151.10-in-addr.arpa**, pada file **/etc/bind/named.conf.local**
  ![s4](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_conf2.png)
  
  - Selanjutnya ditambahkan record **PTR** byte milik IP **Probolinggo*, pada file **/etc/bind/jarkom/79.151.10-in-addr.arpa**
  ![s4](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_reverse.png)
 
 - Screenshot Test
  ![s4](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/4.png)
  
### Soal 5
  **Membuat DNS server Slave pada MOJOKERTO**
  
  - Caranya adalah pada uml **Malang**, ditambahkan **also-notify** dan **allow-transfer** di zone **semerud06**, pada file **/etc/bind/named.conf.local**
  ![s5](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_conf1.png)
  
  - Selanjutnya pada uml **Mojokerto**, dibuatkan zone **semerud06** dengan master IP **Malang**, pada file **/etc/bind/named.conf.local**
  ![s5](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/Mojokerto_conf.png)
 
 - Screenshot Test
  ![s5](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/5.png)
  
### Soal 6
  **Membuat subdomain dengan alamat http://gunung.semerud06.pw yang didelegasikan pada server MOJOKERTO dan mengarah ke IP Server PROBOLINGGO**
  
  - Caranya adalah pada uml **Malang**, ditambahkan record delegasi yang mengarah pada IP **Probolinggo* pada file **/etc/bind/jarkom/semerud06.pw**
  ![s6](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/malang_semeru.png)
  
  - Berikutnya pada uml **Mojokerto**,  dibuatkan zone **gunung.semerud06.pw** dengan bind ke **/etc/bind/delegasi/gunung.semerud06.pw**, pada file **/etc/bind/named.conf.local**
  ![s6](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/mojokerto_conf.png)
  
  - Terakhir pada file **/etc/bind/delegasi/gunung.semerud06.pw**, disetting sebagai berikut:
  ![s6](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/mojokerto_gunung.png)
  
  - Screenshot Test
  ![s6](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/6.png)
  
### Soal 7
  **Membuat subdomain dengan nama http://naik.gunung.semeruyyy.pw, domain ini diarahkan ke IP Server PROBOLINGGO**
  
  - Caranya adalah pada uml **Mojokerto**, ditambahkan record **A** dengan nama **naik** dengan IP **Probolinggo* pada file **/etc/bind/delegasi/gunung.semerud06.pw**
  ![s7](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/mojokerto_gunung.png)
  
  - Screenshot Test
  ![s7](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/7.png)
  
### Soal 8
  **Membuat domain http://semerud06.pw memiliki Document Root pada /var/www/semerud06.pw**
  
  - Pertama-tama pada uml **Probolinggo**, install **apache2** dan **php5**, serta **unzip**
  - Kemudian pada folder **etc/apache2/sites-available** di-copy-kan file default ke semerud06.pw
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/probolinggo_cp.png)
  
  - Selanjutnya ditambahkan servername, alias dan document root sesuai soal
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/probolinggo_semeru.png)
  
  - Lalu pada folder **/var/www** didownload file/folder pendukung untuk web semeru dengan perintah **wget 10.151.36.202/semeru.pw.zip**
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/probolinggo_download.png)
  
  - Setelah selesai download, zip diekstrak dan kemudian diganti nama menjadi semerud06.pw.
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/probolinggo_ekstrak.png)
  
  - Terakhir enable site dengan perintah **a2ensite** dan Apache2 direstart
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/probolinggo_en&res.png)
  
  - Screenshot Test
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/8.png)
