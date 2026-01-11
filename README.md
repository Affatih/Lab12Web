# Laporan Praktikum 12: Autentikasi User & Manajemen Session

## 1. Tujuan Praktikum
Mengamankan aplikasi dengan membatasi hak akses halaman hanya untuk pengguna yang telah terautentikasi (login) dan mengelola status pengguna menggunakan Session.

## 2. Implementasi Session
Aplikasi menggunakan fungsi bawaan PHP `session_start()` yang diletakkan pada bagian paling atas file `index.php`. Hal ini memastikan status login dapat diperiksa di setiap perpindahan halaman (routing).

## 3. Kontrol Akses (Security Gate)
Pada file utama (`index.php`), terdapat logika pengecekan session. Jika pengguna mencoba mengakses halaman dashboard tanpa login, sistem akan otomatis mengalihkan (redirect) pengguna kembali ke halaman login.

**Cuplikan Kode Logika Keamanan:**
```php
session_start();
if (!isset($_SESSION['isLogin'])) {
    header("Location: login.php");
    exit();
}
```

## 4. Alur Autentikasi
**Login**: Memverifikasi username dan password. Jika cocok, data user disimpan ke dalam $_SESSION.
**Persistence**: Selama session aktif, user bebas mengakses modul aplikasi.
**Logout**: Menghapus seluruh data session menggunakan session_destroy(), sehingga akses tertutup kembali.

## 5. Implementasi (Screenshot)
A. Halaman Login
<img width="1366" height="768" alt="Screenshot at 2026-01-11 04-36-21" src="https://github.com/user-attachments/assets/7ef2a5d8-1765-425e-80fb-7120db80da22" />


B. Proteksi Akses (Redirect)
