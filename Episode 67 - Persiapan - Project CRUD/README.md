# BAB 7 - Episode 67: Persiapan - Project CRUD

## Apa yang Dipelajari

- Memahami konsep **CRUD** (Create, Read, Update, Delete)
- Membuat **struktur project** dengan package Python
- Menggunakan **`os` module** untuk interaksi dengan sistem operasi
- Membersihkan layar terminal secara **cross-platform** (Windows/Linux/Mac)
- Membuat **menu interaktif** dengan `while True` dan `match-case`
- Konsep modularitas: memisahkan kode ke dalam **folder/package CRUD**

---

## Penjelasan Kode

### Apa itu CRUD?

**CRUD** adalah 4 operasi dasar pada data:

| Huruf | Fungsi | Bahasa Indonesia | Contoh |
|---|---|---|---|
| **C** | Create | Menambah data | Menambah buku baru |
| **R** | Read | Membaca data | Melihat daftar buku |
| **U** | Update | Mengubah data | Mengubah judul buku |
| **D** | Delete | Menghapus data | Menghapus buku dari daftar |

> Proyek CRUD ini adalah **database perpustakaan sederhana** yang menyimpan data buku dalam file teks.

---

### File: `main.py`

### 1. Import Module

```python
import os
import CRUD as CRUD
```

| Import | Penjelasan |
|---|---|
| `os` | Module bawaan Python untuk interaksi sistem operasi (bersihkan layar, cek OS) |
| `CRUD as CRUD` | Mengimpor package `CRUD` — folder yang berisi modul-modul CRUD |

---

### 2. Blok `__main__`

```python
if __name__ == "__main__":
    sistem_operasi = os.name
```

- `os.name` mendeteksi sistem operasi:
  - `"posix"` → Linux / macOS
  - `"nt"` → Windows
- Variabel `sistem_operasi` digunakan untuk menentukan perintah bersihkan layar yang sesuai.

---

### 3. Membersihkan Layar Terminal

```python
    match sistem_operasi:
        case "posix": os.system("clear")
        case "nt": os.system("cls")
```

| OS | Perintah | Fungsi |
|---|---|---|
| Linux/Mac (`posix`) | `os.system("clear")` | Membersihkan layar terminal |
| Windows (`nt`) | `os.system("cls")` | Membersihkan layar terminal |

> **`os.system()`** menjalankan perintah shell operasi sistem.

---

### 4. Menu Utama dengan Loop

```python
    while(True):
        match sistem_operasi:
            case "posix": os.system("clear")
            case "nt": os.system("cls")
        
        print("SELAMAT DATANG DI PROGRAM")
        print("DATABASE PERPUSTAKAAN")
        print("=========================")

        print(f"1. Read Data")
        print(f"2. Create Data")
        print(f"3. Update Data")
        print(f"4. Delete Data\n")

        user_option = input("Masukan opsi: ")

        print("\n=========================\n")

        match user_option:
            case "1": print("Read Data")
            case "2": print("Create Data")
            case "3": print("Update Data")
            case "4": print("Delete Data")

        print("\n=========================\n")
        is_done = input("Apakah Selesai (y/n)? ")
        if is_done == "y" or is_done == "Y":
            break

    print("Program Berakhir, Terima Kasiih KAKAAAAA")
```

**Alur program:**

```
1. Bersihkan layar
2. Tampilkan menu
3. Minta input opsi dari user
4. Jalankan aksi sesuai opsi
5. Tanya "Apakah selesai?"
   - Jika "y" → keluar dari loop → program selesai
   - Jika "n" → ulangi dari langkah 1
```

**Saat episode ini, setiap opsi masih mencetak teks biasa:**
```
case "1": print("Read Data")      # Belum diimplementasi
case "2": print("Create Data")    # Belum diimplementasi
case "3": print("Update Data")    # Belum diimplementasi
case "4": print("Delete Data")    # Belum diimplementasi
```

Di episode selanjutnya (68-71), print ini akan diganti dengan **panggilan fungsi CRUD**.

---

### Struktur Folder Project

```
Episode 67/
├── main.py              ← File utama (program entry point)
└── CRUD/                ← Package CRUD
    └── __init__.py      ← File kosong (penanda package)
```

**Kenapa harus ada subfolder `CRUD/`?**

Karena di episode selanjutnya, folder `CRUD/` akan diisi dengan modul-modul:

```
CRUD/
├── __init__.py      ← Meng-export fungsi-fungsi utama
├── Database.py      ← Konfigurasi database (nama file, template data)
├── Operasi.py       ← Fungsi-fungsi operasi data (CRUD)
├── Util.py          ← Fungsi utilitas (generate ID random, dll)
└── View.py          ← Tampilan ke user (format tabel, input console)
```

> Ini adalah **pola desain modular**: memisahkan kode berdasarkan tanggung jawabnya masing-masing.

---

### Alur Komunikasi antar Module

```
main.py
  │
  ├── import CRUD  →  CRUD/__init__.py
  │                    │
  │                    ├── import Database.py  →  Konfigurasi
  │                    ├── import Operasi.py   →  Operasi data
  │                    ├── import Util.py      →  Utilitas
  │                    └── import View.py      →  Tampilan
  │
  └── CRUD.init_console()     →  (Episode 68)
      CRUD.read_console()     →  (Episode 68)
      CRUD.create_console()   →  (Episode 69)
      CRUD.update_console()   →  (Episode 70)
      CRUD.delete_console()   →  (Episode 71)
```

---

## Analogi

Bayangkan kamu sedang **membangun sebuah toko**:

1. **`main.py`** = **Pintu masuk toko** — di sinilah pelanggan pertama kali datang dan memilih layanan.

2. **`CRUD/`** = **Ruang belakang toko** — berisi ruang-ruang khusus:
   - `Database.py` = **Lemari arsip** — tempat format data disimpan
   - `Operasi.py` = **Petugas toko** — yang melakukan operasi (ambil, tambah, ubah, hapus data)
   - `Util.py` = **Mesin tik** — alat bantu untuk generate kode unik
   - `View.py` = **Display etalase** — cara data ditampilkan ke pelanggan

3. **`__init__.py`** = **Pintu penghubung** antara ruang depan dan ruang belakang.

Di Episode 67 ini, toko baru **selesai dibangun strukturnya** — belum ada barang yang dijual. Di episode selanjutnya, kita akan mulai **mengisi dan mengoperasikan** toko ini.

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| CRUD | Create, Read, Update, Delete | 4 operasi dasar data |
| `os.name` | `"nt"` atau `"posix"` | Mendeteksi sistem operasi |
| `os.system()` | `os.system("cls")` | Menjalankan perintah shell |
| Package | Folder dengan `__init__.py` | Kumpulan module Python |
| `match-case` | Python 3.10+ pattern matching | Pernyataan kondisional |
| Loop | `while(True):` | Perulangan tak terbatas sampai `break` |
| Modularitas | Pemisahan kode ke modul | Mempermudah maintenance |
