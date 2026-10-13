# BAB 11 - Episode 71: Delete - Project CRUD

## Apa yang Dipelajari

- Mengimplementasikan operasi **Delete** (menghapus data) pada database file teks
- Strategi hapus: **copy ke file temporary**, lalu **rename** file temporary jadi file utama
- Menggunakan **`os.rename()`** untuk mengganti nama file
- Membaca file baris per baris dengan **`file.readline()`** dalam loop
- Konfirmasi hapus agar user tidak salah menghapus data
- **Proyek CRUD lengkap**: semua operasi (CRUD) sudah terimplementasi

---

## Penjelasan Kode

### File: `CRUD/__init__.py`

```python
from .Database import init_console
from .View import read_console, create_console, update_console, delete_console
```

- Semua fungsi utama sudah di-export: `init_console`, `read_console`, `create_console`, `update_console`, **`delete_console`**.
- CRUD sudah **lengkap**!

---

### File: `CRUD/Operasi.py` — Fungsi `delete(no_buku)`

```python
def delete(no_buku):
    try:
        with open(Database.DB_NAME, 'r') as file:
            counter = 0

            while(True):
                content = file.readline()
                if len(content) == 0:
                    break
                elif counter == no_buku - 1:
                    pass              # ← BARIS INI DIHAPUS (skip)
                else:
                    with open("data_temp.txt", 'a', encoding="utf-8") as temp_file:
                        temp_file.write(content)
                counter += 1
    except:
        print("database error")
    
    os.rename("data_temp.txt", Database.DB_NAME)
```

**Penjelasan algoritma hapus:**

```
Baca data.txt baris per baris:
  Baris 0 (counter=0): ✓ copy ke data_temp.txt
  Baris 1 (counter=1): ✗ SKIP (ini yang dihapus)
  Baris 2 (counter=2): ✓ copy ke data_temp.txt
  ...dst

Setelah selesai:
  Rename data_temp.txt → data.txt (ganti file utama)
```

**Kenapa tidak langsung hapus dari file asli?**

Karena Python **tidak bisa menghapus satu baris** dari file teks secara langsung. Strateginya:

| Langkah | Penjelasan |
|---|---|
| 1. Baca file asli | Baris per baris dengan `readline()` |
| 2. Tulis ke file temporary | Semua baris **kecuali** yang dihapus |
| 3. Rename file temporary | Menjadi file utama → file lama tergantikan |

> Ini seperti menyalin daftar hadir ke kertas baru **tanpa nama** yang akan dihapus, lalu mengganti daftar hadir lama dengan yang baru.

---

### Detail Loop `delete()`

```python
counter = 0
while(True):
    content = file.readline()          # Baca satu baris
    if len(content) == 0:              # Kalau baris kosong = sudah habis
        break
    elif counter == no_buku - 1:       # Kalau ini baris yang mau dihapus
        pass                           # Lewati (jangan ditulis)
    else:                              # Baris lain
        with open("data_temp.txt", 'a') as temp_file:
            temp_file.write(content)   # Salin ke file temporary
    counter += 1
```

| `counter` | `content` | Aksi |
|---|---|---|
| 0 | Baris 1 | ✅ Copy ke `data_temp.txt` |
| 1 | Baris 2 | ❌ **Skip** (dihapus) |
| 2 | Baris 3 | ✅ Copy ke `data_temp.txt` |

```python
os.rename("data_temp.txt", Database.DB_NAME)
```

- `os.rename()` **mengganti nama** file `data_temp.txt` menjadi `data.txt`.
- File `data.txt` lama **otomatis tertimpa**.
- File temporary (`data_temp.txt`) **hilang** karena sudah berganti nama.

---

### File: `CRUD/View.py` — Fungsi `delete_console()`

```python
def delete_console():
    read_console()          # Tampilkan semua data
    while(True):
        print("Silahkan pilih nomor buku yang akan di delete")
        no_buku = int(input("Nomor Buku: "))
        data_buku = Operasi.read(index=no_buku)

        if data_buku:
            data_break = data_buku.split(',')
            pk = data_break[0]
            data_add = data_break[1]
            penulis = data_break[2]
            judul = data_break[3]
            tahun = data_break[4][:-1]

            print("\n" + "="*100)
            print("Data yang ingin anda Hapus")
            print(f"1. Judul\t: {judul:.40}")
            print(f"2. Penulis\t: {penulis:.40}")
            print(f"3. Tahun\t: {tahun:4}")
            is_done = input("Apakah anda yakin (y/n)? ")
            if is_done == "y" or is_done == "Y":
                Operasi.delete(no_buku)
                break
        else:
            print("nomor tidak valid, silahkan masukan lagi")

    print("Data berhasil di hapus")
```

**Alur `delete_console()`:**

```
1. Tampilkan semua data
2. Minta nomor buku yang ingin dihapus
3. Baca data buku tersebut
4. Tampilkan data yang akan dihapus
5. Konfirmasi: "Apakah anda yakin?"
   - "n" → batal
   - "y" → hapus data
6. Panggil Operasi.delete()
7. Tampilkan "Data berhasil dihapus"
```

---

### Perbandingan Fungsi `delete()` vs `update()`

