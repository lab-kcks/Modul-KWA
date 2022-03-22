# Keamanan Web dan Aplikasi
## Web Proxy

### Introduction
Saat ini, sebagian besar aplikasi web dan mobile bekerja dengan terus menyambung ke server back-end untuk mengirim dan menerima data dan kemudian memproses data ini di perangkat pengguna. Dengan sebagian besar aplikasi sangat bergantung pada server back-end untuk memproses data, pengujian dan pengamanan server back-end menjadi lebih penting.

Untuk menangkap permintaan dan lalu lintas yang lewat antara aplikasi dan server back-end serta memanipulasi permintaan, kita perlu menggunakan *Web Proxy*

### Apa itu Web Proxy
*Web Proxy* adalah tool yang dapat diatur antara browser/mobile dan server back-end untuk menangkap dan melihat semua permintaan web yang dikirim antara keduanya, yang pada dasarnya bertindak sebagai man-in-the-middle (MITM). web proxy bekerja dengan port web biasanya, seperti port 80 (HTTP) dan 443(HTTPS)

### Kegunaan Web Proxy
- Web application vulnerability scanning
- Web fuzzing
- Web crawling
- Web application mapping
- Web request analysis
- Web configuration testing

### Tool yang Biasa Digunakan
Burp Suite
Burp suite terdapat versi community yang gratis untuk digunakan dan ada versi profesional yang berbayar.
Berikut adalah beberapa fitur yang dapat digunakan pada versi yang gratis:
- Repeating requests
- Encoding/Decoding
- Burp Intruder

Pada versi berbayar terdapat fitur tambahan yaitu:
- Web App Scanner
- Fast Burp Intruder

### Download & Install Burp Suite
1. Pertama yang dilakukan adalah mengunduh Burp Suite pada halaman berikut https://portswigger.net/burp/releases sesuaikan dengan OS kalian.
2. Buka Aplikasi Burp suite pilih Temporary Project, klik tombol nmext. Setelah itu pilih Use Burp defaults, klik tombol start Burp

![](Image/modul_3_tampilan_burp.png)

3. Berikut adalah penampilan aplikasinya

![](Image/modul_3_tampilan_dashboard_burp.png)

### Proxy Setup
Pertama kita harus melakukan konfigurasi untuk menggunakan proxy pada browser kita. Gunakan ekstensi bernama FoxyProxy Standart
![](Image/modul3_FoxyProxy_standart.png)

Mau menggunakan firefox ataupun google chrome sama-sama bisa. Setelah terpasang kita bisa konfigurasi proxynya. Tambahkan Proxy dengan IP 127.0.0.1 dengan port 8080. Karena secara default port web proxy dari burp suite adalah 8080
- Tampilan di Firefox
![](Image/modul_3_konfigurasi_foxyproxy_firefox.png)
- Tampilan di Google Chrome
![](Image/modul_3_konfigurasi_FoxyProxy_Chrome.png)

Jangan lupa untuk melakukan turn on pada proxynya.

### Installing CA Certificate
Langkah selanjutnya adalah melakukan install CA Ceritificate dari web proxynya. Akses http://burp pada browser anda. Maka akan terlihat tampilan seperti ini
![](Image/modul_3_burp.png)

Unduh Certifaicate dengan menekan tombol CA Certificate. Setelah itu tinggal kita pasang CA Certificate pada browser masing masing. Masuk ke bagian setting browser.

- Firefox

Cari Certificates lalu import CA Certificate
![](Image/modul_3_installCA_firefox.png)

- Google Chrome

Masuk ke Security -> Pilih Manage Certificates. Import CA Certificate yang sudah didownload. Pilih Trusted root Certification Authorities jika terdapat sebuah pop up klik saja YES.

![](Image/modul_3_installCA_chrome.png)


Setelah seluruh konfigurasi dilakukan maka seluruh lalu lintas akan dirutekan melalui web proxy (Burp Suite)

### Intercepting Web Requests
Setelah melakukan konfigurasi proxy, kita dapat melakukan intercept dan memanipulasi request dari aplikasi web. Pada sesi ini akan mencoba bagaimana cara untuk melakukan intercept request.

Pada Burp suite terdapat tab bernama Proxy. Didalam tab tersebut tedapat fitur Intercept yang dapat digunakan. Untuk mengaktifkan dan menonaktifkan intercept tinggal tekan tombol on atau off. Untuk melanjutkan request ke server aplikasi tinggal tekan tombol forward.

![](Image/modul_3_intercept_burp.png)

### Repeating Requests
Repeating request memungkinkan kita untuk mengirim ulang permintaan web apapu yang sebelumnya sudah melalui web proxy. Hal ini mempermudah kita untuk memanipulasi pada permintaan tersebut sebelum dikirimkan ke server. Kemudian kita juga bisa melihat response secara langsung.
Cara menggunakannya adalah, di sebelah fitur intercept terdapat tab History. Disana kita bisa lihat history traffict yang melalui proxy listener kita. 

