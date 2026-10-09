# Tugas Mandiri 3 — Menganalisis Authentication dan Authorization

## 1. Peran Pengguna

Pada proyek Aplikasi Pengaduan dan Monitoring Permasalahan Kampus Berbasis Mobile, terdapat tiga peran pengguna, yaitu:

1. **Mahasiswa:** Membuat pengaduan permasalahan kampus, melihat pengaduan miliknya, dan memantau status pengaduan.
2. **Dosen:** Melihat pengaduan yang berkaitan dengan kegiatan akademik dan memberikan tanggapan terhadap pengaduan sesuai kewenangannya.
3. **Fakultas:** Memverifikasi pengaduan, memperbarui status penanganan, dan melihat laporan serta statistik pengaduan.

## 2. Matriks Hak Akses

| **Fitur**                       | **Mahasiswa** | **Dosen** | **Fakultas** | **Endpoint**                    |
| :------------------------------ | :-----------: | :-------: | :----------: | :------------------------------ |
| Membuat pengaduan               |       ✅       |     ❌     |       ❌      | `POST /pengaduan`               |
| Melihat pengaduan milik sendiri |       ✅       |     ❌     |       ❌      | `GET /pengaduan/saya`           |
| Melihat daftar pengaduan        |       ❌       |     ✅     |       ✅      | `GET /pengaduan`                |
| Melihat detail pengaduan        |       ✅*      |     ✅     |       ✅      | `GET /pengaduan/:id`            |
| Memberikan tanggapan pengaduan  |       ❌       |     ✅     |       ✅      | `POST /pengaduan/:id/tanggapan` |
| Memperbarui status pengaduan    |       ❌       |     ❌     |       ✅      | `PATCH /pengaduan/:id/status`   |
| Melihat statistik pengaduan     |       ❌       |     ✅     |       ✅      | `GET /monitoring/statistik`     |
| Membuat laporan rekap pengaduan |       ❌       |     ❌     |       ✅      | `POST /laporan`                 |

Keterangan:

* ✅ = Diizinkan mengakses fitur.
* ❌ = Ditolak dengan kode `403` jika pengguna sudah terautentikasi, tetapi tidak memiliki izin.
* ✅* = Mahasiswa hanya boleh melihat detail pengaduan miliknya sendiri.
* Endpoint di atas merupakan rancangan untuk proyek kelompok.

## 3. Perbedaan Kode 401 dan 403

Kode `401 Unauthorized` digunakan ketika pengguna mengakses endpoint yang dilindungi tanpa token autentikasi atau menggunakan token yang tidak valid. Contohnya, mahasiswa mengirim permintaan ke `POST /pengaduan` tanpa token, sehingga sistem menolak permintaan karena identitas pengguna belum dapat diverifikasi.

Kode `403 Forbidden` digunakan ketika pengguna memiliki token yang valid, tetapi tidak memiliki hak akses untuk menggunakan fitur tertentu. Contohnya, mahasiswa mencoba mengakses `PATCH /pengaduan/:id/status`, padahal fitur tersebut hanya dapat digunakan oleh Fakultas. Sistem menolak permintaan tersebut dengan kode `403`.

## 4. Contoh Analisis Authentication dan Authorization

Pada aplikasi pengaduan kampus, seorang mahasiswa berhasil login menggunakan akun miliknya. Ketika mahasiswa tersebut mencoba mengubah status pengaduan, sistem menolak permintaan karena fitur tersebut hanya tersedia bagi Fakultas.

| **Keadaan**                                                                      | **Pemeriksaan**                                | **Hasil yang diharapkan pada endpoint terlindungi** |
| :------------------------------------------------------------------------------- | :--------------------------------------------- | :-------------------------------------------------- |
| Mahasiswa tidak menyertakan token saat mengirim pengaduan                        | Identitas belum terverifikasi                  | `401`                                               |
| Mahasiswa menyertakan token valid dan mengakses fitur melihat pengaduan miliknya | Identitas valid dan hak akses sesuai           | Permintaan diizinkan                                |
| Mahasiswa menyertakan token valid dan mencoba mengubah status pengaduan          | Identitas valid, tetapi hak akses tidak sesuai | `403`                                               |

## 5. Risiko Jika Endpoint Hanya Menggunakan requireAuth

Jika endpoint `PATCH /pengaduan/:id/status` hanya menggunakan `requireAuth`, sistem hanya memastikan bahwa pengguna sudah login tanpa memeriksa perannya. Mahasiswa yang sudah login berpotensi mengubah status pengaduan jika tidak ada pemeriksaan hak akses tambahan. Oleh karena itu, endpoint tersebut perlu menggunakan `requireAuth` dan `requireRole` agar hanya Fakultas yang dapat memperbarui status pengaduan.

