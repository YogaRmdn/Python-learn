# BAB 5 - If, Elif, Else (Percabangan)

## Apa yang Dipelajari

- Percabangan `if`, `elif`, `else`
- Operator perbandingan: `==`, `is`, `is not`
- Kondisi ganda (range nilai)
- Operator logika: `in`, `not in`
- Mengecek apakah sebuah karakter ada di dalam string

---

## Penjelasan Kode

### File: `if elif else.py`

#### 1. Percabangan Dasar dengan `if`

```python
nilai = 50

if nilai == 75:
    print("nilai anda:", nilai)
```

- `nilai = 50` → menyimpan angka 50.
- `if nilai == 75` → "jika nilai **sama dengan** 75".
- Karena `50 != 75`, kode di dalam `if` **tidak dijalankan**.
- `==` adalah operator **equality** (cek kesamaan), bukan penugasan.

---

#### 2. Operator `is`

```python
if nilai is 60:
    print("nilai anda:", nilai)
```

- `is` membandingkan **identitas objek** (apakah benar-benar objek yang sama).
- Untuk angka kecil, `is` dan `==` sering menghasilkan hal yang sama.
- **Catatan:** Sebaiknya gunakan `==` untuk membandingkan nilai, karena `is` lebih untuk membandingkan objek.

---

#### 3. Operator `is not`

```python
if nilai is not 60:
    print("nilai anda bukan: 60")
```

- `is not` berarti "bukan".
- Karena `50 bukan 60`, kondisi ini **benar** → `"nilai anda bukan: 60"` ditampilkan.

---

#### 4. Percabangan dengan `elif` (Range Nilai)

```python
nilai = 65

if 80 <= nilai <= 100:
    print("nilai anda adalah A")
elif 70 <= nilai < 80:
    print("nilai anda adalah B")
elif 60 <= nilai < 70:
    print("nilai anda adalah C")
elif 50 <= nilai < 60:
    print("nilai anda adalah T, lakukan perbaikan")
else:
    print("maaf anda tidak lulus mata kuliah ini")
```

**Cara kerja:**
1. Cek `80 <= 65 <= 100` → **False** (65 tidak di atas 80)
2. Cek `70 <= 65 < 80` → **False** (65 tidak di atas 70)
3. Cek `60 <= 65 < 70` → **True** → `"nilai anda adalah C"` ditampilkan
4. `elif` dan `else` setelahnya **dilewati**

| Nilai | Grade |
|-------|-------|
| 80 - 100 | A |
| 70 - 79 | B |
| 60 - 69 | C |
| 50 - 59 | T (perlu perbaikan) |
| Di bawah 50 | Tidak lulus |

---

#### 5. Operator `in` untuk List dan String

```python
gorengan = ["bakwan", "cireng", "bala-bala", "gehu", "combro", "pisang goreng", "pukis", "risoles"]
beli = "sepatu"

if beli in gorengan:
    print('Mamang bilang, " ya, saya jual', beli, '"')
```

- `beli in gorengan` mengecek apakah nilai `"sepatu"` **ada di dalam list** `gorengan`.
- Karena `"sepatu"` tidak ada di list → kondisi **False** → tidak ditampilkan.

---

#### 6. Operator `not in`

```python
if not beli in gorengan:
    print('"saya gak jual', beli, '"')
```

- `not beli in gorengan` = "sepatu **tidak ada** di gorengan" → **True**.
- Hasil: `"saya gak jual sepatu"`.

---

#### 7. Mengecek Karakter dalam String

```python
karakter = "z"
if karakter in beli:
    print("ada", karakter, "di", beli)
else:
    print("tidak ada", karakter, "di", beli)
```

- `"z" in "sepatu"` → cek apakah huruf `z` ada di kata `"sepatu"` → **False**.
- Hasil: `"tidak ada z di sepatu"`.

---

## Ringkasan Operator Perbandingan

| Operator | Arti | Contoh | Hasil |
|----------|------|--------|-------|
| `==` | Sama dengan | `5 == 5` | `True` |
| `!=` | Tidak sama dengan | `5 != 3` | `True` |
| `>` | Lebih besar | `5 > 3` | `True` |
| `<` | Lebih kecil | `5 < 3` | `False` |
| `>=` | Lebih besar atau sama | `5 >= 5` | `True` |
| `<=` | Lebih kecil atau sama | `5 <= 3` | `False` |
| `is` | Adalah (identitas) | `a is b` | tergantung objek |
| `is not` | Bukan | `a is not b` | tergantung objek |
| `in` | Ada di dalam | `"a" in "abc"` | `True` |
| `not in` | Tidak ada di dalam | `"z" in "abc"` | `False` |

---

## Analogi

Bayangkan kamu sedang **memilih jurusan** berdasarkan nilai:
- Nilai 90 → Masuk jurusan A (kedokteran).
- Nilai 75 → Masuk jurusan B (teknik).
- Nilai 65 → Masuk jurusan C (ekonomi).
- Nilai 55 → Masuk jurusan T (remedial).
- Di bawah 50 → Maaf, tidak diterima.

Dan ketika di warung:
- `if "bakwan" in gorengan` → "Ada bakwan, mau beli?"
- `if "sepatu" in gorengan` → "Kok sepatu di warung gorengan? 😄"

---

## Tips untuk Pemula

- Gunakan `==` untuk membandingkan **nilai**, bukan `is`.
- `elif` bisa ditulis sebanyak yang dibutuhkan.
- `else` selalu di posisi **terakhir** sebagai "jika tidak ada kondisi yang cocok".
- Indentasi (spasi di awal baris) **sangat penting** di Python. Gunakan 4 spasi atau 1 tab.
