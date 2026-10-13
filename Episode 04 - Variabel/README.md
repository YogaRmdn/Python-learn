# BAB 3 - Variabel

## Apa yang Dipelajari

- Apa itu variabel dalam Python
- Cara membuat (mendeklarasikan) variabel
- Assignment (penugasan nilai ke variabel)
- Aturan penamaan variabel
- Mengubah nilai variabel (reassignment)
- Assignment indirect (menyalin nilai antar variabel)

## Penjelasan Kode

```python
# Variabel adalah tempat menyimpan data

# menaru / assignment nilai
a = 10
x = 5
panjang = 1000

# pemanggilan pertama
print("Nilai a = ", a)
print("Nilai x = ", x)
print("Nilai panjang = ", panjang)

# penamaan
nilai_y = 15 # dengan menggunakan underscore
juta10 = 10000000 # ini boleh
nilaiZ = 17.5 # ini boleh

# pemanggilan kedua
print("Nilai a = ", a)
a = 7
print("Nilai a = ", a)

# assignment indirect
b = a
print("Nilai b = ", b)
```

### Penjelasan Baris per Baris

**Baris 1:**
```python
# Variabel adalah tempat menyimpan data
```
- Komentar yang menjelaskan bahwa variabel berfungsi sebagai **wadah penyimpanan data**.

**Baris 3-5 (Assignment):**
```python
a = 10
x = 5
panjang = 1000
```
- `a = 10` berarti membuat variabel bernama `a` dan menyimpan nilai `10` di dalamnya.
- `=` di sini bukan "sama dengan" dalam matematika, melainkan **operator assignment** (penugasan).
- Teks di sebelah kiri `=` adalah **nama variabel**, dan di sebelah kanan adalah **nilai** yang disimpan.

**Baris 7-9 (Pemanggilan Pertama):**
```python
print("Nilai a = ", a)
print("Nilai x = ", x)
print("Nilai panjang = ", panjang)
```
- `print("Nilai a = ", a)` menampilkan teks `"Nilai a = "` diikuti dengan **nilai** dari variabel `a` (yaitu `10`).
- Koma `,` di dalam `print()` berfungsi sebagai **pemisah** yang otomatis menambahkan spasi.
- Output: `Nilai a =  10`

**Baris 11-13 (Penamaan Variabel):**
```python
nilai_y = 15    # dengan menggunakan underscore
juta10 = 10000000  # ini boleh
nilaiZ = 17.5   # ini boleh
```
- **Aturan penamaan variabel Python:**
  - Bisa menggunakan huruf (a-z, A-Z), angka (0-9), dan underscore (`_`).
  - **Tidak boleh** dimulai dengan angka.
  - **Tidak boleh** menggunakan spasi.
  - **Tidak boleh** menggunakan kata kunci Python (seperti `if`, `for`, `while`, `class`, dll).
  - **Case-sensitive** (huruf besar dan kecil berbeda): `nilai_y` berbeda dari `NILAI_Y`.
- Contoh penamaan yang valid:
  - `nilai_y` (menggunakan underscore) ✅
  - `juta10` (dimulai dengan huruf) ✅
  - `nilaiZ` (camel case) ✅

**Baris 15-17 (Pemanggilan Kedua + Reassignment):**
```python
print("Nilai a = ", a)
a = 7
print("Nilai a = ", a)
```
- Baris 15: Mencetak nilai `a` yang pertama (masih `10`).
- Baris 16: `a = 7` **mengubah nilai** variabel `a` dari `10` menjadi `7`. Ini disebut **reassignment**.
- Baris 17: Mencetak nilai `a` yang baru (sudah `7`).

**Baris 19-20 (Assignment Indirect):**
```python
b = a
print("Nilai b = ", b)
```
- `b = a` menyalin nilai dari variabel `a` ke variabel `b`.
- Nilai `a` saat itu adalah `7`, maka `b` juga menjadi `7`.
- Ini disebut **assignment indirect** (penugasan tidak langsung) karena kita menyalin nilai dari variabel lain.

## Tabel Ringkasan

| Nama Variabel | Nilai | Tipe | Catatan |
|---------------|-------|------|---------|
| `a` | 10 → 7 | integer | Nilai diubah (reassignment) |
| `x` | 5 | integer | |
| `panjang` | 1000 | integer | Nama variabel deskriptif |
| `nilai_y` | 15 | integer | Penamaan dengan underscore |
| `juta10` | 10000000 | integer | Boleh diawali huruf, lalu angka |
| `nilaiZ` | 17.5 | float | Boleh ada huruf kapital di tengah |
| `b` | 7 | integer | Menyalin nilai dari `a` |

## Analogi

Bayangkan variabel adalah **kotak penyimpanan**:
- Kamu punya banyak kotak di gudang.
- Setiap kotak punya **label** (nama variabel) seperti `a`, `x`, `panjang`.
- Di dalam kotak kamu menyimpan **barang** (nilai) seperti angka `10`, `5`, `1000`.
- Kamu bisa **mengganti isi** kotak kapan saja (reassignment).
- Kamu bisa **menyalin isi** satu kotak ke kotak lainnya (assignment indirect): tinggal bilang "isi kotak `b` sama dengan isi kotak `a`".

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi penggunaan variabel |
