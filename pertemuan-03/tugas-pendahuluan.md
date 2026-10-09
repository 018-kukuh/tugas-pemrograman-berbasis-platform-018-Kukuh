# Tugas Pendahuluan

## Soal 1 — Bandingkan Bootstrap dan Tailwind CSS

### Class Utama Pembuatan Kartu dan Tombol

**Bootstrap** menggunakan class komponen seperti `card`, `card-body`, dan `btn btn-primary`.

Sedangkan **Tailwind CSS** menggunakan pendekatan *utility-first* dengan class seperti `max-w-sm`, `rounded`, `overflow-hidden`, `shadow-lg`, dan `p-6` untuk kartu.

Untuk tombol, Tailwind CSS menggunakan class seperti `bg-blue-500`, `text-white`, `font-bold`, `py-2`, `px-4`, dan `rounded`.

### Pendekatan yang Lebih Mudah bagi Pemula

Menurut saya, **Bootstrap lebih mudah digunakan oleh pemula** karena menyediakan komponen siap pakai tanpa harus merangkai banyak *utility class* satu per satu dari awal.

## Soal 2 — Perbandingan Struktur HTML

### Versi Komponen (Bootstrap)

```html
<div class="card" style="width: 18rem;">
  <img src="foto.jpg" class="card-img-top" alt="Foto">
  <div class="card-body">
    <h5 class="card-title">Kukuh Dwi Nur Cahyo</h5>
    <p class="card-text">NIM: 2026001</p>
    <a href="#" class="btn btn-primary">Detail</a>
  </div>
</div>
```

### Versi Utility (Tailwind CSS)

```html
<div class="max-w-xs rounded overflow-hidden shadow-lg bg-white p-4">
  <img class="w-full" src="foto.jpg" alt="Foto">
  <div class="px-6 py-4">
    <div class="font-bold text-xl mb-2">Kukuh Dwi Nur Cahyo</div>
    <p class="text-gray-700 text-base">NIM: 2026001</p>
    <button class="bg-blue-500 text-white font-bold py-2 px-4 rounded">
      Detail
    </button>
  </div>
</div>
```

### Jumlah Aturan CSS / Class Utility

Versi komponen menggunakan struktur class bawaan yang lebih ringkas, sekitar **6 class utama**.

Versi utility membutuhkan sekitar **12 class utility** yang ditulis langsung pada elemen HTML.

### Kemudahan Mengubah Warna

Versi utility lebih mudah diubah warnanya secara spesifik langsung pada elemen tanpa perlu menimpa file CSS terpisah.

## Soal 3 — Amati Isi Token

### Jumlah Bagian Token

Token JWT terdiri dari **3 bagian** yang dipisahkan oleh tanda titik (`.`), yaitu:

1. **Header**
2. **Payload**
3. **Signature**

### Nama Data pada Payload

Data yang terlihat di dalam payload meliputi:

- `sub` (Subject): `1234567890`
- `name`: `John Doe`
- `iat` (Issued At): `1516239022`

### Alasan Password Tidak Boleh Disimpan dalam Payload

Password tidak boleh disimpan dalam payload JWT karena payload menggunakan enkoding Base64 dan **tidak dienkripsi**.

Isi payload dapat dibaca oleh pihak yang mendapatkan token. Menyimpan password di dalam payload sangat berbahaya karena dapat menyebabkan kebocoran data atau *credential leakage*.

## Soal 4 — Analogi Gerbang Kampus

### Contoh Authentication dan Authorization

Pemeriksaan kartu identitas atau **KTM** di gerbang utama kampus untuk memastikan identitas seseorang merupakan contoh **authentication**.

Sedangkan pemeriksaan izin ketika seseorang ingin masuk ke ruang server laboratorium khusus merupakan contoh **authorization**.

### Kondisi Berhasil Identitas tetapi Ditolak Masuk

Seorang mahasiswa tingkat pertama berhasil menunjukkan kartu identitas kampus yang sah sehingga **authentication berhasil**.

Namun, mahasiswa tersebut tetap tidak memiliki izin masuk ke ruang server karena ruangan tersebut hanya dikhususkan bagi staf administrator jaringan. Dalam kondisi ini, **authorization gagal**.

## Soal 5 — Peran di Aplikasi Nyata

### Contoh Aplikasi: SIAKAD UNIRA

1. **Mahasiswa:**  
   Memiliki fitur khusus untuk mengisi Kartu Rencana Studi (KRS).

2. **Dosen:**  
   Memiliki fitur khusus untuk menginput nilai mahasiswa.

3. **Administrator:**  
   Memiliki fitur khusus untuk mengelola data akun pengguna kampus.

### Respons untuk Dua Keadaan

#### Pengguna Belum Login

Server mengembalikan respons:

```text
HTTP 401 Unauthorized
```

Status **401 Unauthorized** menunjukkan bahwa pengguna belum melakukan autentikasi atau belum dikenali oleh sistem.

#### Pengguna Sudah Login tetapi Tidak Memiliki Izin

Server mengembalikan respons:

```text
HTTP 403 Forbidden
```

Status **403 Forbidden** menunjukkan bahwa identitas pengguna sudah dikenali, tetapi pengguna tidak memiliki hak akses yang mencukupi.

### Alasan Penggunaan Status 401 atau 403

Status **401** digunakan agar klien mengetahui bahwa pengguna harus melakukan autentikasi atau login terlebih dahulu.

Sedangkan status **403** digunakan untuk menunjukkan bahwa identitas pengguna sudah valid, tetapi hak akses pengguna terhadap sumber daya tersebut tidak mencukupi.
