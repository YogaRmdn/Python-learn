# BAB 2 - Numbers & Math

## Apa yang Dipelajari

- Tipe data angka: **integer** (bilangan bulat) dan **float** (bilangan desimal)
- Operasi matematika dasar di Python
- Cara menampilkan hasil operasi langsung di dalam `print()`

---

## Penjelasan Kode

### File: `numbers.py`

#### 1. Membuat Variabel dengan Berbagai Tipe Angka

```python
a = 5
b = 3
c = 4.0
```

| Variabel | Nilai | Tipe Data | Penjelasan |
|----------|-------|-----------|------------|
| `a` | `5` | `int` (integer) | Bilangan bulat, tanpa desimal |
| `b` | `3` | `int` (integer) | Bilangan bulat, tanpa desimal |
| `c` | `4.0` | `float` | Bilangan desimal (titik sebagai pemisah desimal) |

> **Perbedaan `int` dan `float`:**
> - `5` → integer
> - `5.0` → float
> - Di Python, angka dengan titik desimal otomatis dianggap sebagai float.

---

#### 2. Penjumlahan

```python
# penjumlahan
print("penjumlahan a + b = ", a + b)
```

- `a + b` = `5 + 3` = `8`
- Teks `"penjumlahan a + b = "` dan hasil `8` ditampilkan bersamaan.
- Operator `+` untuk menjumlahkan dua angka.

---

#### 3. Pengurangan

```python
# pengurangan
print("pengurangan a - b = ", a - b)
```

- `a - b` = `5 - 3` = `2`
- Operator `-` untuk mengurangkan.

---

#### 4. Perkalian

```python
# perkalian
print("perkalian a * b = ", a * b)
```

- `a * b` = `5 * 3` = `15`
- Gunakan `*` (bintang) untuk perkalian, bukan `×`.

---

#### 5. Pembagian

```python
# pembagian
print("pembagian a / b = ", a / b)
```

- `a / b` = `5 / 3` = `1.6666666666666667`
- Pembagian dengan `/` selalu menghasilkan **float** (desimal), meskipun hasilnya bulat.

---

## Ringkasan Tipe Data Angka

| Tipe | Contoh | Penjelasan |
|------|--------|------------|
| `int` | `5`, `-3`, `0` | Bilangan bulat |
| `float` | `4.0`, `3.14`, `-0.5` | Bilangan desimal |

---

## Ringkasan Operasi Matematika

| Operasi | Simbol | Contoh | Hasil |
|---------|--------|--------|-------|
| Penjumlahan | `+` | `5 + 3` | `8` |
| Pengurangan | `-` | `5 - 3` | `2` |
| Perkalian | `*` | `5 * 3` | `15` |
| Pembagian | `/` | `5 / 3` | `1.6667` |

---

## Analogi

Bayangkan kamu di **warung**:
- `a = 5` → Ada 5 butir telur di keranjang.
- `b = 3` → Kamu mau beli 3 butir telur lagi.
- `a + b` → Total telur kamu sekarang 8 butir.
- `c = 4.0` → Harga telur per butir Rp 4.000,00 (desimal).

---

## Tips untuk Pemula

- Jika ingin hasil pembagian **bulat** tanpa desimal, gunakan `//` (floor division). Contoh: `5 // 3 = 1`.
- Jika ingin **sisa pembagian**, gunakan `%` (modulus). Contoh: `5 % 3 = 2`.
- Python mengikuti urutan operasi matematika standar: perkalian/pembagian dihitung dulu sebelum penjumlahan/pengurangan.