![](Image/modul_3_history_burp.png)

Dari History itu kita dapat pilih salah satu request, klik kana ada pilihan "Send to Repeater". Setelah itu kita dapat berganti ke tab Repeater. Jika ingin mengirim request tinggal klik Button Send

![](Image/modul_3_burp_repeater.png)

### Encoding/Decoding
Pada Burp Suite terdapat fitur Encoder dan Decoder. Fitur tersebut berada pada tab Decoder.
![](Image/modul_3_burp_encoder.png)
Beberapa tipe encode/decode yang tersedia adalah
- Base64
- URL
- ASCII HEX
### Burp Intruder
Salah satu hal yang penting dalam melakukan Web Penetration testing adalah fuzzing. Fuzzing adalah suatu metode untuk mencari kerentanan keamanan dengan mengirimkan beberapa payload. Pada Burp Suite terdapat fitur fuzzing yang berama Burp Intruder.

cara menggunakannya adalah dengan memilih request mana yang ingin dilakukan fuzzing. Bisa memilihnya dari history ataupun request yang sedang diintercept. Lakukan Klik kanan dan pilih "Send to Intruder". Setelah itu kita dapat menentukan posisis parameter yang ingin dilakukan fuzzing. Kita juga dapat memilih Attack typenya. Beberapa Attack type yang tersedia adalah:
- Sniper
- Battering ram
- Pitchfork
- Cluster Bomb
Untuk lebih jelasnya dapat dibaca melalui https://portswigger.net/burp/documentation/desktop/tools/intruder/attack-types 

![](Image/modul_3_intruder.png)

Setelah posisi fuzzing sudah ditentukan saatnya memasukkan payload. Bisa pergi ke tab "Payloads". Disana kalian dapat menambahkan payload sendiri. Untuk melakukan serangan tekan Button "Start Attack"
![](Image/modul_3_intruder_2.png)
### Rekomendasi tool lainnya
Tool lain yang biasa digunakan adalah OWASP ZAP. Fitur kurang lebih sama dengan burp suite, akan tetapi terdapat fitur yang dimana di Burp Suite itu berbayar teteapi di ZAP ini gratis yaitu scanner. Kalian dapat mengunduh ZAP melalui halaman berikut ini:
https://www.zaproxy.org/download/ . Untuk melakukan konfigurasi hampir sama dengan Burp Suite. Tinggal menginstall tool tersebut. Setelah itu mendapatkan CA Certificate dengan membuka ZAP lalu Tools->Options->Dynamic SSL Certificates->Save. Setelah intu pasang CA Certificate pada Web browser. Untuk web proxy ZAP jugra berjalan pada 127.0.0.1 port 8080 sama seperti Burp Suite.
![](Image/modul3_halaman_zap.png)

## Keamanan Aplikasi Web

### Introduction
Dalam pembuatan website, salah satu faktor yang sangat penting dan perlu perhatian lebih adalah pada sistem keamanannya. Keamanan sebuah website sangatlah penting mengingat begitu banyak data penting dan tersimpan di dalam server website. Perlu diketahui terdapat sebuah organisasi nirlaba internasional yang memiliki visi untuk menjaka keamanan siber terutama pada sebuah aplikasi website, yaitu OWASP (Open Web Application Security Project). OWASP biasanya akan merilis sebuah list 10 celah keamanan yang sering terjadi pada tahun tersebut. Bisa dilihat pada gambar dibawah ini bahwa untuk list top 10 dari 2017 dan 2021 sudah berbeda mulai dari terdapat kategori baru atau perubahan penamaan,ruang lingkup, dan peringkat celah keamanan.

![](Image/top10owasp.png)
## OWASP top 10 2021
### 1. Broken Access Control

Sebuah kontrol akses memberlakukan kebijakan sehingga pengguna tidak dapat bertindak di luar izin yang dimaksudkan. Broken Access Control biasanya menyebabkan terjadinya  unauthorized information disclosure, modification, or destruction dari sebuah data atau bisa juga melakukan sebuah fungsi bisnis diluar batas pengguna yang sudah ditentukan.

### 2. Cryptographic Failures

Banyak sekali sebuah applikasi web ataupun API tidak melakukan proteksi terhadap data yang sensitif dengan menggunakan sebuah enkripsi. Penyerang dapat mencuri atau memodifikasi data seperti melakukan pencurian kartu kredit, pencurian identitas.Data sensitif harus dienkripsi menggunakan algoritma enkripsi modern. Contohnya simpelnya adalah penggunaan TLS (Transport Layer Security) pada sebuah website.

### 3. Injection

Injection terjadi ketika data yang tidak terpercaya dikirim dan dimasukkan ke sebuah query secara langsung tanpa adanya sanitasi. Penyerang dapat merubah query akhir seusai keinginannya dan mengeksekusinya untuk mendapatkan data yang diinginkannya. Contohnya adalah SQL Injection.

