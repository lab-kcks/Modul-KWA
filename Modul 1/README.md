# Keamanan Web dan Aplikasi
## Introduction

### Fundamental Security Concepts
Prinsip utama dari Information Security adalah menghindari **pencurian, perusakan and gangguan** dengan menggunakan sistem **CIA Triad** (Confidentiality, Integrity and Availability).

<p align="center">
<img width="50%" src="https://i.ytimg.com/vi/AJTJN4wDBM8/hqdefault.jpg">
</p>

- **Confidentiality**
Menjaga sistem dan data agar tidak diakses, dilihat, dibaca oleh siapa pun yang tidak berwenang untuk melakukannya.

- **Integrity**
Melindungi data dari modifikasi atau penghapusan oleh pihak yang tidak berwenang, dan memastikan bahwa ketika orang yang berwenang membuat perubahan yang seharusnya tidak dilakukan, kerusakan dapat dibatalkan.

- **Availability**
Sistem, saluran akses, dan mekanisme otentikasi semuanya harus berfungsi dengan baik agar informasi yang mereka berikan dan lindungi tersedia saat dibutuhkan.

**Note:** *Selain itu, properti lain, seperti keaslian, akuntabilitas, non-penyangkalan, dan keandalan juga dapat dilibatkan. (ISO/IEC 27000:2009)*

- **Auditing & Accountability**
Pada dasarnya terus lacak semuanya, seperti, siapa yang masuk kapan mereka masuk dan siapa yang mengakses data ini.

- **Non-Repudiation**
Non-repudiation adalah jaminan bahwa seseorang tidak dapat menyangkal validitas dari suatu hal atau perkara. Non-repudiation adalah konsep hukum yang banyak digunakan dalam keamanan informasi dan mengacu pada layanan, yang memberikan bukti asal data dan integritas data.

### **Security, Functionality and Usability balance**

Ada ketergantungan antar ketiga atribut ini. Ketika aspek sekuritas diprioritaskan, usability dan fungsionalitas turun. Setiap organisasi harus menyeimbangkan antara ketiga kualitas ini untuk sampai pada sistem informasi yang seimbang. 

<p align="center">
<img width="50%" src="https://gist.githubusercontent.com/Samsar4/62886aac358c3d484a0ec17e8eb11266/raw/f14455ed4def635e1bc93b85657f43dbbf4a3127/triad2.png">
</p>


### Types of Hacker

<p align="center">
<img width="50%" src="https://www.simplilearn.com/ice9/free_resources_article_thumb/types-hacker.JPG">
</p>

> - **Black Hat** - Hackers yang melakukan tindakan kejahatan seperti menjual data atau menjual celah keamanan yang ditemukan.
> - **Gray Hat** - Hackers yang melakukan tindakan baik ataupun buruk pada suatu organisasi/perusahaan yang dia serang tanpa meminta atau diberikan ijin terlebih dahulu.
> - **White Hat** - Ethical hackers; Mereka menggunakan keahlian mereka untuk meningkatkan keamanan dengan mengekspos kerentanan sebelum black hat.

**Script Kiddie / Skiddies** - Individu tidak terampil yang menggunakan skrip atau program jahat, seperti web shell, yang dikembangkan oleh orang lain untuk menyerang sistem komputer dan jaringan serta merusak situs web. 

**State-Sponsored Hacker** - Hacker yang dipekerjakan oleh pemerintah atau entitas terkait .

**Hacktivist** - Seseorang yang melakukan serangan dengan maksud tertentu misalnya isu politik.

**Suicide Hackers** - hackers yang tidak takut masuk penjara atau menghadapi hukuman apa pun.

### Threat Categories
* **Network Threats**
  - Information gathering
  - Sniffing and eavesdropping
  - DNS/ARP Poisoning
  - MITM (Man-in-the-Middle Attack)
  - DoS/DDoS
  - Password-based attacks
  - Firewall and IDS attack
  - Session Hijacking

* **Host Threats**
  - Password cracking
  - Malware attacks
  - Footprinting
  - Profiling
  - Arbitrary code execution
  - Backdoor access
  - Privilege Escalation
  - Code Execution

* **Application Threats**
  - Injection Attacks
  - Improper data/input validation
  - Improper error handling and exeception management
  - Hidden-field manipulation
  - Broken session management
  - Cryptography issues
  - SQL injection
  - Phishing
  - Buffer Overflow
  - Information disclosure
  - Security Misconfigurations



### The Five Stages of Ethical Hacking
### 1. **Reconnaissance**
*Mengumpulkan informasi informasti mengenai target*; Terdapat 2 tipe Recon:
- **Passive Reconnaissance**: Mengumpulkan informasi mengenai target **tanpa interaksi langsung dengan sistem** atau yang lebih dikenal dengan OSINT (Open Source Intelligence).
    - e.g: Google Search, Public records, New releases, Social Media.
- **Active Reconnaissance**: Melibatkan interaksi langsung dengan target.
    - e.g: Melakukan panggilan telfon secara langsung, Job interview; menggunakan tools scaning seperti Nmap, Nessus, OpenVAS, Nikto dan Metasploit dapat dikategorikan sebagai Active Recon.

### 2. **Scanning & Enumeration**
*Memperoleh informasi yang lebih mendalam tentang target.*
- e.g: Network Scanning, Port Scanning, Melihat versi versi apa yang berjalan.

### 3. **Gaining Access**
*Serangan ditujukan untuk mendapatkan akses ke dalam sistem.*
- e.g: Dapat dilakukan secara fisik (offline), melalui kabel LAN atau internet.
  - e.g(2): Spoofing untuk mengeksploitasi sistem dengan berpura-pura menjadi pengguna yang sah atau sistem yang berbeda, mereka dapat mengirim paket data yang berisi bug ke sistem target untuk mengeksploitasi vulnerability.
  - Dapat dilakukan dengan menggunakan banyak teknik seperti injeksi perintah, buffer overflow, kredensial brute force, social engineering, misconfiguration, dll..
  
### 4. **Maintaining Access**
*Item ditempatkan untuk memastikan akses di masa mendatang.*
- e.g: Rookit, Trojan, Backdoor.

### 5. **Covering Tracks**
*Langkah-langkah yang diambil untuk menyembunyikan keberhasilan dan intrusi. *
  - e.g: menghapus logs; melakukan obfuscate terhadap backdoor atau malware yang ditanamkan.

