# BAB 1 - If dan Else Statement

## Apa yang Dipelajari

- Perintah `if` untuk mengecek kondisi
- Perintah `else` sebagai alternatif jika kondisi tidak terpenuhi
- Penggunaan indentasi (spasi/tab) dalam blok kode
- Cara mendapatkan input dari pengguna dengan `input()`
- Perbandingan nilai dengan operator `==`

---

## Penjelasan Kode

### Membaca Input Pengguna

```python
nama = input("Siapa nama anda? ")
```

| Komponen | Penjelasan |
|---|---|
| `nama` | Variabel untuk menyimpan nama yang diketik pengguna |
| `input()` | Fungsi yang menampilkan pesan dan menunggu pengguna mengetik sesuatu |
| `"Siapa nama anda? "` | Pesan yang ditampilkan ke pengguna saat meminta input |

Setelah baris ini dijalankan, variabel `nama` akan berisi teks apa pun yang diketik pengguna.

---

### If Statement

```python
if nama=="otong":
	print("hai otooong, si keren!!!")
```

| Komponen | Penjelasan |
|---|---|
| `if` | Kata kunci untuk memulai percabangan kondisi |
| `nama=="otong"` | Kondisi yang dicek: apakah isi variabel `nama` sama dengan `"otong"`? |
| `:` | Tanda titik dua menandakan akhir dari baris kondisi |
| `print(...)` | Aksi yang dijalankan jika kondisi **True** (benar) |
| **Indentasi** | Baris di bawah `if` harus ditulis lebih kecil (pakai tab/spasi) |

> **Penting:** Dalam Python, indentasi bukan sekadar格式. Indentasi **wajib** untuk menandakan blok kode yang dijalankan bersama. Tanpa indentasi, Python akan error.

---

### Else Statement

```python
else:
	print("Ah kamu bukan otong, kamu gak keren! :(")
```

| Komponen | Penjelasan |
|---|---|
| `else` | Alternatif yang dijalankan jika kondisi `if` **False** (salah) |
| `:` | Tanda titik dua menandakan awal blok `else` |
| `print(...)` | Aksi yang dijalankan jika kondisi tidak terpenuhi |

---

### Menjalankan Kode di Luar Blok

```python
print("akhir dari program")
```

Baris ini **selalu dijalankan** tidak peduli kondisi `if` atau `else` yang terpenuhi, karena ia berada **di luar** blok indentasi.

---

## Alur Program

```
Program diminta input nama
        |
        v
Apakah nama == "otong"?
   /            \
  YES            NO
   |              |
cetak            cetak
"hai otooong"   "Ah kamu bukan otong"
   \            /
    v          v
 cetak "akhir dari program"
```

---

## Analogi

Bayangkan kamu sedang di depan pintu gerbang sekolah:

- **If**: "JIKA kamu bernama Otong, maka kamu boleh masuk pintu VIP."
- **Else**: "JIKA bukan, kamu harus lewat pintu biasa."

Setelah itu, semua orang (baik Otong maupun bukan) tetap masuk ke halaman sekolah (perintah `print("akhir dari program")`).

---

## Tips Penting

1. **Indentasi**: Gunakan **1 tab** atau **4 spasi** secara konsisten. Jangan campur!
2. **Operator perbandingan**: Gunakan `==` untuk membandingkan nilai (bukan `=` yang artinya menetapkan nilai).
3. **Case-sensitive**: `"Otong"` dan `"otong"` dianggap **berbeda** oleh Python.
