# Aplikasi Web "InvenTree"

<div align="center">
    <img src="img/inventree.png" alt="InvenTree logo" width="400" height="auto" />
</div>

## :star2: Sekilas Tentang

InvenTree adalah Sistem Manajemen Inventaris yang menyediakan kontrol stok tingkat rendah dan pelacakan suku cadang yang kuat. Inti dari sistem InvenTree adalah backend basis data Python/Django yang menyediakan antarmuka admin (berbasis web) dan REST API untuk interaksi dengan antarmuka dan aplikasi eksternal. Sistem plugin yang kuat menyediakan dukungan untuk aplikasi dan ekstensi khusus.

## :star2: Instalasi

- Prasyarat, apa saja yang harus diinstal sebelumnya.
- Langkah instalasi dalam CLI.


## :star2: Cara Pemakaian

- Tampilan aplikasi web
- Fungsi-fungsi utama
- Isi dengan data real/dummy (jangan kosongan) dan sertakan beberapa screenshot


## :star2: Pembahasan

- Pendapat anda tentang aplikasi web ini
    - kelebihan
    - kekurangan
      
_**Perbandingan dengan aplikasi web lain yang sejenis (InvenTree VS Fleetbase)**_
#### Bahasa Pemrograman dan Teknologi:

<ul>
    <li>Website InvenTree: Menggunakan bahasa pemrograman Phyton/Django. Database yang digunakan adalah MySQL/PostgreSQL. </li>
    <li>Website Fleetbase: Dikembangkan dengan bahasa pemrograman PHP dan framework Laravel. Database yang digunakan adalah MySQL. Frond-endnya menggunakan Ember.js dan Ember Engines.</li>
</ul>

Perbandingan:

Website Fleetbase menggunakan PHP dan Laravel, sementara InvenTree menggunakan Python dan Django. Pilihan bahasa pemrograman dan framework dapat bergantung pada preferensi pengembang dan kebutuhan proyek.
Website Fleetbase menggunakan MySQL sebagai database, sedangkan InvenTree bisa menggunakan MySQL/PostgreSQL. PostgreSQL biasanya lebih kuat dalam manajemen data kompleks dan memiliki fitur-fitur canggih.

#### Arsitektur Aplikasi:

<ul>
    <li>Website InvenTree: Django menggunakan pola desain yang mirip dengan MVC yang disebut Model-View-Template (MVT), yang juga memisahkan logika aplikasi, tampilan, dan data. </li>
    <li>Website Fleetbase: Menggunakan arsitektur MVC (Model-View-Controller) yang umum digunakan dalam pengembangan web dengan Laravel. Ini memungkinkan pemisahan yang baik antara logika aplikasi, tampilan, dan data.</li>
</ul>

Perbandingan:

Kedua sistem menggunakan pendekatan yang serupa dalam pemisahan tugas antara komponen-komponen inti aplikasi.

#### Kemampuan dan Fitur:

<ul>
    <li>Website InvenTree: Selain fitur dasar manajemen inventori, juga menyediakan fitur-fitur tambahan seperti prediksi permintaan, analisis stok, dan integrasi dengan layanan pihak ketiga seperti sistem akuntansi. </li>
    <li>Website Fleetbase: Memiliki fitur manajemen stok, pelacakan produk, pelanggan, dan penjualan. Memiliki integrasi dengan sistem pembayaran online dan fitur laporan yang kuat.</li>
</ul>

Perbandingan:

Website Fleetbase menawarkan beberapa fitur tambahan yang dapat memberikan nilai tambah dalam manajemen inventori. Selain itu, Fleetbase menyediakan extension yang dpaat digunakan oleh para pengguna. Namun, keduanya tetap memiliki fitur yang sangat lengkap.

#### Komunitas dan Dukungan:

<ul>
    <li>Website InvenTree: Django juga memiliki komunitas yang kuat dan berbagai sumber daya dukungan, serta pustaka ekstensi yang luas.</li>
    <li>Website Fleetbase: Laravel memiliki komunitas yang besar dan aktif dengan banyak sumber daya online, tutorial, dan paket ekstensi.</li>
</ul>

Perbandingan:

Kedua platform memiliki komunitas yang kuat, sehingga pengembang dapat dengan mudah mencari dukungan dan sumber daya tambahan.

#### Tampilan

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

#### Keamanan:

<ul>
    <li>Website InvenTree: Django juga memiliki sejumlah fitur keamanan bawaan dan mempromosikan praktik-praktik keamanan yang baik.</li>
    <li>Website Fleetbase: Laravel dikenal dengan fitur-fitur keamanan bawaannya seperti perlindungan terhadap serangan SQL Injection dan XSS.</li>
</ul>

Perbandingan:

Kedua platform berusaha untuk memberikan tingkat keamanan yang tinggi, tetapi implementasi keamanan akhirnya bergantung pada pengembangan dan konfigurasi proyek secara spesifik.

## Referensi

https://github.com/inventree/
https://github.com/fleetbase/
