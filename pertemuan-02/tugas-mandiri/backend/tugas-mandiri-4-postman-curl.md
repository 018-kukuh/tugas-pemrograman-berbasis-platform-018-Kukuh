# Tugas Mandiri 4 — Pengujian API dengan Postman dan curl

## A. Menggunakan Postman

### 1. Pengujian Metode GET (`https://httpbin.org/get`)

**Pertanyaan / Langkah:**  
Bagaimana cara melakukan pengujian metode GET pada `https://httpbin.org/get` di Postman dan bagaimana hasil responsnya?

**Langkah-langkah:**
1. Membuat request baru di aplikasi Postman.
2. Memilih metode `GET`.
3. Memasukkan URL `https://httpbin.org/get`.
4. Mengklik tombol **Send**.

**Hasil Respons:**  
Server mengembalikan data berformat JSON yang merinci informasi permintaan klien, termasuk metadata `headers`, parameter URL, serta alamat IP pengirim (`origin`).

---

### 2. Pengujian Metode POST dengan JSON (`https://httpbin.org/post`)

**Pertanyaan / Langkah:**  
Bagaimana cara melakukan pengujian metode POST dengan data JSON pada `https://httpbin.org/post` di Postman?

**Langkah-langkah:**
1. Membuat request baru di Postman.
2. Memilih metode `POST`.
3. Memasukkan URL `https://httpbin.org/post`.
4. Membuka tab **Body**.
5. Memilih opsi **raw** dengan tipe **JSON**.
6. Memasukkan data berikut:

```json
{
  "nama": "Umar",
  "kelas": "Informatika"
}
```

---

## B. Menggunakan curl

### 1. Pengujian Metode GET dengan `curl -i`

**Pertanyaan / Langkah:**  
Bagaimana cara melakukan pengujian metode GET menggunakan `curl` dan melihat status serta header respons?

**Langkah-langkah:**
1. Membuka Command Prompt (CMD) atau terminal.
2. Menjalankan perintah berikut:

```bash
curl -i https://httpbin.org/get
```

---

## C. Membandingkan `curl -s` dan `curl -i`

### 1. Pengujian Menggunakan `curl -s`

**Pertanyaan / Langkah:**  
Bagaimana hasil pengujian menggunakan opsi `-s` dan apa fungsi opsi tersebut?

**Langkah-langkah:**
1. Membuka Command Prompt (CMD) atau terminal.
2. Menjalankan perintah berikut:

```bash
curl -s https://httpbin.org/get
```

---

### 2. Perbandingan `curl -s` dan `curl -i`

**Pertanyaan 1: Apa perbedaan hasil kedua perintah tersebut?**

Perintah `curl -s` menampilkan isi respons dari server tanpa menampilkan progress meter, sedangkan `curl -i` menampilkan header HTTP terlebih dahulu kemudian diikuti isi respons.

**Pertanyaan 2: Apa fungsi opsi `-s`?**

Opsi `-s` (*silent*) berfungsi menyembunyikan progress meter dan pesan tambahan sehingga output yang ditampilkan lebih sederhana.

**Pertanyaan 3: Apa fungsi opsi `-i`?**

Opsi `-i` berfungsi menampilkan header HTTP dari respons server, seperti kode status HTTP, `Content-Type`, dan `Content-Length`, sebelum menampilkan isi respons.

**Pertanyaan 4: Kapan Anda menggunakan masing-masing opsi?**

Opsi `-s` digunakan ketika ingin melihat isi respons secara bersih, sedangkan opsi `-i` digunakan ketika ingin memeriksa status dan informasi header dari respons HTTP.
