# BAB 18 - Format String Width and Alignment

## Apa yang Dipelajari

- Width (lebar) pada format string: mengatur jumlah karakter minimum
- Alignment (perataan): rata kanan (`>`), rata kiri (`<`), rata tengah (`^`)
- Multiline string dengan f-string dan triple quotes
- Perbedaan `\n` dan triple quotes untuk baris baru

## Penjelasan Kode

```python
# Width and Multiline

# Data

data_nama = "Ucup Surucup"
data_umur = 17
data_tinggi = 150.1
data_nomor_sepatu = 44
```

---

### 1. String Standard (Tanpa Width)

```python
data_string = f"nama = {data_nama}, umur = {data_umur}, tinggi = {data_tinggi}, sepatu = {data_nomor_sepatu}"
print(5*"="+"Data String"+5*"=")
print(data_string)
```
- Semua data ditampilkan dalam **satu baris** tanpa pengaturan lebar.
- Output: `nama = Ucup Surucup, umur = 17, tinggi = 150.1, sepatu = 44`

---

### 2. Multiline dengan `\n`

```python
data_string = f"nama = {data_nama}, \numur = {data_umur}, \ntinggi = {data_tinggi}, \nsepatu = {data_nomor_sepatu}"
print("\n"+5*"="+"Data String"+5*"=")
print(data_string)
```
- `\n` di dalam f-string membuat **baris baru**.
- Output:
  ```
  nama = Ucup Surucup, 
  umur = 17, 
  tinggi = 150.1, 
  sepatu = 44
  ```

---

### 3. Multiline dengan Triple Quotes

```python
data_string = f"""nama = {data_nama}
umur = {data_umur}
tinggi = {data_tinggi}
sepatu = {data_nomor_sepatu}
"""
print("\n"+5*"="+"Data String"+5*"=")
print(data_string)
```
- **Triple quotes** (`"""..."""`) membuat string **otomatis multi-baris** tanpa perlu `\n`.
- Lebih **rapi dan mudah dibaca**.

---

### 4. Width (Lebar)

```python
data_nama = "Ucup Surucup"
data_tinggi = 105.17
data_string = f"""
nama   = {data_nama:>5}
umur   = {data_umur:>5}
tinggi = {data_tinggi:>5}
sepatu = {data_nomor_sepatu:>5}
"""
print("\n"+5*"="+"Data String"+5*"=")
print(data_string)
```

- `:>5` berarti:
  - `>` = **rata kanan** (alignment)
  - `5` = lebar minimum **5 karakter**

Jika teks lebih panjang dari 5, tetap ditampilkan lengkap (tidak terpotong).

## Alignment

| Syntax | Keterangan | Contoh | Hasil |
|--------|------------|--------|-------|
| `{:>n}` | Rata kanan, lebar n | `f"{'hi':>5}"` | `"   hi"` |
| `{:>5}` | Rata kanan 5 karakter | `f"{123:>5}"` | `"  123"` |
| `{:<n}` | Rata kiri, lebar n | `f"{'hi':<5}"` | `"hi   "` |
| `{:^n}` | Rata tengah, lebar n | `f"{'hi':^5}"` | `" hi "` |
| `{:=n}` | Rata kiri dengan zero-fill | `f"{42:=5}"` | — |

## Analogi

Bayangkan kamu sedang **membuat tabel rapi di Excel**:
- **Width** (`>5`) = Mengatur **lebar kolom** agar semua data sejajar.
- **Alignment** (`>`, `<`, `^`) = Mengatur **posisi teks di dalam sel**: rata kanan, kiri, atau tengah.
- **Triple quotes** (`"""...""")` = Menulis **beberapa baris sekaligus** tanpa perlu menambah `\n` manual.

Seperti saat membuat **tabel data**:
```
nama   = Ucup Surucup
umur   =    17
tinggi = 105.17
sepatu =    44
```
Semua angka **rata kanan** sehingga terlihat rapi dan mudah dibandingkan.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi width dan alignment format string |
