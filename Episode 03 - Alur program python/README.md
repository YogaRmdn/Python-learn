# BAB 2 - Alur Program Python

## Apa yang Dipelajari

- Alur eksekusi program Python dari atas ke bawah (top-to-bottom)
- Urutan eksekusi baris kode
- Cara menggunakan modul `time` untuk mengukur waktu eksekusi
- Comment (komentar) dalam Python: single line dan multiline
- Variabel sederhana dan assignment
- Compiling Python ke bytecode

## Penjelasan Kode

### File: `Main.py`

```python
import time
start_time = time.time()

print("Hello")
print("World")
print("Hello World")

print("Halo Chantiiek")
# ini adalah comment
a = 10 # ini adalah comment juga
"""ada apa dengan
ucup dan otong si ganteng
dalam comment multiline"""
print(a)
print(time.time() - start_time, "detik")
# kita bisa mengcompile python ke
# yang namanya bytecode
# cara mengcompile, buka terminal dan tuliskan
# python -m py_compile Main.py
```

#### Penjelasan Baris per Baris

**Baris 1:**
```python
import time
```
- `import` adalah kata kunci untuk **mengimpor modul** (pustaka/kumpulan fungsi) dari Python.
- `time` adalah modul bawaan Python yang berisi fungsi-fungsi terkait waktu.
- Setelah di-import, kita bisa menggunakan semua fungsi di dalam modul `time`.

**Baris 2:**
```python
start_time = time.time()
```
- `time.time()` mengembalikan waktu dalam bentuk **timestamp** (jumlah detik sejak 1 Januari 1970, disebut *Unix epoch*).
- Nilai waktu tersebut disimpan ke variabel `start_time`.
- Ini berguna untuk mengukur berapa lama program berjalan.

**Baris 4-6:**
```python
print("Hello")
print("World")
print("Hello World")
```
- Tiga perintah `print()` dijalankan **secara berurutan dari atas ke bawah**.
- Baris 4 dijalankan dulu, baru baris 5, baru baris 6.
- Ini membuktikan bahwa alur program Python adalah **top-to-bottom** (dari atas ke bawah).

**Baris 8:**
```python
print("Halo Chantiiek")
```
- Menampilkan teks `"Halo Chantiiek"` ke layar.

**Baris 9:**
```python
# ini adalah comment
```
- Tanda `#` menandakan **single-line comment** (komentar satu baris).
- Comment **tidak dijalankan** oleh Python. Comment hanya untuk catatan programmer.

**Baris 10:**
```python
a = 10 # ini adalah comment juga
```
- `a = 10` adalah **assignment** (penugasan) yang menyimpan nilai `10` ke variabel `a`.
- `# ini adalah comment juga` adalah komentar di akhir baris.

**Baris 11-13:**
```python
"""ada apa dengan
ucup dan otong si ganteng
dalam comment multiline"""
```
- Ini adalah **multiline comment** menggunakan tanda kutip tiga (`"""`).
- Teks di dalamnya bisa memakan beberapa baris dan **tidak dijalankan** oleh Python.

**Baris 14:**
```python
print(a)
```
- Menampilkan nilai dari variabel `a`, yaitu `10`.

**Baris 15:**
```python
print(time.time() - start_time, "detik")
```
- `time.time() - start_time` menghitung **selisih waktu** antara waktu sekarang dan waktu saat program mulai.
- Hasilnya adalah berapa detik program berjalan.
- Output contoh: `0.0012345314025878906 detik`.

**Baris 16-19 (komentar):**
```python
# kita bisa mengcompile python ke
# yang namanya bytecode
# cara mengcompile, buka terminal dan tuliskan
# python -m py_compile Main.py
```
- Komentar yang menjelaskan bahwa Python bisa di-compile ke **bytecode**.
- Perintah untuk compile: `python -m py_compile Main.py`.

### File: `Test.py`

```python
print("Apa Kabar my friend?")
```
- File terpisah yang hanya mencetak satu baris teks.
- Ini menunjukkan bahwa **setiap file `.py` adalah program independen** yang bisa dijalankan sendiri-sendiri.
- Untuk menjalankannya: `python Test.py`

## Analogi

Bayangkan kamu **memasak di dapur**:
1. `import time` = mengambil **timer** dari laci.
2. `start_time = time.time()` = **menyalakan timer** sebelum mulai memasak.
3. `print("Hello")` = langkah pertama memasak, misalnya mengambil bahan.
4. `print("World")` = langkah kedua, mencuci bahan.
5. `print("Hello World")` = langkah ketiga, memasak.
6. Comment (`#`) = **catatan resep** yang tidak kamu ikuti saat memasak, hanya untuk referensi.
7. `print(time.time() - start_time, "detik")` = **mematikan timer** untuk melihat berapa lama memasak.

**Intinya:** Program Python dijalankan **satu per satu dari atas ke bawah**, seperti resep masakan yang diikuti langkah demi langkah.

## Tabel Alur Eksekusi

| Urutan | Baris Kode | Aksi |
|--------|-----------|------|
| 1 | `import time` | Mengimpor modul waktu |
| 2 | `start_time = time.time()` | Mencatat waktu mulai |
| 3 | `print("Hello")` | Cetak "Hello" |
| 4 | `print("World")` | Cetak "World" |
| 5 | `print("Hello World")` | Cetak "Hello World" |
| 6 | `print("Halo Chantiiek")` | Cetak "Halo Chantiiek" |
| 7 | `a = 10` | Simpan nilai 10 ke variabel a |
| 8 | `print(a)` | Cetak nilai a (10) |
| 9 | `print(...)` | Cetak durasi waktu eksekusi |

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi alur program Python |
| `Test.py` | File tambahan, program sederhana independen |
