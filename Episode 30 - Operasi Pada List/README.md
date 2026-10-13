# BAB 10 - Operasi Pada List

## Apa yang Dipelajari

- Mengakses elemen list dengan **index** (positif dan negatif)
- Mengetahui panjang list dengan `len()`
- Menambah elemen dengan `insert()` dan `append()`
- Menggabungkan list dengan `extend()`
- Mengubah elemen list
- Menghapus elemen dengan `remove()` dan `pop()`

---

## Penjelasan Kode

### Indexing (Mengakses Elemen)

```python
# index   0(-3)  1(-2)  2(-1)
data = ["Ucup","Otong","Dudung"]
```

```
Index positif:   0         1         2
               "Ucup"   "Otong"  "Dudung"
Index negatif: -3        -2        -1
```

```python
data_0 = data[0]
print(f"data pertama (index 0) = {data_0}")
```

| Komponen | Penjelasan |
|---|---|
| `data[0]` | Mengambil elemen pertama (index 0) |
| `data_0` | Menyimpan hasilnya ke variabel |

**Output:** `data pertama (index 0) = Ucup`

---

```python
data_terakhir = data[-1]
print(f"data terakhir adalah = {data_terakhir}")
```

**Index negatif** menghitung dari belakang: `-1` = terakhir, `-2` = kedua dari belakang, dst.

**Output:** `data terakhir adalah = Dudung`

---

```python
data_ucup = data[-3]
print(f"data ucup = {data_ucup}")
```

`-3` = tiga elemen dari belakang = elemen pertama = `"Ucup"`

---

### Mengetahui Panjang List

```python
panjang_data = len(data)
print(f"panjang data = {panjang_data}")
```

`len()` mengembalikan **jumlah elemen** dalam list.

**Output:** `panjang data = 3`

---

### insert() — Menambah di Posisi Tertentu

```python
data.insert(1,"Asep")
print(f"data sesudah ditambah = \n{data}")
```

| Komponen | Penjelasan |
|---|---|
| `insert(1, "Asep")` | Sisipkan `"Asep"` di **posisi index 1** |
| `\n` | karakter newline (baris baru) |

**Output:**
```
data sesudah ditambah =
['Ucup', 'Asep', 'Otong', 'Dudung']
```

---

### append() — Menambah di Akhir

```python
data.append("Jajang")
print(f"data ditambah lagi =\n{data}")
```

`append()` selalu menambahkan elemen di **posisi terakhir** list.

**Output:**
```
data ditambah lagi =
['Ucup', 'Asep', 'Otong', 'Dudung', 'Jajang']
```

---

### extend() — Menggabungkan Dua List

```python
data_baru = ["Ujang","Usep","Dadang"]
data.extend(data_baru)
print(f"data gabungan =\n{data}")
```

`extend()` menggabungkan elemen dari list lain ke list yang sudah ada.

**Output:**
```
data gabungan =
['Ucup', 'Asep', 'Otong', 'Dudung', 'Jajang', 'Ujang', 'Usep', 'Dadang']
```

---

### Mengubah Elemen

```python
data[2] = "Michael"
print(f"data rubah = \n{data}")
```

`data[2] = "Michael"` mengganti elemen di index 2.

---

### remove() — Menghapus Elemen Tertentu

```python
data.remove("Ujang")
print(f"data remove = \n{data}")
```

`remove()` menghapus elemen berdasarkan **nilai**, bukan index.

> **Perhatian:** `"usep"` ≠ `"Usep"` (Python case-sensitive!). Jika salah huruf, akan error.

---

### pop() — Menghapus Elemen Terakhir

```python
data_akhir = data.pop()
print(f"data akhir = \n{data}")
print(data_akhir)
```

`pop()` menghapus elemen **terakhir** dan **mengembalikannya** ke variabel `data_akhir`.

---

## Ringkasan Operasi List

| Metode | Fungsi | Contoh |
|---|---|---|
| `data[i]` | Akses elemen ke-i | `data[0]` |
| `data[-1]` | Akses dari belakang | `data[-1]` |
| `len(data)` | Jumlah elemen | `len(data)` → 3 |
| `insert(i, x)` | Sisipkan x di posisi i | `data.insert(1,"A")` |
| `append(x)` | Tambah x di akhir | `data.append("B")` |
| `extend(list2)` | Gabungkan list2 | `data.extend(list2)` |
| `data[i] = x` | Ubah elemen ke-i | `data[2] = "X"` |
| `remove(x)` | Hapus elemen x | `data.remove("A")` |
| `pop()` | Hapus & kembalikan elemen terakhir | `data.pop()` |

---

## Analogi

Bayangkan **list** seperti **daftar belanja**:

- **Index**: "Item ke-1 di daftar adalah `apel`"
- **insert(1, "apel")**: Sisipkan `apel` di posisi ke-2 (setelah yang pertama)
- **append("apel")**: Tambah `apel** di paling bawah daftar
- **remove("apel")**: Coret `apel` dari daftar (dimana pun posisinya)
- **pop()**: Ambil item terakhir dari daftar
