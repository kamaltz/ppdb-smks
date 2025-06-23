# Aplikasi PPDB-SMKS

Aplikasi ini dirancang untuk mengelola proses Penerimaan Peserta Didik Baru (PPDB) untuk Sekolah Menengah Kejuruan (SMK). Aplikasi ini menyediakan fungsionalitas untuk mengelola gelombang pendaftaran, data pendaftar, dan informasi umum.

## Fitur

-   **Gelombang Pendaftaran (Gelombang)**: Membuat dan mengelola berbagai tahapan atau gelombang penerimaan siswa (misalnya, Gelombang 1, Gelombang 2), termasuk statusnya (dibuka/ditutup).
-   **Manajemen Pendaftar (Pendaftar)**: Mendaftar dan melacak calon siswa, mencatat detail seperti sekolah asal.
-   **Manajemen Informasi (Informasi)**: Mempublikasikan dan mengkategorikan informasi serta pengumuman penting terkait proses PPDB.
-   **Kategori**: Mengelompokkan berbagai informasi atau data ke dalam kategori yang berbeda.
-   **Panel Admin**: Antarmuka terpusat bagi administrator untuk mengelola semua aspek sistem PPDB, termasuk pengguna, gelombang, pendaftar, dan informasi.

## Panduan Instalasi (menggunakan Laragon)

Laragon adalah lingkungan pengembangan universal yang portabel, terisolasi, cepat & kuat untuk PHP, Node.js, Python, Java, Go, Ruby. Sangat cocok untuk menyiapkan lingkungan pengembangan lokal dengan cepat.

### Prasyarat

Sebelum memulai, pastikan Anda telah menginstal yang berikut ini:

-   **Laragon**: Unduh dan instal Laragon dari [https://laragon.org/](https://laragon.org/). Pastikan untuk menyertakan Apache/Nginx, MySQL, dan PHP selama instalasi.
-   **Composer**: Manajer dependensi PHP. Laragon biasanya sudah menyertakannya, tetapi Anda dapat memverifikasi atau menginstalnya dari [https://getcomposer.org/](https://getcomposer.org/).
-   **Git**: Untuk mengkloning repositori. Unduh dari [https://git-scm.com/](https://git-scm.com/).

### Langkah-langkah

1.  **Kloning Repositori**:
    Buka Git Bash atau command prompt Anda dan navigasikan ke direktori `www` Laragon Anda (misalnya, `C:\laragon\www`). Kemudian, kloning proyek:

    ```bash
    git clone <repository_url> ppdb-smks
    ```

    (Ganti `<repository_url>` dengan URL repositori Git Anda yang sebenarnya.)

2.  **Masuk ke Direktori Proyek**:

    ```bash
    cd ppdb-smks
    ```

3.  **Instal Dependensi PHP**:
    Instal semua paket PHP yang diperlukan menggunakan Composer:

    ```bash
    composer install
    ```

4.  **Konfigurasi Variabel Lingkungan**:
    Salin file contoh lingkungan dan buat kunci aplikasi:

    ```bash
    cp .env.example .env
    php artisan key:generate
    ```

5.  **Konfigurasi Database**:
    Buka file `.env` yang baru dibuat di editor teks. Konfigurasikan detail koneksi database Anda. Jika Anda menggunakan MySQL bawaan Laragon, pengaturan ini mungkin sudah berfungsi:

    ```dotenv
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=ppdb_smks # Anda mungkin perlu membuat database ini di MySQL
    DB_USERNAME=root
    DB_PASSWORD=
    ```

6.  **Jalankan Migrasi dan Seeder**:
    Perintah ini akan membuat tabel database yang diperlukan dan mengisinya dengan data awal, termasuk pengguna admin.

    ```bash
    php artisan migrate --seed
    ```

7.  **Pengaturan Virtual Host Laragon**:

    -   Buka Laragon.
    -   Buka `Menu > Apache > Sites enabled > Add new site`.
    -   Masukkan `ppdb-smks.test` sebagai nama situs dan arahkan path ke `C:\laragon\www\ppdb-smks\public` (atau di mana pun proyek Anda berada).
    -   Sebagai alternatif, Laragon sering kali membuat host virtual secara otomatis. Cukup klik kanan pada ikon tray Laragon, buka `www`, dan pilih `ppdb-smks`.
    -   Mulai ulang semua layanan Laragon (`Menu > Restart All`).

8.  **Akses Aplikasi**:
    Buka browser web Anda dan kunjungi `http://ppdb-smks.test`.

## Kredensial Login Admin

Anda dapat masuk ke panel administrasi menggunakan kredensial berikut:

-   **Email**: `admin@smk.com`
-   **Kata Sandi**: `123456`

---

Selamat menggunakan aplikasi PPDB-SMKS!
