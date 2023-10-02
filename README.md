# Aplikasi Web "InvenTree"

<div align="center">
    <img src="img/inventree.png" alt="InvenTree logo" width="400" height="auto" />
</div>

## :star2: Sekilas Tentang

InvenTree adalah Sistem Manajemen Inventaris yang menyediakan kontrol stok tingkat rendah dan pelacakan suku cadang yang kuat. Inti dari sistem InvenTree adalah backend basis data Python/Django yang menyediakan antarmuka admin (berbasis web) dan REST API untuk interaksi dengan antarmuka dan aplikasi eksternal. Sistem plugin yang kuat menyediakan dukungan untuk aplikasi dan ekstensi khusus.

## :star2: Instalasi

### Kebutuhan Sistem
- Linux OS (Ubuntu 20.04 LTS atau Debian 11)
- Docker

### Langkah Instalasi
Terdapat 2 pilihan instalasi, yaitu dengan menggunakan docker atau instalasi secara langsung pada sistem.

### Login ke server menggunakan ssh
```
ssh komdatakses@20.187.109.229
```
<details>
    <summary>Dengan Docker</summary>
    <p>
    
### Docker
Instalasi menggunakan docker akan menjalankan sistem lengkap beserta demo data.

#### 1. Install docker terlebih dahulu:
- Ubuntu: [Panduan Instalasi Docker pada Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
- Debian: [Panduan Instalasi Docker pada Debian](https://docs.docker.com/engine/install/debian/)

#### 2. Clone repository
```
git clone https://github.com/inventree/InvenTree.git
```

#### 3. Import demo data
```
docker compose run inventree-dev-server invoke install
docker compose run inventree-dev-server invoke setup-test --dev
```

#### 4. Pengaturan port (opsional)
Anda dapat mengatur port dimana web akan berjalan. Secara default, web server akan berjalan pada port 8000.
```
ports:
    # Expose web server on port 8000
    - 8000:8000
```

#### 5. Jalankan menggunakan docker compose
```
docker compose up -d
```
Aplikasi web akan dapat diakses melalui http://localhost:8000 atau http://ip-vm:8000 jika Anda melakukan instalasi menggunakan virtual machine.

#### Login Details

Terdapat beberapa akun default yang disediakan, sebagaimana diuraikan di bawah ini. Setiap akun diberikan seperangkat izin yang berbeda, sehingga pengguna dapat melihat bagaimana sistem oles/permission InvenTree  berfungsi.

| Username | Password | Description |
| --- | --- | --- |
| allaccess | nolimits | View / create / edit all pages and items |
| reader | readonly | Can view all pages but cannot create, edit or delete database records |
| engineer | partsonly | Can manage parts, view stock, but no access to purchase orders or sales orders |
| admin | inventree | Superuser account, access all areas plus administrator actions |

</details>

<details>
    <summary>Tanpa Docker</summary>
    <p>

### Bare Metal

#### 1. Quick Script
Untuk instalasi pada bare metal cukup jalankan script berikut.
```
wget -qO install.sh https://get.inventree.org && bash install.sh
```
Script tersebut akan melaksanakan semua instalasi tanpa adanya input manual. Instalasi akan memakan waktu sekitar 5-10 menit. 

#### Penjelasan
Setelah script tersebut berjalan maka web server akan berjalan pada port 80. Instalasi web tersebut akan menggunakan nginx sebagai reverse proxy, jadi server aslinya berjalan pada port 6000, lalu di reverse proxy oleh nginx sehingga tampil pada port 80.

#### Login Details
Setelah quick script dijalankan dan semua instalasi selesai, maka sistem akan memberikan satu buah akses akun admin untuk login. Berikut merupakan salah satu contohnya.
```
Admin user data:
   Email: admin@example.com
   Username: admin
   Password: 66l2bIfyTD9g6co5NWjsfjFohlhjxL1YLWMeLyGHaKE=
####################################################################################
```
</details>


#### Penjelasan
Setelah script tersebut berjalan maka web server akan berjalan pada port 80. Instalasi web tersebut akan menggunakan nginx sebagai reverse proxy, jadi server aslinya berjalan pada port 6000, lalu di reverse proxy oleh nginx sehingga tampil pada port 80.


## :star2: Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## :star2: Pembahasan

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
      
_**Perbandingan dengan aplikasi web lain yang sejenis (InvenTree VS Fleetbase)**_
#### 1. Bahasa Pemrograman dan Teknologi:

<ul>
    <li>Website InvenTree: Menggunakan bahasa pemrograman Phyton/Django. Database yang digunakan adalah MySQL/PostgreSQL. </li>
    <li>Website Fleetbase: Dikembangkan dengan bahasa pemrograman PHP dan framework Laravel. Database yang digunakan adalah MySQL. Frond-endnya menggunakan Ember.js dan Ember Engines.</li>
</ul>

Perbandingan:

Website Fleetbase menggunakan PHP dan Laravel, sementara InvenTree menggunakan Python dan Django. Pilihan bahasa pemrograman dan framework dapat bergantung pada preferensi pengembang dan kebutuhan proyek.
Website Fleetbase menggunakan MySQL sebagai database, sedangkan InvenTree bisa menggunakan MySQL/PostgreSQL. PostgreSQL biasanya lebih kuat dalam manajemen data kompleks dan memiliki fitur-fitur canggih.

#### 2. Arsitektur Aplikasi:

<ul>
    <li>Website InvenTree: Django menggunakan pola desain yang mirip dengan MVC yang disebut Model-View-Template (MVT), yang juga memisahkan logika aplikasi, tampilan, dan data. </li>
    <li>Website Fleetbase: Menggunakan arsitektur MVC (Model-View-Controller) yang umum digunakan dalam pengembangan web dengan Laravel. Ini memungkinkan pemisahan yang baik antara logika aplikasi, tampilan, dan data.</li>
</ul>

Perbandingan:

Kedua sistem menggunakan pendekatan yang serupa dalam pemisahan tugas antara komponen-komponen inti aplikasi.

#### 3. Kemampuan dan Fitur:

<ul>
    <li>Website InvenTree: Selain fitur dasar manajemen inventori, juga menyediakan fitur-fitur tambahan seperti prediksi permintaan, analisis stok, dan integrasi dengan layanan pihak ketiga seperti sistem akuntansi. </li>
    <li>Website Fleetbase: Memiliki fitur manajemen stok, pelacakan produk, pelanggan, dan penjualan. Memiliki integrasi dengan sistem pembayaran online dan fitur laporan yang kuat.</li>
</ul>

Perbandingan:

Website Fleetbase menawarkan beberapa fitur tambahan yang dapat memberikan nilai tambah dalam manajemen inventori. Selain itu, Fleetbase menyediakan extension yang dpaat digunakan oleh para pengguna. Namun, keduanya tetap memiliki fitur yang sangat lengkap.

#### 4. Komunitas dan Dukungan:

<ul>
    <li>Website InvenTree: Django juga memiliki komunitas yang kuat dan berbagai sumber daya dukungan, serta pustaka ekstensi yang luas.</li>
    <li>Website Fleetbase: Laravel memiliki komunitas yang besar dan aktif dengan banyak sumber daya online, tutorial, dan paket ekstensi.</li>
</ul>

Perbandingan:

Kedua platform memiliki komunitas yang kuat, sehingga pengembang dapat dengan mudah mencari dukungan dan sumber daya tambahan.

#### 5. Tampilan

<div align="center">
    <p float="left">
          <img src="/img/inventreelogin.png" width="400" height="auto" />
          <img src="/img/fleetbaselogin.png" width="400" height="auto" /> 
    </p>
    <p float="left">
          <img src="/img/inventree.jpeg" width="400" height="auto"/>
          <img src="/img/fleetbase.png" width="400" height="auto" /> 
    </p>
</div>

<ul>
    <li>Website InvenTree: dibuat dengan tampilan terang dan masih kurang memperhatikan sisi kenyamanan pengguna.</li>
    <li>Website Fleetbase: dibuat dengan tampilan gelap dan sudah cukup memperhatikan sisi kenyamanan pengguna.</li>
</ul>

Perbandingan:

Website Fleetbase secara UX lebih nyaman untuk digunakan karena tampilannya memudahkan pengguna yang awam sekalipun.

#### 6. Keamanan:

<ul>
    <li>Website InvenTree: Django juga memiliki sejumlah fitur keamanan bawaan dan mempromosikan praktik-praktik keamanan yang baik.</li>
    <li>Website Fleetbase: Laravel dikenal dengan fitur-fitur keamanan bawaannya seperti perlindungan terhadap serangan SQL Injection dan XSS.</li>
</ul>

Perbandingan:

Kedua platform berusaha untuk memberikan tingkat keamanan yang tinggi, tetapi implementasi keamanan akhirnya bergantung pada pengembangan dan konfigurasi proyek secara spesifik.

## Referensi

https://github.com/inventree/
https://github.com/fleetbase/
