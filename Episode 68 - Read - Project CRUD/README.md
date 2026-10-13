# BAB 8 - Episode 68: Read - Project CRUD

## Apa yang Dipelajari

- Mengimplementasikan operasi **Read** (membaca data) pada database file teks
- Membaca file database menggunakan `open()` dan `file.readlines()`
- Memformat data ke dalam **tabel** di terminal
- Menggunakan **delimiter koma** (`,`) untuk memisahkan kolom data
- Konsep **primary key (pk)** sebagai ID unik setiap data
- Template data dengan **padding spasi** agar panjang kolom tetap
- Sistem **inisialisasi database** — membuat data pertama jika file belum ada

---

## Penjelasan Kode

### Struktur Database

Data disimpan dalam file `data.txt` dengan format **teks delimited koma**:

```
pk,date_add,penulis,judul,tahun
```

**Contoh isi `data.txt`:**
```
lJLsFO,2022-10-13-13-45-52+0700,Faqihza Mukhlish,...,Python dasar untuk...,2085
lJLs55,2022-10-13-13-45-52+0700,Faqihza Mukhlish,...,Python dasar untuk...,2060
```

| Kolom | Isi | Contoh |
|---|---|---|
| `pk` | Primary Key (ID unik 6 karakter) | `lJLsFO` |
| `date_add` | Waktu data dibuat | `2022-10-13-13-45-52+0700` |
| `penulis` | Nama penulis buku | `Faqihza Mukhlish` |
| `judul` | Judul buku | `Python dasar untuk...` |
| `tahun` | Tahun terbit | `2085` |

> Setiap kolom **di-padding dengan spasi** agar panjangnya tetap (255 karakter untuk judul/penulis). Ini memudahkan operasi update/replace dengan `seek()`.

---

### File: `CRUD/__init__.py`

```python
from .Database import init_console
from .View import read_console
```

- Meng-import dan **mengeksport** fungsi `init_console` dan `read_console` dari package `CRUD`.
- Ini memungkinkan `main.py` memanggil `CRUD.init_console()` dan `CRUD.read_console()`.

---

### File: `CRUD/Database.py`

```python
from . import Operasi

DB_NAME = "data.txt"
TEMPLATE = {
    "pk": "XXXXXX",
    "date_add": "yyyy-mm-dd",
    "judul": 255 * " ",
    "penulis": 255 * " ",
    "tahun": "yyyy"
}
```

| Variabel | Penjelasan |
|---|---|
| `DB_NAME` | Nama file database: `"data.txt"` |
| `TEMPLATE` | Dictionary yang mendefinisikan **format dan panjang** setiap kolom |
| `"pk": "XXXXXX"` | Primary key = 6 karakter acak |
| `"judul": 255*" "` | Judul di-padding spasi hingga 255 karakter |
| `"penulis": 255*" "` | Penulis di-padding spasi hingga 255 karakter |
| `"tahun": "yyyy"` | Tahun = 4 digit angka |

---

### Fungsi `init_console()`

```python
def init_console():
    try:
        with open(DB_NAME, "r") as file:
            print("Database tersedia, init done!")
    except:
        print("Database tidak ditemukan, silahkan membuat database baru")
        Operasi.create_first_data()
```

**Alur:**
1. Coba buka file `data.txt` untuk dibaca
2. Jika **berhasil** → database sudah ada, tampilkan pesan sukses
3. Jika **gagal** (file tidak ada) → arahkan user untuk membuat data pertama

---

### File: `CRUD/Operasi.py`

```python
from time import time
from . import Database
from .Util import random_string
import time
```

| Import | Penjelasan |
|---|---|
| `from . import Database` | Mengimpor modul Database dari package yang sama |
| `from .Util import random_string` | Mengimpor fungsi random_string dari Util.py |
| `import time` | Module waktu untuk membuat timestamp |

---

### Fungsi `create_first_data()`

