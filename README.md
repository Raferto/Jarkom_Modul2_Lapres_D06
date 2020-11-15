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
  
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/8.1.png)
  
  - Selanjutnya ditambahkan servername, alias, dan document root sesuai soal
  
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/8.2.png)
  
  - Lalu pada folder **/var/www** didownload file/folder pendukung dengan perintah **wget 10.151.36.202/semeru.pw.zip**
  
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/8.3.png)
  
  - Setelah selesai download, zip diekstrak dan kemudian diganti nama menjadi semerud06.pw.
  
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/8.4.png)
  
  - Terakhir enable site dengan perintah **a2ensite** dan Apache2 direstart dengan perintah **service apache2 restart**
  
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/8.5.png)
  
  - Screenshot Test
  
  ![s8](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/semeru.png)

### Soal 9
  **Mengaktifkan mod rewrite agar url dari http://semerud06.pw/index.php/home menjadi http://semerud06.pw/home**
  
  - Pertama pada uml **Probolinggo**, diaktifkan mod rewrite dengan perintah **a2enmod rewrite** yang dilanjutkan dengan merestart apache2
  
  ![s9](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/9.1.png)
  
  - Selanjutnya dibuat file **.htaccess** di semerud06.pw, dan diisi sebagai berikut
  
  ![s9](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/9.2.png)
  
  - Berikutnya **Allowoverride** pada file **/etc/apache2/sites-available/semerud06.pw**
  
  ![s9](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/9.3.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s9](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)

  - Screenshot Test
  
  ![s9](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/semeru_home.png)
  
### Soal 10
  **Membuat web http://penanjakan.semerud06.pw agar digunakan untuk menyimpan asset file yang memiliki Document Root pada /var/www/penanjakan.semerud06.pw dan memiliki struktur folder sebagai berikut**
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/10.1.png)
  
  - Pertama-tama pada uml **Probolinggo** folder **/var/www/** didownload File/folder pendukung dengan perintah **wget 10.151.36.202/penanjakan.semeru.pw.zip**
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/10.2.png)
  
  - Setelah selesai download, diunzip dan direname filenya
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/10.3.png)
  
  - kemudian dibuat konfig di **/etc/apache2/sites-available**, dengan di-copy-kan file default ke **penanjakan.semerud06.pw**
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/10.4.png)
  
  - Berikutnya diedit file **penanjakan.semerud06.pw** dengan menambahkan config sebagai berikut:
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/10.5.png)
  
  - Terakhir enable site dengan perintah **a2ensite penanjakan.semerud06.pw** dan Apache2 direstart dengan perintah **service apache2 restart**
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/10.6.png)
  
  - Screenshot Test
  
  ![s10](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/penanjakan.png)

### Soal 11
  **Membuat agar folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan**
  
  - Caranya adalah pada uml **Probolinggo**, ditambahkan **Option +indexes** pada **/public** dan **Option -indexes** pada **/public/css**, **/public/javascript**, **/public/images**
  
  ![s11](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/11.1.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s11](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)
  
  - Screenshot Test
  
  ![s11](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/11.2.png)
  
  ![s11](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/11.3.png)
  
  ![s11](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/11.4.png)
  
  ![s11](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/11.5.png)
  
### Soal 12
  **Membuat custom HTTP error code 404, yang disediakan pada file 404.html pada folder /errors untuk mengganti error default 404 dari apache**
  
  - Caranya adalah pada uml **Probolinggo**, di tambahkan error document 404 pada file **penanjakan.semerud06.pw**
  
  ![s12](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/12.1.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s12](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)
  
  - Screenshot Test
  
  ![s12](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/12.2.png)
  
### Soal 13
  **Membuat agar untuk mengakses file asset javascript yang awalnya harus menggunakan url http://penanjakan.semerud06.pw/public/javascripts, karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file asset menjadi http://penanjakan.semerud06.pw/js**
  
  - Caranya adalah pada uml **Probolinggo**, tambahkan **Alias "/js" "/var/www/penanjakan.semerud06.pw/public/javascripts"**
  
  ![s13](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/13.1.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s13](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)
  
  - Screenshot Test
  
  ![s13](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/13.2.png)
  
### Soal 14
  **Membuat agar http://naik.gunung.semerud06.pw pada port 8888 dengan Document Root pada /var/www/naik.gunung.semerud06.pw**
  
  - Pertama-tama pada uml **Probolinggo** di folder **/var/www/** didownload File/folder pendukung dengan perintah **wget 10.151.36.202/naik.gunung.semeru.pw.zip**, dan diunzip setelah selesai
  
  ![s14](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/14.1.png)
  
  - Kemudian dimove sekaligus direname ke **naik.gunung.semerud06.pw**
  
  ![s14](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/14.2.png)
  
  - Selanjutnya, pada folder **sites-available** dibuat config dengan mengcopy file **default** ke **naik.gunung.semerud06.pw**, yang selanjutnya disetting sebagai berikut
  
  ![s14](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/14.3.png)
  
  - Berikutnya, pada file **apache2/ports.conf** ditambahkan Listen port **8888** 
  
  ![s14](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/14.4.png)
  
  
  - Terakhir enable site dengan perintah **a2ensite naik.gunung.semerud06.pw** dan Apache2 direstart dengan perintah **service apache2 restart**
  
  ![s14](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/14.5.png)
  
  - Screenshot Test
  
  ![s14](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/14.6.png)
  
### Soal 15
  **Membuat autentikasi pada http://naik.gunung.semerud06.pw dengan username semeru dan password kuynaikgunung**
  
  - Pertama-tama pada uml **Probolinggo** di **root**, dijankan command **htpasswrd -c /etc/apache/.htpasswd semeru** dan masukan password 
  
  ![s15](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/15.1.png)
  
  - Selanjutnya pada **naik.gunung.semerud06.pw**, ditambahkan **Auth**
  
  ![s15](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/15.2.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s15](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)
  
  - Screenshot Test
  
  ![s15](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/15.3.png)
  
### Soal 16
  **Membuat agar apabila IP Probolinggo dikunjungi akan secara otomatis dialihkan ke http://semerud06.pw**
  
  - Pertama-tama pada uml **Probolinggo** folder **/var/www**, dibuat directory **default** dan di-move index.html ke sana
  
  ![s16](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/16.1.png)
  
  - Selanjutnya buat **.htaccess** dengan **RewriteEngine** sebagai berikut
  
  ![s16](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/16.2.png)
  
  
  - Kemudian diubah konfigurasi pada **site-available** untuk **default** sebagai berikut
  
  ![s16](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/16.3.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s16](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)
  
  - Screenshot Test
  
  ![s16](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/semeru.png)
  
### Soal 17
  **Membuat agar request gambar yang memiliki substring semeru pada /var/www/penanjakan.semerud06.pw/public/images diarahkan menuju semeru.jpg**
  
  - Pertama-tama pada uml **Probolinggo** dibuat **.htaccess** di **penanjakan.semerud06.pw, dengan **RewriteEngine** sebagai berikut
  
  ![s17](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/17.1.png)
  
  - Selanjutnya pada folder **sites-available** diatur konfigurasinya sebagai berikut
  
  ![s17](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/17.2.png)
  
  - Terakhir apache2 direstart dengan perintah **service apache2 restart**
  
  ![s17](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/restart.png)
  
  - Screenshot Test **semeru** dan/atau **semeru**
  
  ![s17](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/17.3.png)
  
  - Screenshot Test tidak ada substring **semeru**
  
  ![s17](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/17.4.png)
  
  - Screenshot Test tidak ada substring **semeru** dan foto tidak ada
  
  ![s17](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/17.5.png)
