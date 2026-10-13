# BAB 11 - Versi Lama 23: Package (Mengelola Module dalam Folder)

## Apa yang Dipelajari

- Konsep **package** — folder yang berisi modul-modul Python
- Peran file **`__init__.py`** sebagai penanda package
- Mengimpor semua isi package dengan `from .module import *`
- Mengimpor fungsi dari package dalam satu langkah

---

## Penjelasan Kode

### Struktur Folder

```
Versi Lama 23 - package/
├── main.py                  ← file utama yang dijalankan
└── sains/                   ← package (folder)
    ├── __init__.py          ← file inisialisasi package
    ├── fisika.py            ← modul fisika
    └── matematika.py        ← modul matematika
```

> **Catatan penting:** Agar folder `sains` bisa diimpor sebagai package, **wajib** ada file `__init__.py` di dalamnya.

---

### File 1: `sains/__init__.py` — Inisialisasi Package

```python
from .matematika import *
from .fisika import *
```

| Elemen | Penjelasan |
|--------|-----------|
| `from .matematika import *` | Mengimpor **semua** isi dari `sains/matematika.py` |
| `from .fisika import *` | Mengimpor **semua** isi dari `sains/fisika.py` |
| **Titik (`.`)** | Berarti **dari folder yang sama** (relative import). `"."` = folder saat ini (`sains`) |

> **`__init__.py`** = File yang dijalankan Python saat package diimpor. Ini menjadikan folder `sains` sebagai package, bukan sekadar folder biasa.

---

### File 2: `sains/matematika.py` — Modul Matematika

```python
def tambah(a, b):
    print('fungsi tambah')
    return a + b

def kurang(a, b):
    print('fungsi kurang')
    return a - b
```

| Fungsi | Mengembalikan |
|--------|--------------|
| `tambah(a, b)` | `a + b` |
| `kurang(a, b)` | `a - b` |

---

### File 3: `sains/fisika.py` — Modul Fisika

```python
def kecepatan(jarak, waktu):
    print('menghitung kecepatan')
    return jarak / waktu

def waktu_tempuh(kecepatan, jarak):
    print('menghitung waktu tempuh')
    return jarak / kecepatan
```

| Fungsi | Rumus | Mengembalikan |
|--------|-------|--------------|
| `kecepatan(jarak, waktu)` | v = s / t | kecepatan |
| `waktu_tempuh(kecepatan, jarak)` | t = s / v | waktu |

---

### File 4: `main.py` — File Utama

```python
from sains import tambah

tambah(2, 1)
# Output:
# fungsi tambah
# 3
```

| Elemen | Penjelasan |
|--------|-----------|
| `from sains import tambah` | Mengimpor fungsi `tambah` dari package `sains` |
| `tambah(2, 1)` | Memanggil fungsi → mencetak "fungsi tambah" dan mengembalikan 3 |

> **Bagaimana ini bisa jalan?**
> 1. `main.py` mengimpor `sains`
> 2. Python menjalankan `sains/__init__.py`
> 3. `__init__.py` menjalankan `from .matematika import *` → fungsi `tambah` dan `kurang` tersedia
> 4. `__init__.py` menjalankan `from .fisika import *` → fungsi `kecepatan` dan `waktu_tempuh` tersedia
> 5. Sekarang semua fungsi bisa diakses langsung dari `sains`: `from sains import tambah`

---

## Alur Import Package

```
main.py
  │
  └── from sains import tambah
        │
        └── Python menjalankan sains/__init__.py
              │
              ├── from .matematika import *  → tambah(), kurang()
              │
              └── from .fisika import *      → kecepatan(), waktu_tempuh()
```

---

## Analogi

### Package = **Lemari Arsip dengan Banyak Laci**

Bayangkan **lemari arsip** bernama `sains`:

| Laci | Isi |
|------|-----|
| `__init__.py` | **Daftar isi** lemari — mencantumkan semua laci dan isinya |
| `matematika.py` | Laci berisi alat: **kalkulator**, **penggaris** |
| `fisika.py` | Laci berisi alat: **meteran**, ** stopwatch** |

**Cara menggunakannya:**

1. Kamu datang ke lemari `sains`.
2. Kamu melihat **daftar isi** (`__init__.py`) yang memberitahu: "Di sini ada kalkulator, penggaris, meteran, dan stopwatch."
3. Kamu mengambil **kalkulator** (`from sains import tambah`) — bisa langsung dipakai tanpa perlu tahu di laci mana kalkulator itu berada.

> **Kunci:** File `__init__.py` berfungsi sebagai **daftar isi** lemari. Tanpa daftar ini, Python tidak tahu isi package dan kamu harus mengimpor per laci: `from sains.matematika import tambah`.
