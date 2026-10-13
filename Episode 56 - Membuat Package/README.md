# BAB 16 - Membuat Package

## Apa yang Dipelajari

- **Package**: folder yang berisi beberapa modul (file `.py`) dan bisa di-import
- Membuat **subfolder** sebagai package
- Import dari package: `import package.module`, `from package import module`
- Import dengan alias dari package
- Struktur folder package

---

## Penjelasan Kode

### Struktur Folder

```
Episode 56 - Membuat Package/
├── main_app.py          ← Program utama
└── sains/               ← Package (folder)
    ├── matematika.py    ← Module matematika
    └── fisika.py        ← Module fisika
```

- Folder `sains/` berisi 2 module: `matematika.py` dan `fisika.py`.
- Folder `sains/` berfungsi sebagai **package** (kumpulan module).

---

### File 1: `sains/matematika.py` (Module di dalam Package)

```python
'''Module matematika'''

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

def pangkat(n):
    return lambda angka:angka**n
```

- Berisi 3 fungsi: `tambah()`, `kali()`, `pangkat()`.
- Sama seperti module di Episode 55, tapi sekarang ditempatkan di dalam folder `sains/`.

### File 2: `sains/fisika.py` (Module di dalam Package)

```python
''' module fisika '''

def gaya(m,a):
    return m*a
```

- Fungsi `gaya(m, a)` menghitung **gaya = massa × percepatan** (Hukum Newton II).

---

### File 3: `main_app.py` (Program Utama)

#### 1. Import dengan Path Lengkap

```python
import sains.matematika
```

- `import sains.matematika` → import module `matematika` yang ada di dalam package `sains`.
- Akses fungsi: `sains.matematika.tambah(1,2,3,4,5)`

```python
hasil_tambah = sains.matematika.tambah(1,2,3,4,5)
print(f"hasil tambah dari package adalah = {hasil_tambah}")
```

- Output: `hasil tambah dari package adalah = 15`

#### 2. Import dengan `from ... import`

```python
from sains import fisika
```

- Import module `fisika` dari package `sains`.
- Akses fungsi: `fisika.gaya(90,10)`

```python
gaya = fisika.gaya(90,10)
print(f"gaya adalah = {gaya}")
```

- `90 × 10 = 900`
- Output: `gaya adalah = 900`

#### 3. Import dengan Alias

```python
from sains.fisika import gaya as force
```

- Mengambil fungsi `gaya` dari `sains.fisika` dan memberi **alias** `force`.

```python
gaya = force(90,10)
print(f"gaya adalah = {gaya}")
```

- `force(90,10)` = `90 × 10 = 900`
- Output: `gaya adalah = 900`

---

## Cara Import dari Package

| Syntax                          | Penjelasan                                      |
|---------------------------------|--------------------------------------------------|
| `import sains.matematika`       | Import module, akses: `sains.matematika.func()`  |
| `from sains import fisika`      | Import module, akses: `fisika.func()`            |
| `from sains.fisika import gaya as force` | Import fungsi + alias, akses: `force()` |

---

## Analogi

Bayangkan **package** seperti **folder di komputer**:

- **Package `sains/`** = Folder bernama "Sains" di dalam My Documents.
- **Module `matematika.py`** = File Excel di folder Sains berisi rumus matematika.
- **Module `fisika.py`** = File Word di folder Sains berisi rumus fisika.
- **`import sains.matematika`** = Kamu membuka folder Sains, lalu membuka file Matematika.
- **`from sains import fisika`** = Kamu langsung mengambil file Fisika dari folder Sains.

---

## Kesalahan Umum Pemula

- **Folder tanpa file `.py`**: Folder tidak akan dikenali sebagai package tanpa file Python di dalamnya (di Python 3.3+ bisa jalan tanpa `__init__.py`, tapi lebih baik pakai).
- **Path import**: Harus tepat: `sains.matematika` (bukan `sains/mematika`).
- **Modul sama nama**: Jika ada `sains/matematika.py` dan `fisika/matematika.py`, keduanya bisa di-import tanpa bentrok karena beda package.
