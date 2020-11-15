# Jarkom_Modul2_Lapres_D06

 - **Rafid Ferdianto - 05111840000032**
 - **Abdur Rohman - 05111840000100**

## Soal
### Keterangan
  3 buah server yang berada di MALANG, MOJOKERTO dan PROBOLINGGO. Server MALANG akan digunakan sebagai DNS Server Master, MOJOKERTO akan digunakan sebagai DNS Server Slave dan PROBOLINGGO akan digunakan sebagai Web Server. Selain 3 server terdapat 2 klien yang digunakan untuk testing yaitu GRESIK dan SIDOARJO. Untuk menyambungkan semua jaringan tersebut diberi router di SURABAYA.

### Soal 1
  **Membuat website utama dengan alamat http://semerud06.pw**
  - Pertama buat website dengan menambahkan zone **semerud06.pw**, dengan cara mengedit file **/etc/bind/named.conf.local**
  ![s1](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/1.1)
  
  - Selanjutnya buat bind yang mengarah pada ip **probolinggo**, pada file **/etc/bind/jarkom/semerud06.pw**
  ![s1](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/1.2)
  
  - Screenshot
  ![s1](https://github.com/Raferto/Jarkom_Modul2_Lapres_D06/blob/main/images/1.3)
  
### Soal 2
  **Membuat alias dengan alamat http://www.semerud06.pw**
  - Caranya adalah dengan menambahkan **CName** dengan nama **www** yang mengarah ke **semerud06.pw.**
