# Tugas Mandiri 5 — Membandingkan SQL Mentah dan ORM

## A. SQL Mentah

### 1. Penulisan Operasi Menggunakan SQL Mentah

**Pertanyaan / Langkah:**  
Bagaimana cara menulis operasi mengambil satu data berdasarkan ID menggunakan SQL secara langsung (*raw SQL*)?

**Langkah-langkah:**
1. Menggunakan koneksi database relasional (misalnya melalui library `mysql2` pada Node.js).
2. Menuliskan perintah SQL secara manual dengan parameter placeholder (`?`).
3. Menjalankan query ke database.

**Contoh Kode SQL Mentah:**
```sql
SELECT * 
FROM jadwal 
WHERE id = ?;
```

---

## B. ORM

### 1. Penulisan Operasi Menggunakan ORM (Prisma)

**Pertanyaan / Langkah:**  
Bagaimana cara menulis operasi yang sama menggunakan ORM (seperti Prisma)?

**Langkah-langkah:**
1. Mendefinisikan model tabel `jadwal` pada skema Prisma.
2. Memanggil fungsi bawaan Prisma client untuk mencari data unik berdasarkan ID.

**Contoh Kode ORM:**
```javascript
const jadwal = await prisma.jadwal.findUnique({
  where: {
    id: 1
  }
});
```

---

## C. Pertanyaan Analisis dan Perbandingan

### 1. Apa perbedaan cara penulisan operasi database menggunakan SQL secara langsung dan ORM?

* **SQL Mentah:** Ditulis menggunakan kueri basis data relasional standar secara langsung, seperti perintah `SELECT`, `FROM`, dan `WHERE`.
* **ORM:** Ditulis menggunakan pendekatan pemrograman berorientasi objek dalam bahasa pemrograman tingkat tinggi di mana tabel database direpresentasikan sebagai model objek (method/fungsi).

### 2. Apa kelebihan SQL Mentah?

* Memberikan kontrol penuh kepada pengembang untuk mengoptimalkan dan menyesuaikan kueri yang kompleks secara manual.
* Cenderung memiliki performa langsung yang efisien karena tidak melalui lapisan abstraksi tambahan.

### 3. Apa kelebihan ORM?

* Penulisan kode lebih bersih, intuitif, dan mudah dibaca.
* Dilengkapi fitur keamanan bawaan (seperti parameterisasi otomatis) untuk mencegah *SQL Injection*.
* Memudahkan pengelolaan migrasi basis data dan relasi antar tabel secara otomatis.

### 4. Apa yang dimaksud dengan SQL injection, dan apa dampaknya terhadap data aplikasi?

* **SQL Injection:** Celah keamanan di mana penyerang dapat menyisipkan atau memanipulasi perintah SQL melalui masukan input data pengguna yang tidak disaring dengan benar.
* **Dampaknya:** Kebocoran data sensitif, perusakan data, hilangnya integritas basis data, hingga pengambilalihan sistem aplikasi.

### 5. Mengapa penggunaan parameter query dapat mengurangi risiko SQL injection?

* Karena parameter *query* memisahkan secara tegas antara struktur kueri SQL dengan data masukan pengguna, sehingga input dari pengguna akan diperlakukan murni sebagai data nilai, bukan sebagai bagian dari perintah eksekusi SQL.

### 6. Bagaimana ORM membantu pengembang mengakses database? Kaitkan jawaban Anda dengan contoh kode yang telah Anda tulis.

* ORM menyediakan fungsi abstraksi tingkat tinggi (seperti `prisma.jadwal.findUnique`) sehingga pengembang tidak perlu menulis sintaks SQL manual. Berdasarkan contoh kode, pengembang cukup memanggil method objek JavaScript dengan parameter terstruktur (`where: { id: 1 }`), dan ORM secara otomatis akan menerjemahkannya ke dalam kueri database yang aman.