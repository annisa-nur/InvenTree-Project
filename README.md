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

#### Penjelasan
Setelah script tersebut berjalan maka web server akan berjalan pada port 80. Instalasi web tersebut akan menggunakan nginx sebagai reverse proxy, jadi server aslinya berjalan pada port 6000, lalu di reverse proxy oleh nginx sehingga tampil pada port 80.
</details>

## :star2: Cara Pemakaian

Cara pemakaian InvenTree ini sebenarnya tidak terlalu sulit walaupun memiliki _interface_ yang sedikit kompleks. Penjelasan cara pemakaiannya adalah sebagai berikut:

1. Sebelum menggunakan InvenTree, kita perlu login ke dalam Web App-nya terlebih dahulu.
    
   <div align="center">
        <p float="left">
             <img src="/img/inventreelogin.png" width="400" height="auto" />
        </p>
   </div>
        
   Dalam mengakses web App ini terdapat beberapa role yang disesuaikan dengan kebutuhan pengguna. 
       
2. Setelah login, kita akan masuk ke halaman utama dan melihat laporan mengenai stock. Di bagian kiri atas, terdapat berbagai menu yang dapat kita gunakan, seperti            _Parts_, _Stock_, _Build_, _Buy_, dan _Sell_. Kemudian di bagian samping kiri kita juga dapat melihat menu lainnya mengenai _part_, _stock_, dan orderan. 
    <div align="center">
        <p float="left">
             <img src="/img/Homepage.jpeg" width="400" height="auto" />
        </p>
    </div>
    
3. Pada bagian _parts_, terdapat tampilan utama mengenai 4 panel berbeda, yaitu kategori, detail, tab, dan konten setiap tab. Objek _parts_ adalah arketipe dari setiap        item stok dalam _inventoty_. Setiap _part_ yang didefinisikan dalam database menyediakan sejumlah atribut berbeda yang menentukan bagaimana _part_ tersebut dapat           digunakan.
    <div align="center">
        <p float="left">
             <img src="/img/Parts.jpeg" width="400" height="auto" />
        </p>
    </div>
    
4. Bagian _Stocks_ berisi informasi mengenai stok yang dimiliki. Pada bagian ini kita dapat memantau stok barang, lokasi stok, dan status stok.
        <ul>
            <li>Item stok adalah contoh sebenarnya dari item _part_. Ini menyatakan kuantitas fisik dari _part_ di lokasi tertentu.</li>
            <li>Lokasi stok mewakili lokasi fisik dunia nyata tempat stok barang disimpan</li>
            <li>Status stok digunakan untuk melihat kondisi terkini dari masing-masing stok barang apakah baik, perlu perhatian, hancur, hilang, dan status lainnya.</li>
        </ul>
    <div align="center">
        <p float="left">
             <img src="/img/Stock.jpeg" width="400" height="auto" />
        </p>
    </div>
        
5. Menu Build menampilkan informasi mengenai _build orders_. _Build Order_ dari section build digunakan untuk membuat stok baru dengan merakit bagian-bagian komponen, sesuai dengan Bill of Materials (BOM). BOM dapat ditentukan untuk setiap Bagian yang ditetapkan sebagai satu kesatuan. BOM terdiri dari bagian lain yang ditetapkan sebagai Komponen. _Build Order_ menggunakan BOM untuk mengalokasikan stok item ke proses perakitan. Saat Build Order selesai, jumlah stok yang diperlukan dikurangi dari stok item yang dialokasikan.
    <div align="center">
        <p float="left">
             <img src="/img/Build.jpeg" width="400" height="auto" />
        </p>
    </div>
    
6. Menu _Buy_ berisi mengenai catatan yang berkaitan dengan pembelian stok bagi perusahaan. Menu ini dibagi menjadi tiga bagian, yaitu _suppliers_, _manufacturers_, dan _purchase orders_.
        <ul>
            <li>Bagian _suppliers_ berisi mengenai perusahaan-perusahaan yang memasok barang-barang untuk stok</li>
            <li>Bagian _manufacturers_ berisi mengenai perusahaan-perusahaan yang memproduksi barang-barang untuk stok</li>
            <li>_Purchase orders_ memungkinkan untuk melacak suku cadang mana yang dibeli dari pemasok dan produsen, sehingga mengubah barang yang dibeli secara eksternal menjadi barang stok/inventory.</li>
        </ul>
    <div align="center">
        <p float="left">
            <img src="/img/Buy-supplier.jpeg" width="400" height="auto" />
            <img src="/img/Buy-manufacturer.jpeg" width="400" height="auto" />
            <img src="/img/Buy-po.jpeg" width="400" height="auto" />
        </p>
    </div>
        
7. Menu _Sell_ berisi mengenai catatan yang berkaitan dengan penjualan stok. Menu ini juga dibagi menjadi tiga bagian, yaitu _customers_, _sakes orders_, dan _return orders_.
         <ul>
            <li>Bagian _customer_ berisi data mengenai perusahaan atau individu yang menjadi pelanggan</li>
            <li>_Sales orders_ memungkinkan pelacakan item stok mana yang dijual kepada pelanggan, sehingga mengubah stok item atau inventaris menjadi item yang dijual secara eksternal.</li>
            <li>_Return orders_ memungkinkan barang stok (yang telah dijual atau dialokasikan kepada pelanggan) untuk dikembalikan ke dalam stok, biasanya  untuk tujuan perbaikan atau pengembalian uang. </li>
        </ul>

   <div align="center">
        <p float="left">
            <img src="/img/Sell-cust.jpeg" width="400" height="auto" />
            <img src="/img/Sell-salesorder.jpeg" width="400" height="auto" />
            <img src="/img/Sell-RO.jpeg" width="400" height="auto" />
        </p>
    </div>

8. Selain menu-menu mengenai pembelian dan penjualan stok, Inventree juga menyediakan menu lainnya, seperti menu notifikasi yang berfungsi untuk melihat berbagai notifikasi dan riwayat. Kemudian erdapat juga fitur _scan barcode_ dan _search_.
   <div align="center">
        <p float="left">
            <img src="/img/tambahan.jpg" width="400" height="auto" />
        </p>
    </div>

## :star2: Pembahasan

**InvenTree adalah sebuah web App yang ditulis dalam bahasa pemrograman python. Web App ini menggunakan python/Django untuk backend basis datanya. InvenTree menyediakan antarmuka admin (berbasis web) dan REST API untuk interaksi dengan antarmuka dan aplikasi eksternal. Web App ini memiliki beberapa kelebihan dan kekurangan, diantaranya adalah sebagai berikut.**

_**Kelebihan**_

1. Sistem plugin yang kuat menyediakan dukungan untuk aplikasi dan ekstensi khusus.
2. Penggunaan resource memory aplikasi yang tidak terlalu besar
3. Terdapat fitur-fitur tambahan untuk melihat prediksi permintaan, analisis stok, dan integrasi dengan layanan pihak ketiga seperti sistem akuntansi.
4. Proses loading dari aplikasi ini tergolong cepat untuk penggunaan fitur atau modul yang lengkap dan banyak.
    
_**Kekurangan**_

1. Memiliki desain yang tidak responsive, sehingga hanya dapat dibuka menggunakan device tertentu.
2. Memiliki fitur yang sangat banyak dan kompleks sehingga sedikit sulit dipahami cara penggunaannya bari orang awam.


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
