
# Tugas Mandiri 2 — Menyusun Tata Letak dengan Class Utility

## 1. Tujuan

Tugas ini bertujuan untuk memahami penggunaan class utility Tailwind CSS dalam menyusun halaman web yang responsif. Halaman yang dibuat terdiri dari navbar, hero, tiga kartu konten, dan footer.

## 2. Hasil Pengerjaan

Saya membuat halaman Profil Mahasiswa menggunakan Tailwind CSS melalui CDN. Halaman memiliki empat bagian utama, yaitu:

1. Navbar yang berisi judul halaman dan tautan navigasi.
2. Hero yang berisi judul pembuka, deskripsi, dan tombol.
3. Tiga kartu konten yang terdiri dari Biodata, Jadwal Kuliah, dan Kegiatan.
4. Footer yang berisi nama halaman dan tahun pembuatan.

## 3. Class Utility dan Fungsinya

### A. Navbar

Class utama yang digunakan:

- `flex`: mengatur elemen dalam tata letak fleksibel.
- `flex-col`: menyusun elemen secara vertikal.
- `sm:flex-row`: menyusun elemen secara horizontal mulai ukuran layar sm.
- `gap-3`: memberikan jarak antar-elemen.
- `px-4 py-4`: memberikan ruang di dalam elemen.
- `hover:text-yellow-300`: mengubah warna teks ketika kursor berada di atas tautan.

### B. Hero

Class utama yang digunakan:

- `grid`: menggunakan tata letak grid.
- `grid-cols-1`: menyusun konten menjadi satu kolom.
- `md:grid-cols-2`: mengubah tata letak menjadi dua kolom pada layar md ke atas.
- `items-center`: menyelaraskan elemen secara vertikal.
- `gap-6`: memberikan jarak antar-elemen.
- `text-3xl`: mengatur ukuran teks judul.
- `font-bold`: membuat teks menjadi tebal.

### C. Tiga Kartu Konten

Class utama yang digunakan:

- `grid`: mengatur kartu menggunakan grid.
- `grid-cols-1`: menyusun kartu dalam satu kolom.
- `md:grid-cols-3`: mengubah susunan menjadi tiga kolom pada layar md ke atas.
- `gap-6`: memberikan jarak antar-kartu.
- `rounded-xl`: membuat sudut kartu membulat.
- `bg-white`: memberikan latar belakang putih.
- `p-6`: memberikan ruang di dalam kartu.
- `shadow-md`: memberikan bayangan pada kartu.
- `hover:-translate-y-1`: mengangkat kartu sedikit ketika kursor berada di atasnya.
- `hover:shadow-xl`: memperbesar bayangan saat kursor berada di atas kartu.

### D. Footer

Class utama yang digunakan:

- `bg-slate-800`: memberikan latar belakang abu-abu gelap.
- `px-4 py-6`: mengatur ruang di dalam footer.
- `text-center`: membuat teks rata tengah.
- `text-white`: memberikan warna putih pada teks.
- `text-slate-300`: memberikan warna abu-abu terang pada teks tambahan.

## 4. Pengujian Responsif

Saya menguji halaman pada tampilan laptop dan lebar layar 360 piksel.

Hasil yang diharapkan:

1. Pada layar laptop, hero tersusun dalam dua kolom dan tiga kartu ditampilkan dalam tiga kolom.
2. Pada layar 360 piksel, hero dan kartu tersusun dalam satu kolom.
3. Navbar tetap dapat dibaca dan tautannya tidak keluar dari layar.
4. Efek hover bekerja ketika kursor berada di atas tautan, tombol, atau kartu.
5. Tidak terdapat gulir horizontal pada layar 360 piksel.

## 5. Bagian yang Mudah dan Sulit Disusun

Bagian yang lebih mudah disusun menggunakan class utility adalah kumpulan kartu karena saya dapat menggunakan `grid grid-cols-1 gap-6 md:grid-cols-3` untuk mengatur jumlah kolom dan jarak antarkartu. Perubahan tata letak dapat dilakukan langsung melalui class HTML. Namun, susunan class menjadi lebih sulit dibaca ketika satu elemen memiliki banyak class untuk mengatur ukuran, warna, jarak, responsivitas, dan efek hover sekaligus.

## 6. Kesimpulan

Tailwind CSS memudahkan saya menyusun halaman web responsif tanpa menulis CSS sendiri. Class seperti `grid-cols-1`, `md:grid-cols-3`, `gap-6`, dan `hover:shadow-xl` memiliki fungsi yang berbeda dalam mengatur tata letak, jarak, dan interaksi. Dengan memahami fungsi class utility, halaman dapat disesuaikan dengan ukuran layar dan kebutuhan desain.