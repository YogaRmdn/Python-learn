# BAB 7 - Operasi Aritmatika

## Apa yang Dipelajari

- 7 operator aritmatika dalam Python: `+`, `-`, `*`, `/`, `%`, `**`, `//`
- Operator precedence (urutan prioritas operasi)
- Penggunaan kurung `()` untuk mengatur prioritas

## Penjelasan Kode

```python
# operasi aritmatika

a = 10
b = 3

# operasi tambah +
hasil = a + b
print(a,'+',b,'=',hasil)

# operasi pengurangan -
hasil = a - b
print(a,'-',b,'=',hasil)

# operasi perkalian *
hasil = a * b
print(a,'*',b,'=',hasil)

# operasi pembagian /
hasil = a / b
print(a,'/',b,'=',hasil)

# operasi eksponen (pangkat) **
hasil = a ** b
print(a,'**',b,'=',hasil)

# operasi modulus %
hasil = a % b
print(a,'%',b,'=',hasil)

# operasi floor division //
hasil = a // b
print(a,'//',b,'=',hasil)

# prioritas operasi, operational precedence
'''
    1. ()
    2. exponen **
    3. perkalian dan teman-teman * / ** % //
    4. pertambahan dan pengurangan + -
'''
x = 3
y = 2
z = 4

hasil = x ** y * (z + x) / y - y % z // x
print(x,'**',y,'*',z,'+',x,'/',y,'-',y,'%',z,'//',x,'=',hasil)

hasil = x + y * z
print(x,'+',y,'*',z,'=',hasil)
# kurung akan mengambil langkah paling pertama
hasil = (x + y) * z 
print('(',x,'+',y,') *',z,'=',hasil)
```

### Penjelasan Operator Aritmatika

Dengan `a = 10` dan `b = 3`:

| Operator | Nama | Contoh | Hasil | Penjelasan |
|----------|------|--------|-------|------------|
| `+` | Penjumlahan | `10 + 3` | `13` | Tambah biasa |
| `-` | Pengurangan | `10 - 3` | `7` | Kurang biasa |
| `*` | Perkalian | `10 * 3` | `30` | Kali biasa |
| `/` | Pembagian | `10 / 3` | `3.3333...` | Selalu menghasilkan **float** |
| `**` | Eksponen (Pangkat) | `10 ** 3` | `1000` | 10 pangkat 3 = 1000 |
| `%` | Modulus (Sisa Bagi) | `10 % 3` | `1` | Sisa bagi 10 ÷ 3 = 1 |
| `//` | Floor Division | `10 // 3` | `3` | Pembagian bulat (dibulatkan ke bawah) |

---

#### Penjelasan Detail Setiap Operator

**`+` Penjumlahan:**
```python
hasil = a + b  # 10 + 3 = 13
```
- Menjumlahkan dua angka.

**`-` Pengurangan:**
```python
hasil = a - b  # 10 - 3 = 7
```
- Mengurangkan dua angka.

**`*` Perkalian:**
```python
hasil = a * b  # 10 * 3 = 30
```
- Mengalikan dua angka.

**`/` Pembagian:**
```python
hasil = a / b  # 10 / 3 = 3.3333...
```
- Hasilnya selalu **float** (desimal), meskipun hasilnya bulat.
- `10 / 2 = 5.0` (bukan `5`).

**`**` Eksponen/Pangkat:**
```python
hasil = a ** b  # 10 ** 3 = 1000
```
- `10 ** 3` artinya 10 pangkat 3 = 10 × 10 × 10 = 1000.

**`%` Modulus (Sisa Bagi):**
```python
hasil = a % b  # 10 % 3 = 1
```
- Sisa dari pembagian `10 ÷ 3`.
- `10 ÷ 3 = 3` sisa `1`, jadi hasilnya `1`.
- Berguna untuk mengecek **ganjil/genap**: `angka % 2 == 0` berarti genap.

**`//` Floor Division (Pembagian Bulat):**
```python
hasil = a // b  # 10 // 3 = 3
```
- Pembagian yang hasilnya **dibulatkan ke bawah** (dipotong desimalnya).
- Sama seperti `int(10 / 3)`.

---

### Operator Precedence (Urutan Prioritas)

```
1. ()              → Kurung paling diprioritaskan
2. **              → Eksponen/pangkat
3. *, /, %, //     → Perkalian, pembagian, modulus, floor division
4. +, -            → Penjumlahan dan pengurangan
```

**Contoh:**
```python
x = 3; y = 2; z = 4

# Tanpa kurung: x + y * z
hasil = x + y * z       # 3 + (2 * 4) = 3 + 8 = 11
print(x,'+',y,'*',z,'=',hasil)   # Output: 3 + 2 * 4 = 11

# Dengan kurung: (x + y) * z
hasil = (x + y) * z     # (3 + 2) * 4 = 5 * 4 = 20
print('(',x,'+',y,') *',z,'=',hasil)  # Output: ( 3 + 2 ) * 4 = 20
```

**Contoh Kompleks:**
```python
hasil = x ** y * (z + x) / y - y % z // x
# Langkah perhitungan:
# 1. Kurung dulu: (z + x) = (4 + 3) = 7
# 2. Pangkat: x ** y = 3 ** 2 = 9
# 3. Kiri ke kanan untuk * / % //:
#    9 * 7 = 63
#    63 / 2 = 31.5
#    y % z = 2 % 4 = 2
#    2 // x = 2 // 3 = 0
# 4. Akhirnya: 31.5 - 0 = 31.5
```

## Analogi

Bayangkan operasi aritmatika seperti **kalkulator di kasir**:
- `+` = Menambah harga barang: Rp10 + Rp3 = Rp13.
- `-` = Diskon: Rp10 - Rp3 = Rp7.
- `*` = Beli banyak: Rp10 × 3 barang = Rp30.
- `/` = Membagi rata: Rp10 dibagi 3 orang = Rp3.33 per orang.
- `%` = Sisa kembalian: Rp10 beli 3, sisa Rp1.
- `//` = Pembagian bulat: Rp10 dibagi 3 orang, masing-masing dapat 3 (tanpa pecahan).
- `**` = Perkalian berulang: 10³ = 10 × 10 × 10 = 1000.

**Prioritas:** Kurung `()` selalu dihitung dulu (seperti aturan "yang di dalam kotak dihitung duluan").

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi operasi aritmatika Python |
