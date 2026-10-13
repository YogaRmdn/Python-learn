# BAB 9 - Versi Lama 21: Import (Modularisasi)

## Apa yang Dipelajari

- Konsep **modul** dan **import** di Python
- Bagaimana mengimpor file `.py` lain dalam satu folder
- Mengakses **variabel** dan **fungsi** dari modul lain

---

## Penjelasan Kode

### Struktur Folder

```
Versi Lama 21 - import/
├── main.py    ← file utama yang dijalankan
└── modul.py   ← file modul yang diimpor
```

---

### File 1: `modul.py` — Modul yang Diimpor

```python
data = "apa kabs?"

def cek_modul():
    print("hallo gan")

print("ini adalah modul saya")
```

| Elemen | Penjelasan |
|--------|-----------|
| `data = "apa kabs?"` | Variabel yang bisa diakses dari modul lain |
| `def cek_modul()` | Fungsi yang bisa dipanggil dari modul lain |
| `print("ini adalah modul saya")` | Kode yang **langsung dijalankan** saat `modul.py` diimpor |

> **Penting:** Saat sebuah modul diimpor, **seluruh kode** di dalamnya dijalankan — termasuk `print()` di baris terakhir.

---

### File 2: `main.py` — File Utama

```python
import modul

print(modul.data)

modul.cek_modul()
```

**Output:**
```
ini adalah modul saya          ← dari print di modul.py (saat import)
apa kabs?                      ← dari print(modul.data)
hallo gan                      ← dari modul.cek_modul()
```

| Elemen | Penjelasan |
|--------|-----------|
| `import modul` | Mengimpor seluruh isi file `modul.py` |
| `modul.data` | Mengakses variabel `data` dari `modul` menggunakan **notasi titik** |
| `modul.cek_modul()` | Memanggil fungsi `cek_modul()` dari `modul` |

---

## Cara Import Lainnya (Tambahan)

| Sintaks | Penjelasan | Contoh Penggunaan |
|---------|-----------|-------------------|
| `import modul` | Impor seluruh modul | `modul.data` |
| `from modul import data` | Impor variabel tertentu | `data` (tanpa nama modul) |
| `from modul import *` | Impor semua isi modul | `data`, `cek_modul()` (tanpa nama modul) |
| `import modul as m` | Alias nama modul | `m.data` |

---

## Analogi

### Modul = **Buku Resep Masakan**

Bayangkan kamu punya **dua buku**:
- **Buku Resep** (`modul.py`) berisi daftar bahan dan cara memasak.
- **Buku Harian** (`main.py`) yang kamu tulis setiap hari.

Saat kamu menulis di **Buku Harian**, kamu bisa **membuka Buku Resep** dan menulis: "Hari ini saya memasak resep dari Buku Resep: Nasi Goreng."

```python
# Di Buku Harian (main.py)
import buku_resep

print(buku_resep.resep_hari_ini)  # ← mengakses data dari Buku Resep
buku_resep.masak()                # ← menjalankan instruksi dari Buku Resep
```

> **Kunci:** Kedua file harus berada dalam **satu folder yang sama** agar bisa saling mengimpor tanpa konfigurasi tambahan.
