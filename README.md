# Perbedaan MySQL dan MySQLi

**Tugas:** Jelaskan perbedaan antara MySQL dan MySQLi!

## Penjelasan

**MySQL** adalah sistem manajemen basis data (database server) tempat data disimpan dan dikelola, misalnya database `perpustakaan` dengan tabel `anggota`. MySQL bekerja di sisi server dan tidak bergantung pada bahasa pemrograman tertentu.

**MySQLi** (MySQL Improved) adalah ekstensi PHP yang dipakai untuk **menghubungkan** program PHP dengan database MySQL. Jadi MySQLi bukan database, melainkan "jembatan" antara PHP dan MySQL.

Dalam dunia PHP, istilah "MySQL" juga sering dipakai untuk menyebut ekstensi lama `mysql_*` (misalnya `mysql_connect()`). Ekstensi lama ini sudah usang dan dihapus sejak PHP 7, lalu digantikan oleh MySQLi.

## Tabel Perbandingan

| Aspek | MySQL | MySQLi |
|---|---|---|
| Jenis | Sistem database (server) | Ekstensi PHP untuk mengakses MySQL |
| Fungsi | Menyimpan dan mengelola data | Menghubungkan PHP dengan database MySQL |
| Contoh | Database, tabel, query SQL | `mysqli_connect()`, `mysqli_query()` |
| Gaya penulisan | - | Prosedural dan berorientasi objek (OOP) |
| Prepared statement | - | Didukung (lebih aman dari SQL Injection) |
| Status | Aktif dan terus dikembangkan | Dipakai dan didukung di PHP modern |
| Ekstensi lama `mysql_*` | Sudah dihapus sejak PHP 7 | Penggantinya |

## Contoh Kode

Ekstensi lama (tidak boleh dipakai lagi):

```php
<?php
$koneksi = mysql_connect("localhost", "root", "");
mysql_select_db("perpustakaan");
?>
```

Ekstensi MySQLi:

```php
<?php
$koneksi = mysqli_connect("localhost", "root", "", "perpustakaan");

if (!$koneksi) {
    die("Koneksi gagal: " . mysqli_connect_error());
}

$hasil = mysqli_query($koneksi, "SELECT * FROM anggota");
while ($baris = mysqli_fetch_assoc($hasil)) {
    echo $baris['nama'] . "<br>";
}
?>
```

## Kesimpulan

MySQL adalah databasenya, sedangkan MySQLi adalah alat di PHP untuk mengakses database tersebut. MySQLi lebih baik daripada ekstensi `mysql_*` lama karena lebih aman (mendukung prepared statement), mendukung gaya OOP, dan masih didukung oleh PHP versi terbaru.