```python
def create_first_data():
    penulis = input("Penulis: ")
    judul = input("Judul: ")
    tahun = input("Tahun: ")

    data = Database.TEMPLATE.copy()

    data["pk"] = random_string(6)
    data["date_add"] = time.strftime("%Y-%m-%d-%H-%M-%S%z", time.gmtime())
    data["penulis"] = penulis + Database.TEMPLATE["penulis"][len(penulis):]
    data["judul"] = judul + Database.TEMPLATE["judul"][len(judul):]
    data["tahun"] = tahun

    data_str = f'{data["pk"]},{data["date_add"]},{data["penulis"]},{data["judul"]},{data["tahun"]}\n'
    
    try:
        with open(Database.DB_NAME, 'w', encoding="utf-8") as file:
            file.write(data_str)
    except:
        print("Udah lah Gagal booooos")
```

**Penjelasan per langkah:**

| Langkah | Kode | Penjelasan |
|---|---|---|
| 1. Input data | `input("Penulis: ")` | Minta data dari user |
| 2. Copy template | `Database.TEMPLATE.copy()` | Salin template agar tidak mengubah yang asli |
| 3. Generate ID | `random_string(6)` | Buat ID acak 6 karakter (contoh: `lJLsFO`) |
| 4. Buat timestamp | `time.strftime(...)` | Format waktu: `2022-10-13-13-45-52+0700` |
| 5. Padding | `penulis + TEMPLATE[...][len(penulis):]` | Tambah spasi di akhir sampai 255 karakter |
| 6. Format string | `f'{pk},{date_add},...'` | Gabungkan semua kolom dengan koma |
| 7. Tulis file | `file.write(data_str)` | Tulis ke `data.txt` |

> **Trik padding:** `penulis + TEMPLATE["penulis"][len(penulis):]`
> Jika penulis = `"Ucup"` (4 karakter), maka spasi yang ditambahkan = `TEMPLATE["penulis"][4:]` = 251 spasi. Total = 255 karakter.

---

### Fungsi `read()`

```python
def read():
    try:
        with open(Database.DB_NAME, 'r') as file:
            content = file.readlines()
            return content
    except:
        print("Membaca database error")
        return False
```

- `file.readlines()` membaca **seluruh baris** sebagai **list of string**.
- Setiap elemen list = satu baris data buku.
- Return: list seperti `['lJLsFO,2022-10-13...,Faqihza,...,2085\n', ...]`

---

### File: `CRUD/View.py`

```python
from . import Operasi

def read_console():
    data_file = Operasi.read()
    
    index = "No"
    judul = "Judul"
    penulis = "Penulis"
    tahun = "Tahun"

    # Header
    print("\n" + "="*100)
    print(f"{index:4} | {judul:40} | {penulis:40} | {tahun:5}")
    print("-"*100)
    
    # Data
    for index, data in enumerate(data_file):
        data_break = data.split(",")
        pk = data_break[0]
        date_add = data_break[1]
        penulis = data_break[2]
        judul = data_break[3]
        tahun = data_break[4]
        print(f"{index+1:4} | {judul:.40} | {penulis:.40} | {tahun:4}", end="")

    # Footer
    print("="*100 + "\n")
```

**Penjelasan:**

| Kode | Penjelasan |
|---|---|
| `Operasi.read()` | Ambil semua data dari file |
| `data.split(",")` | Pecah baris berdasarkan koma → list kolom |
| `enumerate(data_file)` | Loop dengan indeks (0, 1, 2, ...) |
| `{judul:.40}` | Tampilkan judul, maks 40 karakter (dipotong jika lebih) |
| `{index+1:4}` | Nomor urut dengan lebar 4 spasi (rata kanan) |

**Output tabel:**
```
====================================================================================================
  No | Judul                                    | Penulis                                 | Tahun
----------------------------------------------------------------------------------------------------
   1 | Python dasar untuk para ucup ucup yang te | Faqihza Mukhlish                        | 2085
   2 | Python dasar untuk para ucup ucup yang te | Faqihza Mukhlish                        | 2060
   3 | abang abangan                            | otong                                   | 1998
====================================================================================================
```

