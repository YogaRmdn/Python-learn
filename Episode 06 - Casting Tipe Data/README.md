# BAB 5 - Casting Tipe Data

## Apa yang Dipelajari

- Apa itu casting (konversi tipe data)
- Fungsi casting: `int()`, `float()`, `str()`, `bool()`
- Konversi antar tipe data: integer, float, string, boolean
- Aturan dan special case saat casting

## Penjelasan Kode

```python
# Kita belajar Casting
# merubah dari satu tipe ke tipe lain
# tipe data = int, float, str, bool

## INTEGER
print("====INTEGER====")
data_int = 9;
print("data = ", data_int, ",type =",type(data_int))

data_float = float(data_int)
data_str   = str(data_int)
data_bool  = bool(data_int) # akan false jika nilai int = 0
print("data = ", data_float, ",type =",type(data_float))
print("data = ", data_str, ",type =",type(data_str))
print("data = ", data_bool, ",type =",type(data_bool))

## FLOAT
print("====FLOAT====")
data_float = 0;
print("data = ", data_float, ",type =",type(data_float))

data_int = int(data_float) # akan dibulatkan ke bawah
data_str   = str(data_float)
data_bool  = bool(data_float) # akan false jika nilai float = 0
print("data = ", data_int, ",type =",type(data_int))
print("data = ", data_str, ",type =",type(data_str))
print("data = ", data_bool, ",type =",type(data_bool))

## BOOLEAN
print("====BOOLEAN====")
data_bool = False;
print("data = ", data_bool, ",type =",type(data_bool))

data_int = int(data_bool) # akan dibulatkan ke bawah
data_str   = str(data_bool)
data_float  = float(data_bool) # akan false jika nilai float = 0
print("data = ", data_int, ",type =",type(data_int))
print("data = ", data_str, ",type =",type(data_str))
print("data = ", data_float, ",type =",type(data_float))

## STRING
print("====STRING====")
data_str = "10";
print("data = ", data_str, ",type =",type(data_str))

data_int    = int(data_str) # string harus angka
data_float  = float(data_str)  # string harus angka
data_bool   = bool(data_str) # false jika string kosong
print("data = ", data_int, ",type =",type(data_int))
print("data = ", data_float, ",type =",type(data_float))
print("data = ", data_bool, ",type =",type(data_bool))
```

### Penjelasan Detail per Bagian

---

#### 1. Casting dari INTEGER

```python
data_int = 9
data_float = float(data_int)   # 9 → 9.0
data_str   = str(data_int)     # 9 → "9"
data_bool  = bool(data_int)    # 9 → True
```

| Asal | Ke | Hasil | Keterangan |
|------|-----|-------|------------|
| `int(9)` → `float()` | float | `9.0` | Ditambah desimal `.0` |
| `int(9)` → `str()` | string | `"9"` | Dibungkus tanda kutip |
| `int(9)` → `bool()` | boolean | `True` | Karena `9 ≠ 0` |

> **Aturan Boolean dari Integer:** Nilai `0` akan menjadi `False`, selain `0` menjadi `True`.

---

#### 2. Casting dari FLOAT

```python
data_float = 0
data_int = int(data_float)     # 0 → 0
data_str   = str(data_float)   # 0 → "0.0"
data_bool  = bool(data_float)  # 0 → False
```

| Asal | Ke | Hasil | Keterangan |
|------|-----|-------|------------|
| `float(0.0)` → `int()` | int | `0` | **Dibulatkan ke bawah** (dipotong desimalnya) |
| `float(0.0)` → `str()` | string | `"0.0"` | Tetap ada `.0` |
| `float(0.0)` → `bool()` | boolean | `False` | Karena `0.0 = 0` |

> **Penting:** `int()` pada float **membuang bagian desimal** (bukan dibulatkan ke atas). Misal: `int(3.9)` = `3`, bukan `4`.

---

#### 3. Casting dari BOOLEAN

```python
data_bool = False
data_int = int(data_bool)      # False → 0
data_str   = str(data_bool)    # False → "False"
data_float  = float(data_bool) # False → 0.0
```

| Asal | Ke | Hasil | Keterangan |
|------|-----|-------|------------|
| `bool(False)` → `int()` | int | `0` | `False = 0` |
| `bool(True)` → `int()` | int | `1` | `True = 1` |
| `bool(False)` → `str()` | string | `"False"` | Teks "False" |
| `bool(False)` → `float()` | float | `0.0` | Mirip seperti `int()` |

---

#### 4. Casting dari STRING

```python
data_str = "10"
data_int    = int(data_str)    # "10" → 10
data_float  = float(data_str)  # "10" → 10.0
data_bool   = bool(data_str)   # "10" → True
```

| Asal | Ke | Hasil | Keterangan |
|------|-----|-------|------------|
| `str("10")` → `int()` | int | `10` | String harus berisi **angka** |
| `str("10")` → `float()` | float | `10.0` | String harus berisi **angka** |
| `str("10")` → `bool()` | boolean | `True` | Karena string tidak kosong |
| `str("")` → `bool()` | boolean | `False` | **String kosong = False** |

> **Peringatan:** Jika string bukan angka (misal `"hello"`), `int("hello")` akan menghasilkan **error**!

## Tabel Ringkasan Casting

| Dari \ Ke | `int()` | `float()` | `str()` | `bool()` |
|-----------|---------|-----------|---------|----------|
| `int(9)` | — | `9.0` | `"9"` | `True` |
| `int(0)` | — | `0.0` | `"0"` | `False` |
| `float(3.9)` | `3` | — | `"3.9"` | `True` |
| `float(0.0)` | `0` | — | `"0.0"` | `False` |
| `bool(True)` | `1` | `1.0` | `"True"` | — |
| `bool(False)` | `0` | `0.0` | `"False"` | — |
| `str("5")` | `5` | `5.0` | — | `True` |
| `str("")` | ❌ Error | ❌ Error | — | `False` |

## Analogi

Bayangkan casting seperti **menukar uang di money changer**:
- Kamu punya **rupiah** (integer) dan mau tukar ke **dolar** (float). Nilainya berubah bentuk tapi tetap mewakili jumlah yang sama.
- `float(9)` = menukar Rp9 ke dolar → $9.0 (tetap nilai yang sama, tapi format beda).
- `int(3.9)` = memotong recehan, jadi hanya ambil bagian utuh saja: `3`.
- `bool(0)` = uang Rp0 = tidak ada uang = `False`.
- `bool(9)` = ada uang = `True`.
- String `"10"` yang di-cast ke `int` = "uang yang tertulis angka 10" → benar-benar jadi angka `10`.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi casting tipe data |
