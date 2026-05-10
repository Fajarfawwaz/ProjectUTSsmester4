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

# 1. Modul Mahasiswa (User Interface)

# - Halaman Login & Recovery:

# LOGIN, REGISTER, FORGOT PASSWORD : 

<img width="220" alt="image" src="https://github.com/user-attachments/assets/6eaaffbb-2989-4040-8421-de88a9383aee" />
<img width="220" alt="image" src="https://github.com/user-attachments/assets/bb072d3d-7845-4599-980d-79e0f0179527" />
<img width="220" alt="image" src="https://github.com/user-attachments/assets/98358d4b-11e7-49e4-a809-d14f1a4c11e7" />

## ◦ Mendukung autentikasi ganda (Lokal & Cloud).

## ◦ Fitur Identity Recovery: Jika user pindah perangkat atau re-install aplikasi, sistem secara otomatis menarik kembali nama, role, dan data wajah (embedding) dari Cloud ke SQLite lokal.

# - Halaman Dashboard Utama:

<img width="250" alt="image" src="https://github.com/user-attachments/assets/6c85796b-ff35-4a29-926f-2bb58e604c41" />

## ◦ Statistik Dinamis: Menampilkan total hadir, telat, dan izin yang disinkronkan langsung dari server AwardSpace.

## ◦ Real-time Greeting: Ucapan selamat berdasarkan waktu sistem (Pagi/Siang/Malam).

## ◦ Profile Preview: Menampilkan foto profil yang diambil saat pendaftaran wajah.

# - Halaman Registrasi Wajah (Biometric Enrollment):

<img width="250" alt="image" src="https://github.com/user-attachments/assets/bb3142f2-06b3-493c-b93b-8c44187cc484" />

## ◦ Menggunakan Google ML Kit untuk mendeteksi wajah dan FaceNet Model untuk mengonversi citra wajah menjadi 192 titik koordinat angka (embeddings).

## ◦ Data ini di-upload ke Cloud untuk keamanan identitas permanen.

# - Halaman Absensi (Scanning & Geofencing):

<img width="250" alt="image" src="https://github.com/user-attachments/assets/13509c91-17c0-4c33-9749-47c17a21994e" />

## ◦ Validasi Lokasi: Memeriksa jarak user dengan koordinat Kampus UPB. Jika jarak > 150 meter, akses scan wajah ditutup (mencegah manipulasi lokasi).

## ◦ Biometric Verification: Mencocokkan wajah saat ini dengan data pendaftaran menggunakan algoritma Cosine Similarity.

# - Halaman Riwayat (Attendance History):

<img width="250" alt="image" src="https://github.com/user-attachments/assets/ae48e7d5-5b64-432d-971b-d035204abb9a" />

## ◦ Menampilkan list kronologis kehadiran user yang diambil dari basis data lokal (SQLite).

# - Halaman Pengajuan Izin (Digital Leave Request) :

<img width="250" alt="image" src="https://github.com/user-attachments/assets/a28fc16b-5d01-4e1d-861d-48a76a1eae20" />

## Halaman ini berfungsi sebagai sistem administrasi jika mahasiswa berhalangan hadir (Sakit, Izin, atau Cuti).

## • Formulir Digital: Input jenis izin (Sakit/Izin/Cuti), alasan keterangan tertulis, dan pemilihan tanggal.

## • Lampiran Bukti (Camera Integration): Mahasiswa diwajibkan melampirkan foto bukti (misalnya: Surat Keterangan Dokter) yang diambil langsung melalui kamera sebagai validasi.

## • Data Persistence:
   
   ### ◦ Lokal: Data disimpan ke tabel pengajuan_izin di SQLite.
   
   ### ◦ Cloud: Secara otomatis mengirimkan notifikasi status ke database AwardSpace sehingga Admin dapat melihat alasan ketidakhadiran di tabel rekapitulasi secara real-time.

## • Business Logic: Pengajuan izin otomatis mengisi kolom status pada riwayat absensi sehingga persentase kehadiran tetap terhitung secara administratif.

# - Halaman Profil & Manajemen Identitas (Identity Module) :

<img width="250" alt="image" src="https://github.com/user-attachments/assets/b7b4131a-2c81-4dfd-86eb-b16c9d3dc351" />

Halaman ini adalah pusat pengaturan data pribadi dan verifikasi keamanan perangkat user.

## • Visual Identity: Menampilkan foto profil mahasiswa yang diambil saat pendaftaran biometrik pertama kali (Face Enrollment).

## • Informasi Personal: Menampilkan detail data yang tersimpan di server:
   
   ### ◦ Nama Lengkap & Email Akun.
   
   ### ◦ Nomor Telepon & Alamat.
   
   ### ◦ Tanggal Lahir.
   
   ### ◦ Role User: Menandakan status akun (Mahasiswa/Admin).

## • Security Info (Device Integrity): 
   
   ### ◦ Face Registry Status: Menampilkan indikator apakah data wajah sudah tersinkronisasi dengan server Cloud.
   
   ### ◦ Device ID Binding: Menampilkan ID unik perangkat untuk memastikan akun tidak disalahgunakan di banyak perangkat berbeda.
   