| Aspek | `delete()` | `update()` |
|---|---|---|
| Strategi | Copy ke file temporary, lalu rename | Tulis ulang di posisi dengan `seek()` |
| File temporary | Ya (`data_temp.txt`) | Tidak |
| `os.rename()` | Ya | Tidak |
| `file.seek()` | Tidak | Ya |
| Mode file | `'r'` (baca) + `'a'` (tulis temp) | `'r+'` (baca+tulis) |

---

### File: `main.py` — Final (Semua CRUD Aktif)

```python
match user_option:
    case "1": CRUD.read_console()
    case "2": CRUD.create_console()
    case "3": CRUD.update_console()
    case "4": CRUD.delete_console()    # ← Delete sudah diimplementasi!
```

Semua operasi CRUD sudah aktif dan terhubung ke fungsi-fungsi di package `CRUD`.

---

### Contoh Proses Delete

```
Sebelum hapus:
  1. Python dasar untuk... | Faqihza Mukhlish | 2085
  2. Python dasar untuk... | Faqihza Mukhlish | 2060
  3. Galaxy bima sakti...  | otong            | 1998
  4. Ucup bermain antar... | Joko sujoko      | 1999
  5. Otong bermain di...   | Otong            | 2099

User pilih: hapus nomor 2
Konfirmasi: "Apakah anda yakin? y"

Sesudah hapus:
  1. Python dasar untuk... | Faqihza Mukhlish | 2085
  2. Galaxy bima sakti...  | otong            | 1998
  3. Ucup bermain antar... | Joko sujoko      | 1999
  4. Otong bermain di...   | Otong            | 2099
```

> Data ke-2 (`Python dasar untuk... | Faqihza Mukhlish | 2060`) sudah tidak ada. Data lain otomatis bergeser.

---

### Struktur Lengkap Package CRUD (Episode 71 — Final)

```
CRUD/
├── __init__.py      ← Export: init_console, read_console, create_console,
│                       update_console, delete_console
├── Database.py      ← DB_NAME, TEMPLATE, init_console()
├── Operasi.py       ← create_first_data(), create(), read(), update(), delete()
├── Util.py          ← random_string()
└── View.py          ← read_console(), create_console(), update_console(),
                        delete_console()
```

### Alur Komunikasi Lengkap

```
main.py
  │
  ├── CRUD.init_console()
  │       └── Database.py → Cek/buat database
  │
  ├── CRUD.read_console()
  │       └── View.py → Operasi.read() → Tampilkan tabel
  │
  ├── CRUD.create_console()
  │       └── View.py → Input data → Operasi.create() → Tulis ke file
  │
  ├── CRUD.update_console()
  │       └── View.py → Operasi.read(index) → Input baru → Operasi.update() → Tulis ulang
  │
  └── CRUD.delete_console()
          └── View.py → Operasi.read(index) → Konfirmasi → Operasi.delete() → Copy+Rename
```

---

## Analogi

Bayangkan kamu adalah **petugas perpustakaan** yang harus **mencabut kartu buku** dari lemari:

1. **`delete_console()`** = Kamu memajang semua kartu di meja, lalu pelanggan berkata: "Saya mau hapus kartu nomor 3."
2. **Konfirmasi** = Kamu mengambil kartu ke-3, menunjukkannya ke pelanggan: "Ini kartunya ya, yakin mau dihapus?"
3. **`Operasi.delete()`** = Kamu mengambil **daftar arsip baru** (kertas kosong), lalu menyalin **semua kartu kecuali nomor 3** ke kertas baru.
4. **`os.rename()`** = Kamu mengganti label daftar arsip lama dengan yang baru. Daftar lama dibuang.
5. **Hasilnya** = Daftar arsip sekarang hanya berisi 4 kartu (bukan 5). Kartu nomor 3 sudah hilang permanen.

> Strategi "copy ke temporary, lalu rename" seperti **membuat salinan daftar tanpa item yang dihapus**, lalu mengganti daftar asli. Ini cara paling aman karena kita tidak perlu mengedit file langsung.

---

## Ringkasan CRUD Lengkap (Episode 67-71)

| Operasi | Fungsi | Mode File | Strategi |
|---|---|---|---|
| **C**reate | `Operasi.create()` | `'a'` (append) | Tulis di akhir file |
| **R**ead | `Operasi.read()` | `'r'` (read) | `readlines()` → list |
| **U**pdate | `Operasi.update()` | `'r+'` (read+write) | `seek()` + `write()` → timpa di posisi |
| **D**elete | `Operasi.delete()` | `'r'` + `'a'` + rename | Copy ke temp, skip baris dihapus, rename |

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Hapus data | Strategi copy-rename | Tidak bisa hapus langsung, harus copy ke file temporary |
| `os.rename(a, b)` | Mengganti nama file | File temporary → file utama |
| `file.readline()` | Baca satu baris | Digunakan dalam loop untuk membaca per baris |
| `counter` | Penghitung baris | Melacak posisi baris saat ini |
| `len(content) == 0` | Cek akhir file | `readline()` mengembalikan `""` saat file habis |
| `pass` | Tidak melakukan apa-apa | Melewati baris yang akan dihapus |
| Konfirmasi hapus | `input("y/n")` | Mencegah hapus data secara tidak sengaja |