### 4. Insecure Design
Jangan lupakan hal terpenting sebelum memulai coding aplikasi yaitu membuat sebuah design alur aplikasi yang aman. Kita sebagai programmer harus mengetahui ancaman apa yang akan kita hadapi. Seperti memetakan mana saja yang merupakan public data,private data, restricted data, dan mungkin saja High risk data (token, password). Perlu diperhatikan untuk membuat pesan kesalahan kepada user yang aman(tidak mengekspos error message yang mengandung data sensitif). Celah keamanan yang termasuk dalam kategori ini sebenarnya sangat luas, dan lebih berfokus kepada desain keamanan yang hilang atau salah. Secure design sendiri adalah culture dan metodologi yang terus-menerus mengevaluasi threats dan memastikan bahwa kode yang dirancang diuji dengan detail untuk mencegah metode serangan yang diketahui. Diperlukan suatu kebijakan dan aturan yang kuat dalam proses pengembangan aplikasi. Salah satu contohnya adalah implementasi DevSecOps, yaitu implementasi aspek security pada software development lifecycle. Dalam secure design juga mengawasi celah keamanan supply chain, atau memastikan aplikasi/library dari pihak ketiga aman dan dalam versi paling mutakhir.

### 5. Security Misconfiguration

"Your software is only as secure as you configure it to be". Perlu disadari standar konfigurasi secara default belum tentu membuat sebuah software tersebut sudah aman. Bisa saja akun default pada sebuah software/aplikasi yang digunakan jadi pintu masuk oleh hacker untuk melakukan ekploitasi lebih lanjut. Tidak hanya sistem operasi, frameworks, libraries, dan aplikasi harus dikonfigurasi dengan aman, tetapi juga harus diperbarui secara tepat waktu.

### 6. Vulnerable and Outdated Components

Sebuah komponen seperti library,frameworks, dan juga modul software berjalan pada pivilege yang sama dengan sebuah aplikasi website yang menggunakan komponen tersebut. Jika terdapat sebuah komponen yang vulnerable maka bisa saja terjadi pencurian data ataupun server takeover. Sebuah aplikasi menggunakan komponen yang memiliki kerentanan yang sudah diketahui maka dapat terjadi serangan yang mengakibatkan kerugian. Contohnya adalah kasus Log4j. Banyak sekali yang menggunakan log4j di java  untuk membuat sebuah log. Disini log4j ditemukan kerentanan Remote Code Execution dengan mengeksploitasi insecure JNDI lookups sehingga banyak sekali aplikasi yang terkena serangan Remote code Execution.Contohnya adalah Mincecraft. Sehingga perushaan yang menggunakan log4j cepat-cepat menambal celah keamanan tersebut.

![](Image/log4j.png)

### 7. Identification and Authentication Failures

Fungsi aplikasi yang terkait dengan otentikasi dan manajemen sesi sering diimplementasikan secara tidak benar. Hal ini memungkinkan penyerang untuk mengkompromikan kata sandi, kunci, atau token sesi, atau untuk mengeksploitasi kelemahan implementasi lain untuk menyamamar/menggunakan identitas pengguna lain untuk sementara atau permanen.

### 8. Software and Data Integrity Failures

Software and Data Integrity Failures adalah tipe celah keamanan yang muncul ketika proses pengambilan/penginstallan library dari sumber yang tidak terpercaya. Pada tahun lalu, 2021, terdapat salah satu celah keamanan yang membuat perusahaan perusahaan besar seperti Facebook, Apple, Amazon, Netflix, Google, Microsoft termasuk menjadi korban dari tipe serangan dependency confusing. Dependency confusing adalah serangan dimana ketika software melakukan update library/aplikasi dia mengambil dari repository yang tidak terpercaya dan sudah disisipi code berbahaya. Celah keamanan ini muncul karena software tidak melakukan pengecekan darimana libirary tersebut diinstal dan apakah data didalamnya sesuai dengan yang diinginkan atau tidak. 

### 9. Security Logging and Monitoring Failures

Security Logging dan Monitoring sangatlah penting. Logging dan Monitoring dibutuhkan untuk melihat apa saja yang terjadi pada sebuah aplikasi website (apakah ada aktivitas yang mencurigakan atau tidak). Dengan cacatnya sistem Logging dan Monitoring mengakibatkan terlambatnya proses Incident response. Hal ini mengakibatkan jika aplikasi berhasil diserang maka attacker akan dengan mudahnya melakukan ekploitasi lebih dalam tanpa langsung diketahui oleh pemilik aplikasi.

### 10. Server-Side Request Forgery

Server Side Request Forgery (SSRF) mengacu pada serangan di mana penyerang dapat mengirim permintaan yang dibuat dari aplikasi web yang rentan. SSRF biasanya digunakan untuk menargetkan sistem internal di belakang firewall yang biasanya tidak dapat diakses oleh penyerang dari jaringan eksternal. Contohnya adalah sebuah website yang dapat membuat HTTP request ke sebuah domain yang diberikan oleh user, kemungkinan besar terdapat celah SSRF didalamnya.

![](Image/ssrf.png)