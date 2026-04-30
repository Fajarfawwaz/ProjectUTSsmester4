# Absensi Fajar 📱 (Pelita Bangsa Edition)

Sistem Absensi Biometrik & Geofencing Berbasis Android Native

## IDENTITAS MAHASISWA :

## Nama : Fajar Fawwaz Atallah 

## Kelas : I241D

## NIM : 312410357

## MATKUL : PEMROGRAMAN MOBILE 

SAYA MEMBUAT TUGAS INI UNTUK MENGERJAKAN TUGAS UTS PEMROGRAMAN MOBILE SEMESTER 4

## 📝 Deskripsi Proyek

Absensi Fajar adalah solusi manajemen kehadiran cerdas yang dirancang khusus untuk meningkatkan integritas data di lingkungan kampus atau perkantoran. Aplikasi ini berfokus pada fitur Anti-Fraud (Anti-Kecurangan) dengan menggabungkan dua validasi utama secara bersamaan: Verifikasi Wajah (AI) dan Penguncian Lokasi (GPS).

Versi ini dikonfigurasi khusus untuk Universitas Pelita Bangsa (UPB) Cikarang, di mana absensi hanya dapat dilakukan jika pengguna berada dalam radius 150 meter dari koordinat gedung utama kampus.

## ✨ Fitur Unggulan

•🛡️ Face AI Recognition: Menggunakan model FaceNet (TensorFlow Lite) untuk mencocokkan wajah secara real-time dengan akurasi tinggi.

•📍 Smart Geofencing: Validasi koordinat GPS menggunakan FusedLocationProvider. Memblokir akses absensi jika pengguna berada di luar radius Universitas Pelita Bangsa.

•📊 Premium Analytics Dashboard: Tampilan ringkasan statistik (Hadir, Terlambat, Izin) yang dihitung otomatis dari database lokal secara real-time.

•🕒 Intelligent Attendance Logic: Penentuan status otomatis berdasarkan waktu (Hadir jika < 09:00, Terlambat jika > 09:00).

•📇 Executive Profile: Manajemen identitas digital lengkap dengan fitur ganti foto profil dan Smart Calendar (DatePicker).

•☁️ Web Service Sync: Sinkronisasi data otomatis dari database lokal (SQLite) ke server cloud (MySQL) melalui Retrofit API.


## 🛠️ Tech Stack

| Komponen | Teknologi | | --- | --- | | Bahasa Pemrograman | Java (Android Native) | | Database HP / Server | SQLite & MySQL via XAMPP | | Artificial Intelligence | TensorFlow Lite & Google ML Kit (FaceNet) | | Networking / API | Retrofit 2 & GSON | | Location Services | Google Play Services (FusedLocationProvider) | | UI Framework | Material Design 3, CardView, Gradient Drawables |

## 📸 Penjelasan Modul & Antarmuka Aplikasi

<img width="1018" height="788" alt="Screenshot 2026-04-30 132424" src="https://github.com/user-attachments/assets/5ca0c39c-f0db-4363-a70c-e70efe45b460" />


Berdasarkan alur kerja aplikasi, berikut adalah fungsi dari setiap halaman utama:

1.Splash Screen: Layar pemuatan awal yang melakukan inisialisasi model AI dan pengecekan koneksi server.

2.Login Screen: Akses masuk menggunakan email dan password dengan desain Card Overlay yang mewah.

3.Register Screen: Pendaftaran pengguna baru yang menyinkronkan data secara otomatis ke database lokal dan server.

4.Forgot Password: Fitur pemulihan kata sandi mandiri melalui validasi email terdaftar.

5.Face Enrollment: Proses pendaftaran identitas biometrik wajah pengguna ke dalam sistem database.

6.Smart Dashboard: Pusat navigasi yang menampilkan jam realtime, statistik kehadiran, dan status radius GPS kampus.

7.Attendance Scanner: Mesin inti absensi. Menjalankan Geofencing Check terlebih dahulu sebelum mengaktifkan pemindaian wajah.

8.Success Screen: Umpan balik visual berupa animasi centang hijau saat absensi berhasil diverifikasi.

9.Attendance History: Daftar rekapitulasi kehadiran lengkap dengan jam masuk, keluar, dan status otomatis.

10.Permission Form: Formulir pengajuan izin/sakit yang dilengkapi dengan fitur unggah foto dokumen pendukung.

11.Executive Profile: Halaman identitas diri yang elegan, menampilkan status keanggotaan dan detail biodata pengguna.

12.Edit Profile: Halaman untuk memperbarui data diri, mengubah foto profil, dan memilih tanggal lahir melalui kalender.


## ⚙️ Cara Instalasi & Konfigurasi

### 1. Persiapan Server (XAMPP)

•Pastikan Apache dan MySQL aktif.

•Buat database db_absensi di phpMyAdmin.

•Import struktur tabel yang tersedia dalam folder database_sql.

•Letakkan folder API (PHP) ke dalam direktori C:/xampp/htdocs/absensi_api.


### 2. Persiapan Android Studio•Clone repositori ini ke direktori lokal Anda.

•Buka file com.example.absensifajar.utils.ApiClient.

•Ganti BASE_URL dengan IP Address laptop Anda (Gunakan perintah ipconfig di CMD).

•Pastikan HP Android dan Laptop terhubung dalam jaringan Wi-Fi yang sama.


### 3. Konfigurasi Radius Geofence

Koordinat default disetel pada gedung Universitas Pelita Bangsa:

•Latitude: -6.3245

•Longitude: 107.1687

•Radius: 150 Meter


## 📞 Kontak & Pengembang

Jika Anda menemukan kendala teknis atau ingin berdiskusi mengenai pengembangan aplikasi ini, silakan hubungi:

•Nama: Fajar Fawwaz Atallah

•WhatsApp: +62 858-2397-3618

•Email: Fajarfawwaz64@gmail.com

•Universitas: Universitas Pelita Bangsa, Cikarang, Indonesia.
