# BAB 15 - Membuat Module

## Apa yang Dipelajari

- **Module**: file `.py` yang berisi fungsi/fariabel yang bisa di-import ke file lain
- Cara membuat module sendiri (cukup buat file `.py`)
- Tiga cara import module: `import`, `from ... import`, dan `import ... as`
- Fungsi **`*args`** dan **lambda** di dalam module
- Konsep **currying** di module matematika

---

## Penjelasan Kode

### File Utama: `matematika.py` (Module yang Dibuat)

```python
# module matematika

def tambah(*args):
    hasil = 0
    for data in args:
        hasil += data
    return hasil

def kali(*args):
    hasil = 1
    for data in args:
        hasil *= data
    return hasil

def pangkat(n:int):
    return lambda angka:angka**n
```

#### Fungsi `tambah(*args)`
- Menerima **banyak angka** sebagai tuple (via `*args`).
- Menjumlahkan semua angka dari 0.
- Contoh: `tambah(1,2,3,4,5)` → `0+1+2+3+4+5 = 15`

#### Fungsi `kali(*args)`
- Menerima **banyak angka** sebagai tuple.
- Mengalikan semua angka dari 1.
- Contoh: `kali(1,2,3,4,5)` → `1×1×2×3×4×5 = 120`

#### Fungsi `pangkat(n)` (Currying)
- Membuat **fungsi pangkat** dari angka tertentu.
- `pangkat(3)` mengembalikan `lambda angka:angka**3` → fungsi pangkat tiga.
- Bisa dipanggil langsung: `pangkat(3)(5)` → `5**3 = 125`

---

### File 1: `main_app.py` — Import dengan `import` Biasa

```python
import matematika

hasil_tambah = matematika.tambah(1,2,3,4,5)
print(f"hasil tambah = {hasil_tambah}")

hasil_kali = matematika.kali(1,2,3,4,5)
print(f"hasil tambah = {hasil_kali}")

pangkat_3 = matematika.pangkat(3)
print(f"hasil pangkat3 = {pangkat_3(3)}")
```

- `import matematika` → import seluruh modul.
- Akses fungsi pakai `matematika.nama_fungsi()`.
- `pangkat_3 = matematika.pangkat(3)` → menyimpan fungsi pangkat 3 ke variabel.
- `pangkat_3(3)` → `3**3 = 27`
- Output:
  ```
  hasil tambah = 15
  hasil tambah = 120
  hasil pangkat3 = 27
  ```

---

### File 2: `main_from.py` — Import dengan `from ... import`

```python
from matematika import tambah,kali,pangkat

hasil_tambah = tambah(1,2,3,4,5)
print(f"hasil tambah = {hasil_tambah}")

hasil_kali = kali(1,2,3,4,5)
print(f"hasil tambah = {hasil_kali}")

pangkat_3 = pangkat(3)
print(f"hasil pangkat3 = {pangkat_3(3)}")
```

- `from matematika import tambah,kali,pangkat` → mengambil **3 fungsi spesifik** dari modul.
- Tidak perlu pakai `matematika.` lagi, bisa langsung panggil `tambah()`, `kali()`, `pangkat()`.

---

### File 3: `main_alias.py` — Import dengan Alias

```python
from matematika import tambah as add
from matematika import kali as k
from matematika import pangkat as terserah_kalian_mau_apa

import matematika as math

hasil_tambah = add(1,2,3,4,5)
print(f"hasil tambah = {hasil_tambah}")

hasil_kali = math.kali(1,2,3,4,5)
print(f"hasil tambah = {hasil_kali}")

pangkat_3 = terserah_kalian_mau_apa(3)
print(f"hasil pangkat3 = {pangkat_3(3)}")
```

- **`as`** → memberi **nama lain** (alias) untuk modul/fungsi.
- `tambah as add` → sekarang fungsi `tambah` dipanggil sebagai `add`.
- `import matematika as math` → modul `matematika` dipanggil sebagai `math`.
- Berguna untuk mempersingkat nama panjang.

---

## Tiga Cara Import

| Cara                              | Syntax                                      | Kelebihan                    | Kekurangan                  |
|-----------------------------------|----------------------------------------------|------------------------------|------------------------------|
| `import module`                   | `import matematika`                          | Jelas asalnya                | Harus pakai `module.func()`  |
| `from module import func`         | `from matematika import tambah`             | Langsung pakai `tambah()`    | Bisa bentrok nama            |
| `import module as alias`          | `import matematika as math`                 | Nama lebih pendek            | Orang lain harus lihat alias |

---

## Analogi

Bayangkan kamu **membuat resep masakan sendiri** dan membagikannya ke teman:

1. **Membuat module** = Menulis **buku resep** berisi 3 resep: Tambah, Kali, Pangkat.
2. **`import matematika`** = Teman meminjam **buku resep lengkap**. Saat memasak, mereka bilang "Resep dari buku Matematika: tambah(...)".
3. **`from matematika import tambah`** = Teman hanya **fotocopy resep Tambah**. Saat memasak, langsung pakai tanpa menyebut nama buku.
4. **`import matematika as math`** = Teman menulis **singkatan** di bukunya: "Math" = Buku Resep Matematika.

---

## Kesalahan Umum Pemula

- **`from matematika import *`**: Import semua fungsi. Tidak disarankan karena bisa **bentrok nama** dengan fungsi lain.
- **Lupa nama file modul**: Nama file `matematika.py` = nama modul yang di-import.
- **Circular import**: Jika `matematika.py` import `main_app.py` dan sebaliknya → error.
- **File modul harus di direktori yang sama**: atau di Python path.
