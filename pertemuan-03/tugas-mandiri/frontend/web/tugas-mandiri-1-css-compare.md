
# Tugas Mandiri 1 — Membandingkan Dua Pendekatan Penataan Kartu

## 1. Tujuan

Tujuan tugas ini adalah membandingkan pendekatan component-based dan utility-first dalam membuat kartu profil mahasiswa menggunakan HTML dan CSS.

## 2. Hasil Pengerjaan

Saya membuat dua halaman kartu profil mahasiswa dengan konten yang sama, yaitu:

- Nama: Kukuh 
- NIM: 2024520018
- Foto: Foto profil Kukuh
- Tombol: Lihat Profil

Kedua halaman memiliki desain kartu berwarna putih, latar belakang abu-abu, foto berbentuk lingkaran, dan tombol berwarna biru.

Perbedaan kedua halaman terletak pada cara mengatur tampilannya.

### A. Component-Based

File: `tugas-mandiri-1-component.html`

Pada versi ini, saya menulis CSS di dalam tag `<style>`. Saya menggunakan class seperti `.card`, `.profile-photo`, `.profile-name`, `.profile-nim`, dan `.btn`.

Kelebihan pendekatan ini adalah tampilan dapat diatur melalui aturan CSS yang terpusat. Jika ingin mengubah warna semua tombol, saya cukup mengubah aturan `.btn`.

### B. Utility-First

File: `tugas-mandiri-1-utility.html`

Pada versi ini, saya menggunakan Tailwind CSS melalui CDN. Tampilan diatur dengan class utility seperti `p-5`, `rounded-2xl`, `bg-white`, `text-center`, dan `shadow-lg`.

Kelebihan pendekatan ini adalah saya dapat mengatur tampilan langsung pada elemen HTML tanpa menulis aturan CSS sendiri.

## 3. Perbandingan Kedua Pendekatan

| Aspek | Component-Based | Utility-First |
|---|---|---|
| Penulisan tampilan | Menggunakan CSS dalam tag `<style>` | Menggunakan class utility Tailwind |
| Jumlah baris CSS | Sekitar 70 baris CSS, termasuk aturan responsif | Tidak ada CSS buatan sendiri |
| Jumlah class utility | Tidak menggunakan class utility Tailwind | Sekitar 30–35 kemunculan class utility |
| Waktu pengerjaan | Memerlukan waktu untuk menulis aturan CSS | Dapat lebih cepat setelah memahami class Tailwind |
| Mengubah tema | Mengubah aturan CSS pada class komponen | Mengganti class warna, ukuran, dan tampilan |
| Penggunaan ulang | Class komponen dapat digunakan pada banyak elemen | Kombinasi class utility dapat digunakan kembali |
| Ketergantungan | Tidak membutuhkan framework CSS | Membutuhkan Tailwind CSS |

Catatan: Jumlah baris CSS dan class utility perlu disesuaikan dengan kode akhir yang benar-benar digunakan. Jumlah class utility dihitung berdasarkan kemunculan class pada atribut `class`, bukan jumlah jenis class yang berbeda.

## 4. Pengujian Responsif

Saya menguji kedua halaman pada tampilan laptop dan layar dengan lebar 360 piksel.

Hasil yang diharapkan:

1. Kartu tampil di tengah halaman.
2. Foto, nama, NIM, dan tombol dapat terlihat dengan jelas.
3. Kartu menyesuaikan lebar layar.
4. Tidak muncul gulir horizontal pada lebar layar 360 piksel.

## 5. Perbandingan Waktu Pengerjaan dan Perubahan Tema

Dalam percobaan ini, pendekatan utility-first dapat mempercepat penataan awal karena saya tidak perlu menulis aturan CSS satu per satu. Namun, saya perlu memahami nama dan fungsi class Tailwind.

Pendekatan component-based memerlukan penulisan CSS tersendiri. Meskipun demikian, perubahan tema dapat dilakukan dengan mudah melalui aturan CSS yang digunakan bersama oleh beberapa komponen.

## 6. Pilihan Pendekatan untuk Proyek Akhir

Untuk halaman yang memiliki banyak komponen dengan desain yang sama, seperti halaman dashboard, profil, dan daftar data, saya memilih component-based karena aturan tampilannya dapat digunakan kembali dan dikelola secara terpusat.

Untuk halaman yang memerlukan pengembangan tampilan dengan cepat, seperti halaman sederhana atau prototipe, saya memilih utility-first karena pengaturan tampilan dapat dilakukan langsung melalui class pada HTML.

Pemilihan pendekatan tetap disesuaikan dengan kebutuhan, ukuran proyek, dan konsistensi desain.

## 7. Kesimpulan

Component-based dan utility-first memiliki kelebihan masing-masing. Component-based memudahkan pengelolaan aturan CSS yang digunakan bersama, sedangkan utility-first memudahkan penataan tampilan secara langsung melalui class utility.

Kedua pendekatan dapat menghasilkan kartu profil yang responsif apabila struktur HTML dan pengaturan lebarnya dibuat dengan benar.