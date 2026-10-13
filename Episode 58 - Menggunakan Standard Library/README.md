# BAB 18 - Menggunakan Standard Library

## Apa yang Dipelajari

- **Standard Library**: kumpulan module bawaan Python yang siap pakai
- Menggunakan module `datetime` untuk bekerja dengan tanggal dan waktu
- Menggunakan module `collections.Counter` untuk menghitung frekuensi item
- Membaca file teks dengan module `io`
- Tidak perlu install apapun, tinggal `import`

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Module `datetime`

```python
import datetime

data_waktu = datetime.datetime.now()
print(f"datetime now : {data_waktu}")
print(f"tahun : {data_waktu.year}")
print(f"hari : {data_waktu.strftime('%A')}")
```

- **`datetime.datetime.now()`** → mengambil waktu **saat ini** (tanggal, jam, menit, detik).
- **`.year`** → mengambil komponen **tahun** dari objek datetime.
- **`.strftime('%A')`** → format datetime menjadi **nama hari** (Senin, Selasa, dst.).

Contoh output:
```
datetime now : 2026-09-06 14:30:25.123456
tahun : 2026
hari : Sunday
```

#### 2. Module `collections.Counter`

```python
from collections import Counter

data = ["a","b","c","d","a","d","a"]
data_count = Counter(data)

print(f"data count = {data_count}")
print(f"jumlah a = {data_count['a']}")
print(f"jumlah d = {data_count['d']}")
```

- **`Counter`** → menghitung **frekuensi kemunculan** setiap item dalam list/iterable.
- `Counter(["a","b","c","d","a","d","a"])` → `{'a': 3, 'd': 2, 'b': 1, 'c': 1}`
- `data_count['a']` → berapa kali `"a"` muncul = **3 kali**.
- `data_count['d']` → berapa kali `"d"` muncul = **2 kali**.

Contoh output:
```
data count = Counter({'a': 3, 'd': 2, 'b': 1, 'c': 1})
jumlah a = 3
jumlah d = 2
```

#### 3. Module `io` (Baca File)

```python
import io

file = io.open("file_text.txt","r")
print(file.read())
```

- **`io.open("file_text.txt", "r")`** → membuka file `file_text.txt` dalam mode **read** (`"r"`).
- **`.read()`** → membaca **seluruh isi file** sebagai string.

**File `file_text.txt`:**
```
Say hello from Otong Surotong, makin sekut di mari
```

Output:
```
Say hello from Otong Surotong, makin sekut di mari
```

---

## Standard Library yang Dipelajari

| Module              | Fungsi                                         | Contoh Penggunaan                         |
|---------------------|------------------------------------------------|--------------------------------------------|
| `datetime`          | Bekerja dengan tanggal dan waktu               | `datetime.datetime.now()`                 |
| `collections.Counter` | Menghitung frekuensi item                    | `Counter(["a","a","b"])` → `{'a':2, 'b':1}` |
| `io`                | Operasi input/output (termasuk baca file)       | `io.open("file.txt", "r")`                |

---

## Modul Standard Library Populer Lainnya

| Module       | Fungsi                                    | Contoh                           |
|--------------|-------------------------------------------|----------------------------------|
| `os`         | Interaksi dengan sistem operasi           | `os.system("cls")`              |
| `math`       | Fungsi matematika lanjut                  | `math.sqrt(16)` → 4.0           |
| `random`     | Generate angka acak                       | `random.randint(1,10)`          |
| `string`     | Konstanta string                          | `string.ascii_uppercase`        |
| `json`       | Baca/tulis file JSON                      | `json.loads(data)`              |
| `re`         | Regular expressions                       | `re.findall(r'\d+', text)`      |
| `sys`        | Informasi interpreter Python              | `sys.version`                   |

---

## Analogi

Bayangkan **Standard Library** adalah **perlengkapan masak bawaan di dapur**:

- **`datetime`** = **Jam dinding** di dapur. Kamu bisa tahu waktu sekarang, tanggal, hari.
- **`collections.Counter`** = **Timbangan** yang menghitung berapa kali bahan tertentu dipakai.
- **`io`** = **Buku resep** yang bisa kamu buka dan baca isinya.
- Kamu **tidak perlu beli** perlengkapan ini (install), karena sudah tersedia di dapur (Python).

---

## Cara Menggunakan Standard Library

```python
# 1. Import seluruh module
import datetime

# 2. Import item tertentu
from collections import Counter

# 3. Import dengan alias
import datetime as dt
```

**Tips:** Tidak perlu menghafal semua standard library. Cukup tahu **apa yang tersedia**, nanti bisa googling saat dibutuhkan.

---

## Kesalahan Umum Pemula

- **File path**: `io.open("file_text.txt")` harus dijalankan dari **direktori yang sama** dengan file teks.
- **Lupa tutup file**: Sebaiknya pakai `with open(...) as file:` agar file otomatis ditutup.
- **Memasang module yang sudah ada**: Jangan `pip install datetime` karena `datetime` sudah bawaan Python.
