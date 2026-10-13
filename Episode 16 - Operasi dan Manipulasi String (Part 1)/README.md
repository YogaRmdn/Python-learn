# BAB 15 - Operasi dan Manipulasi String (Part 1)

## Apa yang Dipelajari

- Menyambung string (**concatenation**) dengan `+`
- Menghitung panjang string dengan `len()`
- Operator `in` dan `not in` untuk mengecek keberadaan karakter
- Mengulang string dengan `*`
- **Indexing** dan **slicing** string
- Fungsi `min()`, `max()`, `ord()`, `chr()`
- Method `count()` untuk menghitung kemunculan karakter

## Penjelasan Kode

---

### 1. Concatenation (Menyambung String)

```python
nama_pertama = "Ucup"
nama_tengah = "D"
nama_akhir = "Fame"

nama_lengkap = nama_pertama + nama_tengah + nama_akhir
print(nama_lengkap)  # Output: UcupDFame

nama_lengkap = nama_pertama + " " + nama_tengah + "'" + nama_akhir
print(nama_lengkap)  # Output: Ucup D'Fame
```
- Operator `+` pada string berfungsi sebagai **penggabung** (concatenation), bukan penjumlahan angka.
- Spasi `" "` bisa ditambahkan manual di antara string.

---

### 2. Panjang String

```python
panjang = len(nama_lengkap)
print("panjang " + nama_lengkap + " adalah " + str(panjang))
```
- `len()` mengembalikan **jumlah karakter** dalam string.
- `str(panjang)` diperlukan karena `panjang` adalah integer, dan `print()` dengan `+` butuh string.

---

### 3. Operator `in` dan `not in`

```python
d = "d"
status = d in nama_lengkap
print("apakah " + d + " ada di " + nama_lengkap + ", " + str(status))

D = "D"
status = D in nama_lengkap
print("apakah " + D + " ada di " + nama_lengkap + ", " + str(status))

x = "x"
status = x not in nama_lengkap
print("apakah " + x + " tidak ada di " + nama_lengkap + ", " + str(status))
```
- `in` mengecek **apakah karakter ada di dalam string** → menghasilkan `True/False`.
- `not in` mengecek **apakah karakter TIDAK ada** di dalam string.
- **Perhatian:** Python **case-sensitive** → `"d"` berbeda dari `"D"`.

---

### 4. Mengulang String

```python
print("wk"*100)
print(100*"wk")
```
- Operator `*` pada string berfungsi sebagai **pengulang**.
- `"wk" * 100` menghasilkan `"wk"` diulang 100 kali.

---

### 5. Indexing dan Slicing

```python
print("index ke-0 : " + nama_lengkap[0])       # karakter pertama
print("index ke-6 : " + nama_lengkap[6])       # karakter ke-6
print("index ke-(-1) : " + nama_lengkap[-1])   # karakter terakhir
print("index ke-[6,8) : " + nama_lengkap[6:8]) # slicing dari index 6 sampai sebelum 8
print("index ke-[0,2,4,6,8] : " + nama_lengkap[0:10:2]) # ambil index 0,2,4,6,8
```

| Sintaks | Keterangan | Contoh |
|---------|------------|--------|
| `s[i]` | Ambil karakter ke-`i` | `s[0]` = karakter pertama |
| `s[-1]` | Ambil karakter **terakhir** | `s[-1]` = karakter dari belakang |
| `s[a:b]` | Slice dari index `a` sampai **sebelum** `b` | `s[0:3]` = index 0,1,2 |
| `s[a:b:c]` | Slice dengan **step** `c` | `s[0:10:2]` = index 0,2,4,6,8 |

---

### 6. min, max, ord, chr

```python
print("nilai terkecil : " + min(nama_lengkap))
print("nilai terbesar : " + max(nama_lengkap))

ascii_code = ord(" ")
print("ASCII number dari spasi : " + str(ascii_code))

data = 117
print("Character dari ascii code 117 : " + chr(data))
```
- `min(string)` → karakter dengan **nilai ASCII terkecil**.
- `max(string)` → karakter dengan **nilai ASCII terbesar**.
- `ord(char)` → mengembalikan **kode ASCII** dari sebuah karakter.
- `chr(angka)` → mengembalikan **karakter** dari kode ASCII.

---

### 7. Method `count()`

```python
data = "otong surotong pararotong"
jumlah = data.count("o")
print("jumlah o di " + data + " : " + str(jumlah))
```
- `count("o")` menghitung **berapa kali** karakter `"o"` muncul dalam string.

## Tabel Ringkasan

| Operasi | Fungsi/Operator | Contoh | Hasil |
|---------|-----------------|--------|-------|
| Concatenation | `+` | `"Hi" + " " + "You"` | `"Hi You"` |
| Panjang | `len()` | `len("Hello")` | `5` |
| Cek keberadaan | `in` | `"e" in "Hello"` | `True` |
| Cek tidak ada | `not in` | `"x" not in "Hello"` | `True` |
| Ulang string | `*` | `"ha" * 3` | `"hahaha"` |
| Index ke-0 | `s[0]` | `"Hello"[0]` | `"H"` |
| Index terakhir | `s[-1]` | `"Hello"[-1]` | `"o"` |
| Slice | `s[a:b]` | `"Hello"[1:3]` | `"el"` |
| ASCII to char | `chr()` | `chr(65)` | `"A"` |
| Char to ASCII | `ord()` | `ord("A")` | `65` |
| Hitung kemunculan | `count()` | `"hello".count("l")` | `2` |

## Analogi

Bayangkan string seperti **deretan kotak huruf** (seperti papan skor di bandara):

- **Concatenation (`+`)** = Menyambungkan dua papan tulis jadi satu.
- **Indexing (`s[0]`)** = Membaca huruf di **kotak ke-0** (pertama).
- **Slicing (`s[1:4]`)** = Membaca **beberapa kotak sekaligus** dari kotak ke-1 sampai ke-3.
- **`in`** = "Apakah huruf **A** ada di papan ini?" → Ya/Tidak.
- **`len()`** = Menghitung **total kotak** di papan.
- **`min()`/`max()`** = Huruf dengan **nilai terkecil/terbesar** (berdasarkan urutan alfabet/ASCII).

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, operasi dan manipulasi string part 1 |
