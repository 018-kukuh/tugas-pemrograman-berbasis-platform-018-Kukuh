# Tugas Mandiri 4 — Menganalisis Struktur dan Validitas JWT

## 1. Tujuan

Tujuan tugas ini adalah memahami struktur JSON Web Token (JWT), mengenali klaim yang terdapat dalam payload, dan menguji validitas tanda tangan token ketika payload diubah.

## 2. Analisis Klaim JWT

JWT digunakan untuk membawa informasi atau klaim yang dapat diperiksa oleh server. Pada proyek Aplikasi Pengaduan dan Monitoring Permasalahan Kampus Berbasis Mobile, JWT dapat digunakan untuk mengenali pengguna dan menentukan perannya.

| **Klaim** | **Fungsi**                                                                                           |
| :-------- | :--------------------------------------------------------------------------------------------------- |
| `sub`     | Menunjukkan identitas atau ID pengguna dalam token.                                                  |
| `nim`     | Menunjukkan Nomor Induk Mahasiswa jika klaim ini tersedia dalam payload.                             |
| `role`    | Menunjukkan peran pengguna, misalnya `MAHASISWA`, `DOSEN`, atau `FAKULTAS`, jika digunakan oleh API. |
| `iat`     | Menunjukkan waktu penerbitan token dalam format Unix timestamp.                                      |
| `exp`     | Menunjukkan waktu kedaluwarsa token dalam format Unix timestamp.                                     |

Klaim yang benar-benar digunakan harus disesuaikan dengan payload JWT hasil login dari API praktikum.

## 3. Perbedaan Klaim iat dan exp

Klaim `iat` (*issued at*) menunjukkan waktu ketika token diterbitkan oleh server. Sementara itu, klaim `exp` (*expiration time*) menunjukkan waktu ketika token tidak lagi berlaku. Selisih waktu antara kedua klaim dapat digunakan untuk mengetahui masa berlaku token.

## 4. Pengujian Token JWT

Pengujian dilakukan menggunakan endpoint `GET /auth/me` dengan token asli dan token yang payload-nya telah diubah tanpa memperbarui tanda tangan.

| **Token yang diuji**             | **Endpoint**   | **Hasil yang diharapkan** | **Hasil pengujian**          |
| :------------------------------- | :------------- | :------------------------ | :--------------------------- |
| Token asli yang masih berlaku    | `GET /auth/me` | `200 OK`                  | [Isi sesuai hasil pengujian] |
| Token dengan payload yang diubah | `GET /auth/me` | `401 Unauthorized`        | [Isi sesuai hasil pengujian] |

### Analisis Hasil Pengujian

Token asli yang masih berlaku diharapkan memperoleh respons `200 OK` karena tanda tangan token valid dan token belum kedaluwarsa.

Token yang payload-nya diubah tanpa memperbarui tanda tangan diharapkan memperoleh respons `401 Unauthorized`. Hal ini terjadi karena tanda tangan JWT digunakan untuk mendeteksi perubahan pada isi token, sehingga perubahan payload membuat tanda tangan tidak lagi cocok dengan hasil verifikasi server.

## 5. Dokumentasi Pengujian

Lampirkan tangkapan layar berikut:

1. Payload JWT di jwt.io dengan token lengkap disamarkan.
2. Hasil permintaan `GET /auth/me` menggunakan token asli.
3. Hasil permintaan `GET /auth/me` menggunakan token yang telah diubah.

Token JWT lengkap tidak boleh ditampilkan dalam laporan.
