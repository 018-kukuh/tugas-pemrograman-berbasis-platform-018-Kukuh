# Tugas Mandiri 5 — Membandingkan Hashing dan Enkripsi serta Menjaga Kunci Rahasia

## 1. Pengujian Hash Kata Sandi

Pengujian dilakukan menggunakan pustaka `bcryptjs` dengan kata sandi `sama` dan faktor biaya (*cost*) sebesar `10`.

Perintah yang digunakan:

```bash
node -e "console.log(require('./backend/node_modules/bcryptjs').hashSync('sama', 10))"
```

### Hasil Pengujian

| **Percobaan** | **Kata sandi masukan** | **Nilai hash**                          |
| :------------ | :--------------------- | :-------------------------------------- |
| Pertama       | `sama`                 | Tempel hasil hash pertama dari terminal |
| Kedua         | `sama`                 | Tempel hasil hash kedua dari terminal   |

### Analisis Hasil

Kedua percobaan menggunakan kata sandi yang sama, tetapi menghasilkan nilai hash yang berbeda karena bcrypt menggunakan salt acak yang berbeda pada setiap proses hashing. Faktor biaya (*cost*) sebesar `10` mengatur tingkat pekerjaan komputasi yang dibutuhkan, sehingga proses hashing memerlukan waktu lebih lama dan membantu memperlambat upaya menebak kata sandi.

## 2. Perbedaan Hashing dan Enkripsi

Hashing mengubah data menjadi nilai hash dan tidak dirancang untuk mengembalikan data asli melalui proses kebalikan. Sebaliknya, enkripsi mengubah data menjadi bentuk yang tidak dapat dibaca secara langsung dan memungkinkan data asli dipulihkan melalui dekripsi menggunakan kunci yang sesuai.

## 3. Alasan Aplikasi Menyimpan Hash Kata Sandi

Aplikasi menyimpan hash kata sandi agar kata sandi asli tidak tersimpan dalam bentuk teks biasa di database. Dengan cara ini, risiko penyalahgunaan kata sandi dapat dikurangi apabila database mengalami kebocoran.

## 4. Cara Kerja bcrypt.compare

Fungsi `bcrypt.compare` memeriksa apakah kata sandi yang dimasukkan pengguna sesuai dengan hash yang tersimpan. Fungsi ini menggunakan informasi salt dan parameter yang terdapat dalam hash untuk melakukan pemeriksaan tanpa perlu menyimpan kata sandi asli.

## 5. Pengertian Rainbow Table dan Fungsi Salt

Rainbow table adalah kumpulan hasil perhitungan hash yang telah dibuat sebelumnya untuk membantu menebak data asli dari nilai hash. Salt membuat hash dari kata sandi yang sama menjadi berbeda, sehingga mengurangi efektivitas penggunaan rainbow table yang telah dihitung sebelumnya.

## 6. Pentingnya Menjaga JWT_SECRET

`JWT_SECRET` merupakan kunci rahasia yang digunakan untuk menandatangani atau memverifikasi JWT pada algoritma berbasis secret. Jika kunci ini bocor, pihak lain dapat berpotensi membuat token palsu yang diterima server, sehingga kunci harus disimpan secara aman dan tidak dimasukkan ke riwayat Git.

## 7. Pemeriksaan Keamanan Repositori

### A. Pemeriksaan berkas .env

Perintah yang dijalankan:

```bash
git ls-files --error-unmatch backend/.env 2>/dev/null && echo "BAHAYA: .env terlacak" || echo "AMAN: .env tidak terlacak"
```

Hasil pemeriksaan:

```text
Tempel hasil yang muncul di terminal di sini.
```

### B. Pemeriksaan token JWT

Perintah yang dijalankan:

```bash
git grep -nE 'eyJ[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+\.[A-Za-z0-9_-]+' -- docs web mobile || echo "AMAN: tidak ada JWT di laporan atau client"
```

Hasil pemeriksaan:

```text
Tempel hasil yang muncul di terminal di sini.
```

### C. Analisis Hasil Pemeriksaan

Hasil pemeriksaan digunakan untuk mengetahui apakah berkas `.env` terlacak oleh Git dan apakah token JWT terdeteksi dalam folder `docs`, `web`, atau `mobile` yang diperiksa. Jika ditemukan berkas atau token yang berisi informasi rahasia, lokasi temuan harus dicatat dan dilakukan penanganan agar rahasia tidak terekspos.

Jika `backend/.env` terlacak, hentikan pelacakannya dengan `git rm --cached backend/.env` dan pastikan berkas tersebut masuk ke `.gitignore`. Jika `JWT_SECRET` sudah terpapar, ganti kunci tersebut dan cabut atau perbarui token yang terdampak sesuai kebutuhan. Menghapus berkas dari versi terbaru saja tidak menghapus rahasia dari riwayat Git.
