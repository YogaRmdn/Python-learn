# BAB 14 - Import Statement

## Apa yang Dipelajari

- **Import**: cara mengambil kode dari file `.py` lain
- Tiga cara import: `import`, `from ... import`, dan `import ... as`
- Import **modul** (file `.py` lain) dalam satu direktori
- Menggunakan **variabel** dan **fungsi** dari modul yang di-import
- Konsep **namespace** dalam import

---

## Penjelasan Kode

### File Utama: `main_app.py`

#### 1. Import untuk Menyambung Program dari File Lain

```python
import program_print
import program_ucup
```

- `import program_print` → menjalankan semua kode di dalam `program_print.py`.
- `import program_ucup` → menjalankan semua kode di dalam `program_ucup.py`.

**File `program_print.py`:**
```python
print("test")
```

**File `program_ucup.py`:**
```python
print("Hai saya Ucup")
```

- Saat `main_app.py` dijalankan, output langsung muncul:
  ```
  test
  Hai saya Ucup
  ```
- Karena kode `print()` di dalam file-file itu **dieksekusi otomatis** saat file di-import.

#### 2. Import dengan Data (Variabel)

```python
import variable
import kucuy

# data ada di namespace variable
print(variable.data)
print(kucuy.data)
```

**File `variable.py`:**
```python
data = "Faqihza guanteeeeng Habis"
```

**File `kucuy.py`:**
```python
data = "Mukhlish guanteng puoool!"
```

- `variable.data` → mengakses variabel `data` dari file `variable.py`.
- `kucuy.py` juga punya variabel `data`, tapi karena di-namespace berbeda (`kucuy.data`), tidak bentrok.
- Output:
  ```
  Faqihza guanteeeeng Habis
  Mukhlish guanteng puoool!
  ```

#### 3. Import dengan Fungsi

```python
import matematika

hasil = matematika.tambah(4,5)
print(hasil)
```

**File `matematika.py`:**
```python
def tambah(a:float,b:float)->float:
    return a+b
```

- `matematika.tambah(4,5)` → memanggil fungsi `tambah` dari file `matematika.py`.
- Hasil: `4 + 5 = 9`
- Output: `9`

---

## Ringkasan File di Folder Episode 54

| File               | Isi                                               | Fungsi                          |
|--------------------|---------------------------------------------------|---------------------------------|
| `main_app.py`      | Program utama, mengimpor semua modul              | Menjalankan dan mengakses modul |
| `program_print.py` | `print("test")`                                   | Cetak "test" saat di-import     |
| `program_ucup.py`  | `print("Hai saya Ucup")`                          | Cetak sapaan saat di-import     |
| `variable.py`      | `data = "Faqihza guanteeeeng Habis"`             | Menyimpan data string           |
| `kucuy.py`         | `data = "Mukhlish guanteng puoool!"`             | Menyimpan data string lain      |
| `matematika.py`    | Fungsi `tambah(a, b)`                            | Menjumlahkan dua angka          |

---

## Cara Import dalam Python

| Syntax                       | Penjelasan                                      | Contoh Penggunaan       |
|------------------------------|--------------------------------------------------|--------------------------|
| `import module`              | Import seluruh modul                             | `module.fungsi()`        |
| `from module import item`    | Import item tertentu saja                        | `fungsi()` langsung      |
| `from module import *`       | Import semua item (tidak disarankan)             | `fungsi()` langsung      |
| `import module as alias`     | Import dengan nama alias                         | `alias.fungsi()`         |
| `from module import item as a` | Import item dengan alias                       | `a()` langsung           |

---

## Analogi

Bayangkan **perpustakaan**:

- **Import** = Kamu **meminjam buku** dari perpustakaan ke meja belajarmu.
- **`import matematika`** = Kamu meminjam buku **Matematika Lengkap**. Untuk membaca, kamu harus tulis: `matematika.bab1()`.
- **`from matematika import tambah`** = Kamu hanya meminjam **bab Penjumlahan**. Langsung baca tanpa perlu menyebut nama bukunya.
- **Namespace** = Meja belajarmu: setiap buku punya "area" sendiri, jadi tidak tertukar.

---

## Kesalahan Umum Pemula

- **File modul harus satu direktori**: File yang di-import harus berada di folder yang sama dengan file pemanggil.
- **Kode di modul dieksekusi saat import**: Jadi `print("test")` akan langsung muncul saat kamu `import program_print`.
- **Namespace**: Kamu harus pakai `module.item` kecuali pakai `from module import item`.
- **Circular import**: Jika file A import file B, dan file B import file A → error.
