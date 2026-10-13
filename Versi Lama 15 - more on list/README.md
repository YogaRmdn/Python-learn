# BAB 3 - Versi Lama 15: More on List (Metode Lanjutan List)

## Apa yang Dipelajari

- Membuat list dan mencetak isinya
- Metode **menambah data**: `append()`, `extend()`, `insert()`
- Metode **menghitung**: `count()`
- Metode **menghapus data**: `remove()`
- Metode **membalik**: `reverse()`
- Metode **menyalin**: `copy()`

---

## Penjelasan Kode

### File: `morelist.py`

#### 1. Membuat List

```python
Barang = ['kunci', 'ember', 'jaket', 'ban', 'mobil']
print(Barang)
# Output: ['kunci', 'ember', 'jaket', 'ban', 'mobil']
```

List adalah kumpulan data yang **有序** (berurutan) dan **bisa diubah** (mutable).

#### 2. `append()` — Menambah Satu Elemen di Akhir

```python
Barang.append('sepeda')
print(Barang)
# Output: ['kunci', 'ember', 'jaket', 'ban', 'mobil', 'sepeda']
```

| | |
|-|-|
| `append()` | Menambah **satu item** di **posisi terakhir** list |

#### 3. `extend()` — Menambah Elemen dari List Lain

```python
Barang.extend('dompet')
print(Barang)
```

**PENTING:** Karena argumennya adalah string `'dompet'` (bukan list), `extend()` memecah string per huruf:

```
Output: [..., 's', 'e', 'p', 'e', 'd', 'a', 'd', 'o', 'm', 'p', 'e', 't']
```

Jika ingin menambah satu kata, gunakan `extend(['dompet'])` dengan list.

#### 4. `insert()` — Menambah di Posisi Tertentu

```python
Barang.insert(3, 'sepeda')
print(Barang)
```

| Parameter | Penjelasan |
|-----------|-----------|
| `3` | Posisi indeks ke-3 (hitung dari 0) |
| `'sepeda'` | Elemen yang akan disisipkan |

#### 5. `count()` — Menghitung Kemunculan

```python
jumlahSepeda = Barang.count('sepeda')
print("Jumlah sepeda adalah:", jumlahSepeda)
```

Menghitung berapa kali `'sepeda'` muncul dalam list.

#### 6. `remove()` — Menghapus Elemen Pertama yang Cocok

```python
Barang.remove('sepeda')
print(Barang)
```

Menghapus **hanya kemunculan pertama** `'sepeda'` dari list.

#### 7. `reverse()` — Membalik Urutan List

```python
Barang.reverse()
print(Barang)
```

Membalik urutan elemen secara **in-place** (langsung mengubah list asli).

#### 8. `copy()` — Menyalin List (Shallow Copy)

```python
Stuff = Barang.copy()
Stuff.append('gelas')
print(Stuff)   # ← ada 'gelas'
print(Barang)  # ← TIDAK ada 'gelas'
```

| Elemen | Penjelasan |
|--------|-----------|
| `Barang.copy()` | Membuat **salinan baru** dari `Barang` ke variabel `Stuff` |
| `Stuff.append('gelas')` | Menambah `'gelas'` ke `Stuff` — **tidak mempengaruhi** `Barang` |

Tanpa `copy()`, `Stuff = Barang` hanya akan membuat **referensi** (alias), sehingga perubahan di `Stuff` juga mengubah `Barang`.

---

## Ringkasan Metode List

| Metode | Fungsi | Mengubah Asli? |
|--------|--------|----------------|
| `append(x)` | Tambah `x` di akhir | Ya |
| `extend(iterable)` | Tambah semua elemen dari iterable | Ya |
| `insert(i, x)` | Sisipkan `x` di indeks `i` | Ya |
| `count(x)` | Hitung kemunculan `x` | Tidak |
| `remove(x)` | Hapus kemunculan pertama `x` | Ya |
| `reverse()` | Balik urutan list | Ya |
| `copy()` | Buat salinan baru | Tidak |

---

## Analogi

Bayangkan kamu punya **daftar belanja** di kertas:

- **`append()`** = Kamu menulis **satu item baru** di **paling bawah** daftar.
- **`extend()`** = Kamu menempelkan **seluruh daftar belanja dari kertas lain** di bawah daftarmu.
- **`insert(3, x)`** = Kamu **menyisipkan** item baru di **baris ke-3** daftar, baris di bawahnya bergeser ke bawah.
- **`count()`** = Kamu **menghitung** berapa kali "telur" muncul di daftar.
- **`remove()`** = Kamu **mencoret** item pertama yang namanya "telur" dari daftar.
- **`reverse()`** = Kamu **membalik kertas** dari bawah ke atas.
- **`copy()`** = Kamu **fotokopi** daftar belanja. Tulisan di fotokopi tidak mempengaruhi daftar asli.
