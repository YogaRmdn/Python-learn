# BAB 4 - Tipe Data

## Apa yang Dipelajari

- Apa itu tipe data dalam Python
- Tipe data umum: `integer`, `float`, `string`, `boolean`
- Tipe data khusus: `complex`
- Menggunakan modul `ctypes` dari bahasa C
- Fungsi `type()` untuk mengecek tipe data

## Penjelasan Kode

```python
# a = 10, a adalah variabel dengan nilai 10

# tipe data: Angka satuan yang gak ada
# koma nya (integer)
data_integer = 11
print("data : ", data_integer)
print("- bertipe : ", type(data_integer))

# tipe data: angka dengan koma (float)
data_float = 1.5
print("data : ", data_float)
print("- bertipe : ", type(data_float))

# tipe data: kumpulan karakter (string)
data_string = "ucup"
print("data : ", data_string)
print("- bertipe : ", type(data_string))

# tipe data: biner true/false (boolean)
data_bool = False
print("data : ", data_bool)
print("- bertipe : ", type(data_bool))

## tipe data khusus

# bilangan kompleks
data_complex = complex(5,6)
print("data : ", data_complex)
print("- bertipe : ", type(data_complex))

# tipe data dari bahasa C

from ctypes import c_double, c_char

data_c_double = c_double(10.5)
print("data : ", data_c_double)
print("- bertipe : ", type(data_c_double))
```

### Penjelasan per Tipe Data

---

#### 1. Integer (`int`) - Bilangan Bulat

```python
data_integer = 11
print("data : ", data_integer)
print("- bertipe : ", type(data_integer))
```
- `data_integer = 11` menyimpan bilangan bulat **11** (tanpa koma/desimal).
- `type(data_integer)` mengembalikan `<class 'int'>`.
- **Contoh lain:** `-5`, `0`, `100`, `99999`

---

#### 2. Float - Bilangan Desimal

```python
data_float = 1.5
print("data : ", data_float)
print("- bertipe : ", type(data_float))
```
- `data_float = 1.5` menyimpan bilangan **berkoma/desimal**.
- `type(data_float)` mengembalikan `<class 'float'>`.
- **Contoh lain:** `3.14`, `-0.5`, `100.0`

---

#### 3. String (`str`) - Teks/Karakter

```python
data_string = "ucup"
print("data : ", data_string)
print("- bertipe : ", type(data_string))
```
- `data_string = "ucup"` menyimpan **kumpulan karakter** (teks) dalam tanda kutip ganda.
- Bisa juga menggunakan tanda kutip tunggal: `'ucup'`.
- `type(data_string)` mengembalikan `<class 'str'>`.
- **Contoh lain:** `"Halo"`, `'Python 3'`, `"123"` (ini tetap string, bukan angka!)

---

#### 4. Boolean (`bool`) - Benar/Salah

```python
data_bool = False
print("data : ", data_bool)
print("- bertipe : ", type(data_bool))
```
- Boolean hanya punya **dua nilai**: `True` (benar) atau `False` (salah).
- Huruf **harus kapital**: `True` dan `False` (bukan `true` atau `false`).
- `type(data_bool)` mengembalikan `<class 'bool'>`.

---

#### 5. Complex - Bilangan Kompleks

```python
data_complex = complex(5, 6)
print("data : ", data_complex)
print("- bertipe : ", type(data_complex))
```
- `complex(5, 6)` membuat bilangan kompleks: **5 + 6j** (di mana `j` adalah unit imajiner).
- Bilangan kompleks digunakan dalam ilmu kalkulus dan fisika.
- Output: `(5+6j)`
- `type(data_complex)` mengembalikan `<class 'complex'>`.

---

#### 6. Tipe Data dari C (`ctypes`)

```python
from ctypes import c_double, c_char

data_c_double = c_double(10.5)
print("data : ", data_c_double)
print("- bertipe : ", type(data_c_double))
```
- `from ctypes import c_double, c_char` mengimpor tipe data dari **bahasa C**.
- `c_double(10.5)` membuat variabel dengan tipe `c_double` yang bernilai `10.5`.
- Ini adalah tipe data khusus yang jarang dipakai dalam Python sehari-hari, tapi berguna untuk **interoperabilitas** dengan program C.

## Tabel Tipe Data

| Tipe Data | Contoh Nilai | Fungsi Type | Deskripsi |
|-----------|-------------|-------------|-----------|
| `int` | `11`, `-5`, `0` | `type()` → `<class 'int'>` | Bilangan bulat |
| `float` | `1.5`, `3.14`, `-0.5` | `type()` → `<class 'float'>` | Bilangan desimal |
| `str` | `"ucup"`, `'hello'` | `type()` → `<class 'str'>` | Teks/karakter |
| `bool` | `True`, `False` | `type()` → `<class 'bool'>` | Benar atau Salah |
| `complex` | `complex(5,6)` → `(5+6j)` | `type()` → `<class 'complex'>` | Bilangan kompleks |
| `c_double` | `c_double(10.5)` | `type()` → `<class 'ctypes.c_double'>` | Tipe data C |

## Analogi

Bayangkan tipe data seperti **jenis wadah penyimpanan**:

- **Integer (`int`)** = **Toples kelereng** → Isinya kelereng (angka bulat) saja, tidak ada pecahan.
- **Float** = **Gelas ukur** → Bisa mengukur cairan sampai desimal, misalnya `1.5 liter`.
- **String (`str`)** = **Kotak surat** → Isinya tulisan/karakter, bisa apa saja yang kamu ketik.
- **Boolean (`bool`)** = **Lampu on/off** → Hanya ada dua kondisi: menyala (`True`) atau mati (`False`).
- **Complex** = **Peta koordinat** → Punya dua komponen: real dan imajiner (seperti koordinat x, y).

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi berbagai tipe data Python |