---

### File: `CRUD/Util.py`

```python
import random
import string

def random_string(panjang: int) -> str:
    hasil_string = ''.join(random.choice(string.ascii_letters) for i in range(panjang))
    return hasil_string
```

| Kode | Penjelasan |
|---|---|
| `string.ascii_letters` | Semua huruf: `abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ` |
| `random.choice(...)` | Pilih satu huruf acak dari string |
| `''.join(...)` | Gabungkan semua huruf menjadi satu string |
| `for i in range(panjang)` | Ulangi sebanyak `panjang` karakter |

**Contoh output:** `random_string(6)` → `"lJLsFO"`, `"xKqRzW"`, dll.

---

### File: `main.py`

```python
import os
import CRUD as CRUD

if __name__ == "__main__":
    sistem_operasi = os.name

    # Bersihkan layar
    match sistem_operasi:
        case "posix": os.system("clear")
        case "nt": os.system("cls")

    print("SELAMAT DATANG DI PROGRAM")
    print("DATABASE PERPUSTAKAAN")
    print("=========================")

    # Inisialisasi database
    CRUD.init_console()

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

        match user_option:
            case "1": CRUD.read_console()     # ← Read sudah diimplementasi!
            case "2": print("Create Data")     # ← Belum
            case "3": print("Update Data")     # ← Belum
            case "4": print("Delete Data")     # ← Belum

        is_done = input("Apakah Selesai (y/n)? ")
        if is_done == "y" or is_done == "Y":
            break

    print("Program Berakhir, Terima Kasiih KAKAAAAA")
```

> Pada Episode 68, opsi `"1"` sudah memanggil `CRUD.read_console()`. Sementara opsi lain masih placeholder.

---

### Alur Program Read

```
User pilih "1. Read Data"
        │
        ▼
CRUD.read_console()
        │
        ▼
Operasi.read()
        │
        ▼
Buka data.txt → baca semua baris → return list
        │
        ▼
View.read_console()
        │
        ▼
Format jadi tabel → cetak ke layar
```

---

## Analogi

Bayangkan kamu adalah **petugas perpustakaan**:

1. **`Database.py`** = **Lemari arsip** — punya format baku untuk setiap kartu buku (ID, tanggal, judul, penulis, tahun).

2. **`Operasi.py`** = **Kamu sebagai petugas** — kamu membuka lemari arsip, mengambil semua kartu, dan membawanya ke meja.

3. **`Util.py`** = **Mesin cetak kartu** — membuat nomor kartu acak untuk buku baru.

4. **`View.py`** = **Papan pengumuman** — kamu menempelkan semua kartu buku di papan dengan format rapi supaya orang bisa melihat daftar buku.

5. **`init_console()`** = **Cek lemari arsip** — kalau lemari kosong, kamu minta data buku pertama. Kalau sudah ada, kamu bilang "siap digunakan".

> Membaca data seperti **membuka lemari arsip dan membacakan daftar buku** yang ada di dalamnya.

---

## Ringkasan Konsep Penting

| Konsep | Penjelasan |
|---|---|
| **Database teks** | File `.txt` sebagai penyimpanan data, setiap baris = satu record |
| **Delimiter koma** | Kolom dipisahkan oleh koma (`,`) |
| **Primary Key (pk)** | ID unik 6 karakter untuk setiap record |
| **Padding spasi** | Kolom di-padding agar panjangnya tetap (255 char) |
| **Template** | Dictionary yang mendefinisikan format setiap kolom |
| **`split(",")`** | Memecah string berdasarkan delimiter koma |
| **`readlines()`** | Membaca semua baris file sebagai list |
| **`enumerate()`** | Loop dengan indeks otomatis |
| **`__init__.py`** | File yang mengeksport fungsi dari package |
