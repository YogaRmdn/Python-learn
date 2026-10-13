# BAB 12 - Versi Lama 24: `__name__ == "__main__"`

## Apa yang Dipelajari

- Konsep `__name__` di Python
- Perbedaan **menjalankan langsung** vs **diimpor** sebagai modul
- Menggunakan `if __name__ == "__main__"` sebagai **entry point**
- Membuat modul yang bisa **dijalankan sendiri** sekaligus **diimpor** oleh modul lain

---

## Penjelasan Kode

### Struktur Folder

```
Versi Lama 24 - __main__/
├── main.py        ← file utama yang dijalankan
└── matematika.py  ← modul yang bisa dijalankan & diimpor
```

---

### File 1: `matematika.py` — Module dengan `__main__`

```python
def tambah(a, b):
    print(a, '+', b, '=', a + b)

def kurang(a, b):
    print(a, '-', b, '=', a - b)

def main():
    print('ini adalah fungsi utama dari matematika')

if __name__ == '__main__':
    main()
```

#### Penjelasan Tiap Bagian:

**1. Fungsi-fungsi Biasa:**

```python
def tambah(a, b):
    print(a, '+', b, '=', a + b)

def kurang(a, b):
    print(a, '-', b, '=', a - b)
```

Fungsi-fungsi ini bisa dipanggil dari mana saja — saat file dijalankan langsung **atau** saat diimpor.

**2. Fungsi `main()`:**

```python
def main():
    print('ini adalah fungsi utama dari matematika')
```

Fungsi khusus yang berisi kode **tes/pengujian** untuk memastikan modul berjalan dengan benar.

**3. Kondisi `if __name__ == "__main__"`:**

```python
if __name__ == '__main__':
    main()
```

| Elemen | Penjelasan |
|--------|-----------|
| `__name__` | Variabel spesial Python yang otomatis ada di setiap file |
| `"__main__"` | Nilai `__name__` jika file **dijalankan langsung** (`python matematika.py`) |
| Kondisi ini | `True` hanya jika file dijalankan langsung — **tidak berlaku** saat file diimpor |

---

### File 2: `main.py` — File Utama

```python
import matematika as mm

mm.tambah(3, 5)
mm.kurang(3, 5)
```

**Output:**
```
3 + 5 = 8
3 - 5 = -2
```

> **Penting:** Saat `main.py` mengimpor `matematika`, fungsi `main()` di dalam `matematika.py` **TIDAK dijalankan** karena `__name__` bernilai `"matematika"` (bukan `"__main__"`).

---

## Perbedaan: Dijalankan Langsung vs Diimpor

### Skenario 1: Menjalankan `matematika.py` Langsung

```bash
python matematika.py
```

| `__name__` | `if __name__ == "__main__"` | Hasil |
|------------|---------------------------|-------|
| `"__main__"` | `True` ✅ | `main()` **dijalankan** → Output: "ini adalah fungsi utama dari matematika" |

### Skenario 2: Mengimpor `matematika.py` dari `main.py`

```bash
python main.py
```

| `__name__` | `if __name__ == "__main__"` | Hasil |
|------------|---------------------------|-------|
| `"matematika"` | `False` ❌ | `main()` **TIDAK dijalankan** — hanya fungsi `tambah()` dan `kurang()` yang tersedia |

---

## Mengapa Ini Penting?

Bayangkan `matematika.py` punya kode **tes** di dalamnya:

```python
def tambah(a, b):
    return a + b

# Kode tes (hanya ingin dijalankan saat testing)
print("Hasil tes:", tambah(3, 4))  # ← ini akan MENGANGGU saat diimpor!
```

Tanpa `if __name__ == "__main__"`, **setiap kali** `matematika.py` diimpor, kode tes akan berjalan. Dengan pola `__main__`, kode tes hanya berjalan saat file dijalankan langsung.

```python
def tambah(a, b):
    return a + b

# ✅ Kode tes hanya berjalan saat dijalankan langsung
if __name__ == "__main__":
    print("Hasil tes:", tambah(3, 4))
```

---

## Ringkasan

| `__name__` | Kondisi | Kode di `if` berjalan? |
|------------|---------|----------------------|
| `"__main__"` | File dijalankan langsung | Ya ✅ |
| `"nama_modul"` | File diimpor dari modul lain | Tidak ❌ |

---

## Analogi

### `__name__ == "__main__"` = **Saklar Lampu**

Bayangkan sebuah **lampu pintar** di kamar:
- **Saat kamu berada di kamar** (file dijalankan langsung): lampu **menyala** — karena memang untuk kamu.
- **Saat orang lain lewat di depan kamar** (file diimpor): lampu **tidak menyala** — karena orang itu bukan kamu.

```python
if __name__ == "__main__":
    # "Jika yang menjalankan saya adalah pemilik kamar (file sendiri),
    #  nyalakan lampu (jalankan kode tes)."
    nyalakan_lampu()
```

> **Aturan emas:** Selalu gunakan `if __name__ == "__main__":` di file modul kamu. Ini memastikan modul bisa **dijalankan sendiri untuk testing** sekaligus **diaman diimpor** oleh modul lain tanpa efek samping.
