# BAB 11 - Operasi Pada List 2

## Apa yang Dipelajari

- Menghitung kemunculan elemen dengan `count()`
- Mencari posisi elemen dengan `index()`
- Mengurutkan list dengan `sort()`
- Membalik urutan list dengan `reverse()`

---

## Penjelasan Kode

### Data Awal

```python
data_angka = [1,5,1,4,3,2,4,3,2,3,7,8,9,0]
print(f"data angka = \n{data_angka}")
```

**Output:** `[1, 5, 1, 4, 3, 2, 4, 3, 2, 3, 7, 8, 9, 0]`

---

### count() — Menghitung Kemunculan

```python
jumlah_data_4 = data_angka.count(4)
jumlah_data_3 = data_angka.count(3)

print(f"jumlah angka 4 = {jumlah_data_4}")
print(f"jumlah angka 3 = {jumlah_data_3}")
```

| Komponen | Penjelasan |
|---|---|
| `count(4)` | Menghitung **berapa kali** angka 4 muncul dalam list |

**Output:**
```
jumlah angka 4 = 2
jumlah angka 3 = 3
```

---

### index() — Mencari Posisi Elemen

```python
data = ["Ucup","Otong","Dudung","Ujang"]
print(f"data = {data}")

index_dudung = data.index("Dudung")
index_ujang = data.index("Ujang")
print(f"index si Dudung = {index_dudung}")
print(f"index si Ujang = {index_ujang}")
```

| Komponen | Penjelasan |
|---|---|
| `index("Dudung")` | Mengembalikan **index** dari `"Dudung"` |

**Output:**
```
index si Dudung = 2
index si Ujang = 3
```

> **Catatan:** `index()` hanya mengembalikan index **pertama** kemunculan. Jika ada duplikat, hanya yang pertama yang dikembalikan.

---

### sort() — Mengurutkan List

```python
print(f"data angka sebelum sort = \n{data_angka}")
data_angka.sort()
print(f"data angka sort = \n{data_angka}")
```

`sort()` mengurutkan list **di tempat** (tidak membuat list baru).

**Output:**
```
data angka sebelum sort =
[1, 5, 1, 4, 3, 2, 4, 3, 2, 3, 7, 8, 9, 0]
data angka sort =
[0, 1, 1, 2, 2, 3, 3, 3, 4, 4, 5, 7, 8, 9]
```

---

### sort() pada List String

```python
data = ["Ucup","Otong","Dudung","Ujang"]
data.sort()
print(f"data sort = {data}")
```

List string juga bisa diurutkan (berdasarkan **urutan alfabet/huruf**).

---

### reverse() — Membalik Urutan

```python
data_angka.reverse()
data.reverse()
print(f"data di reverse = \n{data_angka} \n{data}")
```

`reverse()` membalik urutan elemen **di tempat**.

**Output:**
```
data di reverse =
[9, 8, 7, 5, 4, 4, 3, 3, 3, 2, 2, 1, 1, 0]
['Ujang', 'Dudung', 'Otong', 'Ucup']
```

---

## Ringkasan

| Metode | Fungsi | Mengubah Asli? | Mengembalikan? |
|---|---|---|---|
| `count(x)` | Hitung kemunculan x | Tidak | Jumlah (int) |
| `index(x)` | Cari index x | Tidak | Index (int) |
| `sort()` | Urutkan list | **Ya** | Tidak ada (None) |
| `reverse()` | Balik urutan list | **Ya** | Tidak ada (None) |

---

## Analogi

Bayangkan kamu mengurus **kartu perpustakaan**:

- **count()**: "Berapa buku penulis `Andi` yang saya pinjam?" → menghitung
- **index()**: "Buku `Laskar Pelangi` ada di posisi keberapa?" → mencari posisi
- **sort()**: "Urutkan semua buku berdasarkan abjad" → mengurutkan
- **reverse()**: "Balik urutan buku, dari yang terakhir ke yang pertama" → membalik

---

## Tips

1. `sort()` dan `reverse()` mengubah list **secara langsung** (in-place). Jika ingin menyimpan salinan, gunakan `copy()` terlebih dahulu.
2. `sort()` bisa menerima parameter `reverse=True` untuk mengurutkan dari besar ke kecil.
3. Jika elemen tidak ditemukan, `index()` akan menghasilkan **error** `ValueError`.
