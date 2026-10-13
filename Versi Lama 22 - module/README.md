# BAB 10 - Versi Lama 22: Module (Membuat Module Sendiri)

## Apa yang Dipelajari

- Membuat **module sendiri** (file `.py` berisi fungsi-fungsi)
- Berbagai cara **mengimpor** fungsi dari modul
- Menggunakan **alias** dengan `import ... as`
- Mengimpor fungsi tertentu dengan `from ... import`

---

## Penjelasan Kode

### Struktur Folder

```
Versi Lama 22 - module/
├── main.py        ← file utama yang dijalankan
└── matematika.py  ← modul berisi fungsi matematika
```

---

### File 1: `matematika.py` — Module

```python
def tambah(a, b):
    print('fungsi tambah')
    print(a, '+', b, '=', a + b)

def kurang(a, b):
    print('fungsi kurang')
    print(a, '-', b, '=', a - b)
```

| Fungsi | Parameter | Yang Dilakukan |
|--------|-----------|---------------|
| `tambah(a, b)` | Dua angka | Mencetak operasi penjumlahan |
| `kurang(a, b)` | Dua angka | Mencetak operasi pengurangan |

---

### File 2: `main.py` — File Utama

File ini menunjukkan **berbagai cara import** (bebaris dikomentari untuk demonstrasi):

#### Cara 1: `import` Biasa
```python
# import matematika
# matematika.tambah(3, 4)   → Output: fungsi tambah / 3 + 4 = 7
# matematika.kurang(4, 5)   → Output: fungsi kurang / 4 - 5 = -1
```
- Harus pakai **nama modul** di depan: `matematika.tambah()`

#### Cara 2: `import ... as` (Alias)
```python
# import matematika as m
# m.tambah(3, 4)
# m.kurang(5, 4)
```
- Bisa pakai **nama pendek** (`m`): `m.tambah()`

#### Cara 3: `from ... import` Fungsi Tertentu
```python
# from matematika import tambah, kurang
# tambah(4, 5)   ← langsung tanpa nama modul
# kurang(5, 4)
```
- Bisa panggil **langsung**: `tambah()` tanpa `matematika.`

#### Cara 4: `from ... import *` (Semua)
```python
# from matematika import *
# tambah(4, 5)
# kurang(5, 4)
```
- Mengimpor **semua fungsi** — praktis tapi berisiko menimpa nama yang sama.

#### Cara 5: `from ... import ... as` (Alias Fungsi) ✅ Yang Aktif
```python
from matematika import tambah as t

t(3, 4)
# Output:
# fungsi tambah
# 3 + 4 = 7
```

| Elemen | Penjelasan |
|--------|-----------|
| `from matematika import tambah as t` | Impor fungsi `tambah`, beri alias `t` |
| `t(3, 4)` | Panggil fungsi dengan nama alias |

---

## Perbandingan Cara Import

| Cara | Sintaks | Perlu Nama Modul? | Perlu Nama Fungsi? |
|------|---------|-------------------|---------------------|
| Import modul | `import matematika` | `matematika.tambah()` | Ya |
| Alias modul | `import matematika as m` | `m.tambah()` | Ya |
| Import fungsi | `from matematika import tambah` | Tidak | `tambah()` |
| Import semua | `from matematika import *` | Tidak | Tidak |
| Alias fungsi | `from matematika import tambah as t` | Tidak | `t()` |

---

## Analogi

### Module = **Toolkit / Kotak Peralatan**

Bayangkan kamu punya **kotak perkakas** (`matematika.py`) berisi:
- **Palu** (`tambah()`) — untuk menumbuk
- **Obeng** (`kurang()`) — untuk membuka

Cara menggunakannya:

1. **Bawa seluruh kotak** → `import matematika` → pakai: `matematika.palu()`
2. **Bawa kotak dengan nama pendek** → `import matematika as m` → pakai: `m.palu()`
3. **Ambil hanya palu** → `from matematika import palu` → pakai: `palu()`
4. **Ambil semua isi kotak** → `from matematika import *` → pakai: `palu()`
5. **Ambil palu, beri nama "pukul"** → `from matematika import palu as pukul` → pakai: `pukul()`

> **Tips untuk pemula:** Gunakan **Cara 3** (`from matematika import tambah`) untuk kode yang lebih ringkas, atau **Cara 2** (`import matematika as m`) untuk kode yang lebih jelas dari mana fungsinya berasal.