## • Edit Profile: Fitur untuk memperbarui data nomor telepon dan alamat secara dinamis yang langsung memperbarui database SQLite lokal dan MySQL Cloud.

# 2. Modul Administrator (Admin Control Panel)

# - Admin Dashboard:

<img width="250" alt="image" src="https://github.com/user-attachments/assets/bde0ba62-d459-4954-9f2a-b646faaa9ba5" />

## ◦ Global Stats: Menampilkan ringkasan kehadiran seluruh mahasiswa hari ini secara visual.

## ◦ Digital Clock Real-time: Menunjukkan waktu server yang akurat.

## ◦ Recent Activity Log: Menampilkan 5 aktivitas absensi terbaru dari seluruh mahasiswa untuk pengawasan instan.

# - Halaman Monitoring Kehadiran (Rekapitulasi) dan Untuk Mendownload Detail Mahasiswa :

<img width="250" alt="image" src="https://github.com/user-attachments/assets/ca162704-934a-49c7-bcdd-2036ad2e8732" />
<img width="250" alt="image" src="https://github.com/user-attachments/assets/2914a62a-7598-43ee-b793-fbaff787c1ed" />


## ◦ Daftar seluruh mahasiswa beserta total performa kehadiran (Hadir, Telat, Izin).

## ◦ Klik pada nama mahasiswa akan membuka halaman Detail Individu.

# - Halaman Daftar Mahasiswa (User Management):

<img width="250" alt="image" src="https://github.com/user-attachments/assets/5e9275b4-612e-48a1-aec5-280a7eadf375" />

## ◦ Tampilan format Tabel Zebra (selang-seling warna) untuk kenyamanan membaca data.

## ◦ Real-time Search: Fitur pencarian instan berdasarkan nama atau email tanpa perlu memuat ulang halaman.

# - Halaman Detail & Export:

<img width="250" alt="image" src="https://github.com/user-attachments/assets/4d007e37-b5b5-4884-a10f-d006cb2afaf3" />

## ◦ Ringkasan profil mahasiswa.

## ◦ Export to Excel (.xls): Menghasilkan laporan kehadiran individu yang siap cetak untuk keperluan administratif.

# - Halaman Kontrol Sistem (The "Obeng" Feature):

<img width="250" alt="image" src="https://github.com/user-attachments/assets/5aefafe5-3f48-424e-b5fe-9e04d95cbddd" />

## ◦ Dynamic Configuration: Admin dapat mengubah radius absensi (misal 150m ke 200m) dan jam masuk secara remote tanpa coding ulang.

## ◦ Maintenance Tools: Tombol Reset Data untuk mengosongkan riwayat absen tiap semester dan Cloud Backup untuk mendownload salinan database SQL.

# 🛠️ Stack Teknologi & Spesifikasi Teknis

| Komponen | Teknologi | | :--- | :--- | | Language | Java (JDK 11) | | Networking | Retrofit 2.9.0 & OkHttp | | AI/ML | Google ML Kit Face Detection & FaceNet TFLite | | Location | Google Play Services Location (Fused Location) | | UI/UX | Material Design 3, CardView, Lottie Animation | | Backend | PHP 7.4 (RESTful API) | | Database | MySQL (Cloud) & SQLite (Local) | | Reporting | Spreadsheet Logic (HTML to XLS Stream) |

# 🗄️ Skema Database Utama (MySQL)

<img width="1914" height="414" alt="image" src="https://github.com/user-attachments/assets/1b9f33ad-5ad8-4d5f-aeb6-ed37270be217" />

## • Table users: ``` id, nama, email, password, embedding (TEXT), role (INT) ```

## • Table tb_absensi: ``` id, user_id, tanggal, jam, status, lat, lng ```

## • Table settings: ``` id, radius, jam_masuk, broadcast_msg ```

# 📝 Kesimpulan Validasi (Core Logic)

# Aplikasi ini menerapkan standar keamanan "Anti-Cheating":

## 1. Anti-Foto: Model AI dilatih untuk membedakan wajah asli dan replika.

## 2. Anti-Fake GPS: Penggunaan Fused Location Provider mempersulit penggunaan aplikasi manipulasi koordinat.

## 3. Device Integrity: Sinkronisasi Cloud menjamin data tidak dapat dimanipulasi melalui clear cache atau pembersihan data lokal oleh user.


## Di bawah ini adalah Link Folder Android Studio Project Saya, dan link download aplikasi ( jika ingin mencoba ) : 

### Link Folder Android Studio : https://drive.google.com/file/d/1cDR3nn-R3_LMhvkLk3ytWINYQP-ZEl9u/view?usp=sharing

### Link Download Aplikasi Saya : https://drive.google.com/file/d/1U1XOHtmTXr0z_YSWPCpnxTi_UPGqL4yF/view?usp=sharing 

# 👤 Developer

Fajar Fawwaz Atallah Mahasiswa Teknik Informatika - Universitas Pelita Bangsa
