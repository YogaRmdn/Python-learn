# BAB 17 - Init pada Package

## Apa yang Dipelajari

- **`__init__.py`**: file spesial yang menjadikan folder sebagai Python **package**
- Fungsi `__init__.py`: menjalankan kode saat package di-import
- Menggunakan **relative import** (`from . import ...`)
- Package bersarang (sub-package): package di dalam package
- Import fungsi langsung dari sub-package

---

## Penjelasan Kode

### Struktur Folder

```
Episode 57 - Init pada Package/
├── main_app.py              ← Program utama
└── sains/                   ← Package utama
    ├── __init__.py          ← Inisialisasi package sains
    ├── pisika.py            ← Module fisika (note: penulisannya "pisika")
    └── matematika/          ← Sub-package (package di dalam package)
        ├── __init__.py      ← Inisialisasi sub-package matematika
        ├── basic.py         ← Module operasi dasar
        └── scientific.py    ← Module operasi lanjut
```

---

### File 1: `sains/__init__.py` (Init Package Utama)

```python
from . import matematika
from . import pisika

# __all__ = [
#     "matematika",
#     "pisika"
# ]
```

- **`from . import matematika`** → import sub-package `matematika` dari package `sains`.
- **Titik `.`** = **relative import**, artinya "dari package yang sedang berada" (sains).
- **`from . import pisika`** → import module `pisika` dari package yang sama.
- `__all__` (dikomentari) → daftar module yang akan di-import jika pakai `from sains import *`.

**Yang terjadi saat `import sains`:**
1. Python menjalankan `sains/__init__.py`.
2. `__init__.py` meng-import `matematika` dan `pisika`.
3. Sekarang bisa akses `sains.matematika` dan `sains.pisika`.

---

### File 2: `sains/matematika/__init__.py` (Init Sub-Package)

```python
from . import basic
from . import scientific

from .basic import tambah,kali
from .scientific import pangkat
```

- **Baris 1-2**: Import module `basic` dan `scientific` dari sub-package `matematika`.
- **Baris 4**: Import **fungsi spesifik** `tambah` dan `kali` dari `basic`.
- **Baris 5**: Import **fungsi spesifik** `pangkat` dari `scientific`.
- **Hasil**: Kita bisa akses `sains.matematika.tambah()` langsung (tidak perlu `sains.matematika.basic.tambah()`).

---

### File 3: `sains/matematika/basic.py`

```python
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
```

- Fungsi **tambah**: menjumlahkan semua angka.
- Fungsi **kali**: mengalikan semua angka.

### File 4: `sains/matematika/scientific.py`

```python
def pangkat(n):
    return lambda angka:angka**n
```

- Fungsi **pangkat**: currying untuk membuat fungsi pangkat.
- `pangkat(3)` → `lambda angka:angka**3`

### File 5: `sains/pisika.py`

```python
def gaya(m,a):
    return m*a
```

- Fungsi **gaya**: menghitung gaya = massa × percepatan.

---

### File 6: `main_app.py` (Program Utama)

```python
import sains
from sains.matematika import scientific

hasil_tambah = sains.matematika.tambah(1,2,3,4,45)
print(f"hasil tambah = {hasil_tambah}")

hasil_pisika = sains.pisika.gaya(10,9.8)
print(f"hasil pisika = {hasil_pisika}")

hasil_kali = sains.matematika.kali(1,3,4,5,6)
print(f"hasil kali = {hasil_kali}")

pangkat_3 = scientific.pangkat(3)
print(f"hasil pangkat 3 = {pangkat_3(5)}")
```

**Penjelasan baris per baris:**

1. `import sains` → import package `sains`. Karena ada `__init__.py`, semua module di dalamnya langsung bisa diakses.
2. `from sains.matematika import scientific` → import module `scientific` dari sub-package `matematika`.
3. `sains.matematika.tambah(1,2,3,4,45)` → `1+2+3+4+45 = 55`
4. `sains.pisika.gaya(10,9.8)` → `10 × 9.8 = 98.0`
5. `sains.matematika.kali(1,3,4,5,6)` → `1×3×4×5×6 = 360`
6. `scientific.pangkat(3)` → fungsi pangkat 3
7. `pangkat_3(5)` → `5**3 = 125`

**Output:**
```
hasil tambah = 55
hasil pisika = 98.0
hasil kali = 360
hasil pangkat 3 = 125
```

---

## Struktur Package Lengkap

```
sains/                          ← Package Utama
├── __init__.py                 ← Inisialisasi: import matematika & pisika
├── pisika.py                   ← Module: fungsi gaya()
│
└── matematika/                 ← Sub-Package
    ├── __init__.py             ← Inisialisasi: import basic & scientific
    ├── basic.py                ← Module: fungsi tambah(), kali()
    └── scientific.py           ← Module: fungsi pangkat()
```

---

## Analogi

Bayangkan **toko serba ada**:

- **Package `sains`** = **Toko "Sains Jaya"** (toko utama).
- **`__init__.py` sains** = **Papan nama toko** yang menunjukkan departemen yang tersedia: Matematika dan Fisika.
- **Sub-package `matematika`** = **Departemen Matematika** di dalam toko.
- **`__init__.py` matematika** = **Papan nama departemen** yang menunjukkan bagian: Basic (alat tulis) dan Scientific (alat laboratorium).
- **`basic.py`** = Rak produk alat tulis (pensil, penggaris).
- **`scientific.py`** = Rak produk alat laboratorium (mikroskop, tabung reaksi).
- **`import sains`** = Kamu masuk toko. Papan nama langsung memberi tahu semua departemen.
- **`sains.matematika.tambah()`** = Kamu ke Departemen Matematika, ambil produk "tambah", pakai.

---

## Perbedaan dengan Episode 56

| Aspek               | Episode 56 (Tanpa `__init__.py`) | Episode 57 (Dengan `__init__.py`) |
|---------------------|-----------------------------------|------------------------------------|
| Import package      | `import sains.matematika`        | `import sains`                    |
| Akses module        | Harus path lengkap                | Bisa lebih ringkas karena `__init__` sudah import |
| Sub-package         | Tidak ada                         | Ada (matematika/)                 |
| Relative import     | Tidak ada                         | `from . import ...`               |

---

## Kesalahan Umum Pemula

- **Lupa `__init__.py`**: Tanpa file ini, folder tidak dikenali sebagai package (di Python < 3.3).
- **Relative import salah**: `from . import` hanya bisa dipakai di dalam package, bukan di file biasa.
- **Path terlalu panjang**: Jika sering pakai `sains.matematika.basic.tambah()`, bisa import langsung di `__init__.py` agar lebih pendek.
