# Absensi Fajar v2.0: Enterprise Cloud-Based Attendance System 🚀

## IDENTITAS MAHASISWA :

## Nama : Fajar Fawwaz Atallah 

## Kelas : I241D

## NIM : 312410357

## MATKUL : PEMROGRAMAN MOBILE 

SAYA MEMBUAT TUGAS INI UNTUK MENGERJAKAN TUGAS UTS PEMROGRAMAN MOBILE SEMESTER 4

## DI BAWAH INI ADALAH LIST DI CLICK UP PERUBAHAN DARI APLIKASI SAYA YANG SEBELUMNYA , SAYA MERUBAH SEDIKIT TAMPILAN DAN MENAMBAHKAN BEBERAPA FITUR :

<img width="1271" height="528" alt="image" src="https://github.com/user-attachments/assets/1785ae48-a7c5-4dac-b440-1fe2bf5264a8" />


## UNTUK LINK CLICK UP ( SCRUM ) YANG LEBIH LENGKAPNYA SEBAGAI BERIKUT : https://app.clickup.com/90181768471/v/l/6-901813018848-1

## Absensi Fajar adalah solusi manajemen kehadiran berbasis Android yang menggabungkan presisi Biometric Face Recognition dengan validasi lokasi Geofencing GPS. Sistem ini dirancang untuk memastikan integritas data kehadiran dengan teknologi sinkronisasi Cloud yang aman dan efisien.

# 🏗️ Arsitektur Sistem (System Architecture)

## Aplikasi ini menggunakan model Hybrid Synchronization:1.Local Storage (SQLite): Digunakan untuk manajemen sesi, caching data riwayat, dan operasional offline terbatas.2.Cloud Storage (MySQL via AwardSpace): Berperan sebagai Single Source of Truth (Sumber data utama) untuk monitoring Administrator secara real-time.3.Communication: Menggunakan Retrofit 2 dengan arsitektur REST API untuk pertukaran data format JSON.


# DI Bawah Ini adalah UI login dan  HALAMAN MAHASISWA : 

<img width="1018" height="788" alt="Screenshot 2026-04-30 132424" src="https://github.com/user-attachments/assets/13724084-bac6-4cdf-882d-f33f4a3e873a" />


# 📱 Penjelasan Detail Halaman (Page-by-Page Explanation)

## 1. Modul Mahasiswa (User Interface)

### - Halaman Login & Recovery:

# LOGIN : 

<img width="200" alt="image" src="https://github.com/user-attachments/assets/6eaaffbb-2989-4040-8421-de88a9383aee" />
<img width="200" alt="image" src="https://github.com/user-attachments/assets/bb072d3d-7845-4599-980d-79e0f0179527" />


◦ Mendukung autentikasi ganda (Lokal & Cloud).

◦ Fitur Identity Recovery: Jika user pindah perangkat atau re-install aplikasi, sistem secara otomatis menarik kembali nama, role, dan data wajah (embedding) dari Cloud ke SQLite lokal.

### - Halaman Dashboard Utama:

◦ Statistik Dinamis: Menampilkan total hadir, telat, dan izin yang disinkronkan langsung dari server AwardSpace.

◦ Real-time Greeting: Ucapan selamat berdasarkan waktu sistem (Pagi/Siang/Malam).

◦ Profile Preview: Menampilkan foto profil yang diambil saat pendaftaran wajah.

### - Halaman Registrasi Wajah (Biometric Enrollment):

◦ Menggunakan Google ML Kit untuk mendeteksi wajah dan FaceNet Model untuk mengonversi citra wajah menjadi 192 titik koordinat angka (embeddings).

◦ Data ini di-upload ke Cloud untuk keamanan identitas permanen.

### - Halaman Absensi (Scanning & Geofencing):

◦ Validasi Lokasi: Memeriksa jarak user dengan koordinat Kampus UPB. Jika jarak > 150 meter, akses scan wajah ditutup (mencegah manipulasi lokasi).

◦Biometric Verification: Mencocokkan wajah saat ini dengan data pendaftaran menggunakan algoritma Cosine Similarity.

### - Halaman Riwayat (Attendance History):

◦ Menampilkan list kronologis kehadiran user yang diambil dari basis data lokal (SQLite).

## 2. Modul Administrator (Admin Control Panel)

## - Admin Dashboard:

◦ Global Stats: Menampilkan ringkasan kehadiran seluruh mahasiswa hari ini secara visual.

◦ Digital Clock Real-time: Menunjukkan waktu server yang akurat.

◦ Recent Activity Log: Menampilkan 5 aktivitas absensi terbaru dari seluruh mahasiswa untuk pengawasan instan.

## - Halaman Monitoring Kehadiran (Rekapitulasi):

◦ Daftar seluruh mahasiswa beserta total performa kehadiran (Hadir, Telat, Izin).

◦ Klik pada nama mahasiswa akan membuka halaman Detail Individu.

## - Halaman Daftar Mahasiswa (User Management):

◦ Tampilan format Tabel Zebra (selang-seling warna) untuk kenyamanan membaca data.

◦ Real-time Search: Fitur pencarian instan berdasarkan nama atau email tanpa perlu memuat ulang halaman.

## - Halaman Detail & Export:

◦ Ringkasan profil mahasiswa.

◦ Export to Excel (.xls): Menghasilkan laporan kehadiran individu yang siap cetak untuk keperluan administratif.

## - Halaman Kontrol Sistem (The "Obeng" Feature):

◦ Dynamic Configuration: Admin dapat mengubah radius absensi (misal 150m ke 200m) dan jam masuk secara remote tanpa coding ulang.

◦ Maintenance Tools: Tombol Reset Data untuk mengosongkan riwayat absen tiap semester dan Cloud Backup untuk mendownload salinan database SQL.

## 🛠️ Stack Teknologi & Spesifikasi Teknis

| Komponen | Teknologi | | :--- | :--- | | Language | Java (JDK 11) | | Networking | Retrofit 2.9.0 & OkHttp | | AI/ML | Google ML Kit Face Detection & FaceNet TFLite | | Location | Google Play Services Location (Fused Location) | | UI/UX | Material Design 3, CardView, Lottie Animation | | Backend | PHP 7.4 (RESTful API) | | Database | MySQL (Cloud) & SQLite (Local) | | Reporting | Spreadsheet Logic (HTML to XLS Stream) |

## 🗄️ Skema Database Utama (MySQL)

<img width="1914" height="414" alt="image" src="https://github.com/user-attachments/assets/1b9f33ad-5ad8-4d5f-aeb6-ed37270be217" />


• Table users: ``` id, nama, email, password, embedding (TEXT), role (INT) ```

• Table tb_absensi: ``` id, user_id, tanggal, jam, status, lat, lng ```

• Table settings: ``` id, radius, jam_masuk, broadcast_msg ```

## 📝 Kesimpulan Validasi (Core Logic)

## Aplikasi ini menerapkan standar keamanan "Anti-Cheating":

1. Anti-Foto: Model AI dilatih untuk membedakan wajah asli dan replika.

2. Anti-Fake GPS: Penggunaan Fused Location Provider mempersulit penggunaan aplikasi manipulasi koordinat.

3. Device Integrity: Sinkronisasi Cloud menjamin data tidak dapat dimanipulasi melalui clear cache atau pembersihan data lokal oleh user.


# 👤 Developer

Fajar Fawwaz Atallah Mahasiswa Teknik Informatika - Universitas Pelita Bangsa
