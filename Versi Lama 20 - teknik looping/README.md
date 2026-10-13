# BAB 8 - Versi Lama 20: Teknik Looping

## Apa yang Dipelajari

- **`enumerate()`** — looping dengan indeks otomatis
- **`zip()`** — menggabungkan dua list dan looping bersamaan
- **`sorted()`** — looping elemen set secara terurut
- **`dict.items()`** — looping key dan value dictionary
- **`reversed()`** — looping dari belakang ke depan

---

## Penjelasan Kode

### File: `tekniklooping.py`

#### Data Awal

```python
nama_band = ['Payung Teduh', 'Fourtwnty', 'Dialog Dini Hari', 'Mr. Sonjaya', 'Parahyena', 'Syahrini']

kumpulan_lagu = ['Akad', 'Zona Nyaman', 'Rumahku', 'Sang Filsuf', 'Sindoro', 'Jodohku']
```

---

#### 1. `enumerate()` — Looping dengan Indeks

```python
for index, band in enumerate(nama_band):
    print(index, ':', band)
```

**Output:**
```
0 : Payung Teduh
1 : Fourtwnty
2 : Dialog Dini Hari
3 : Mr. Sonjaya
4 : Parahyena
5 : Syahrini
```

| Elemen | Penjelasan |
|--------|-----------|
| `enumerate()` | Mengembalikan pasangan **(indeks, nilai)** untuk setiap elemen |
| `index` | Nomor urut (mulai dari 0) |
| `band` | Nilai elemen pada list |

> Tanpa `enumerate`, kamu harus membuat variabel indeks manual (`for i in range(len(...))`).

---

#### 2. `zip()` — Menggabungkan Dua List

```python
for band, lagu in zip(nama_band, kumpulan_lagu):
    print(band, 'menyanyikan lagu yang berjudul:', lagu)
```

**Output:**
```
Payung Teduh menyanyikan lagu yang berjudul: Akad
Fourtwnty menyanyikan lagu yang berjudul: Zona Nyaman
Dialog Dini Hari menyanyikan lagu yang berjudul: Rumahku
...
```

| Elemen | Penjelasan |
|--------|-----------|
| `zip()` | Menggabungkan dua iterable menjadi **pasangan tuple** per indeks |
| `(band, lagu)` | Unpacking: elemen pertama → `band`, elemen kedua → `lagu` |

```
Payung Teduh  ←→  Akad
Fourtwnty     ←→  Zona Nyaman
Dialog Dini   ←→  Rumahku
...
```

> `zip` berhenti di list **terpendek** jika panjangnya berbeda.

---

#### 3. `sorted()` — Looping Set Secara Terurut

```python
playlist = {'baby baby', 'ada apa dengan cinta', 'cenat-cenut', 'jaran goyang', 'jaran goyang', 'gorgom', 'kuda', 'kucing'}

for lagu in sorted(playlist):
    print(lagu)
```

| Elemen | Penjelasan |
|--------|-----------|
| `set` | Tidak berurutan dan tidak ada duplikat → `"jaran goyang"` hanya muncul sekali |
| `sorted()` | Mengembalikan elemen set dalam **urutan alfabetis** |

> `sorted()` tidak mengubah set asli, hanya mengurutkan untuk keperluan looping.

---

#### 4. `dict.items()` — Looping Key dan Value

```python
playlist2 = {
    'Payung Teduh': 'akad',
    'Fourtwnty': 'Zona Nyaman',
    'Dialog Dini Hari': 'Rumahku',
}

for i, v in playlist2.items():
    print(i, 'lagunya:', v)
```

**Output:**
```
Payung Teduh lagunya: akad
Fourtwnty lagunya: Zona Nyaman
Dialog Dini Hari lagunya: Rumahku
```

| Elemen | Penjelasan |
|--------|-----------|
| `.items()` | Mengembalikan pasangan **(key, value)** sebagai tuple |
| `i` | Key (nama band) |
| `v` | Value (nama lagu) |

**Cara lain looping dictionary:**

| Metode | Yang Didapat |
|--------|-------------|
| `d.keys()` | Hanya key |
| `d.values()` | Hanya value |
| `d.items()` | Key dan value |

---

#### 5. `reversed()` — Looping dari Belakang

```python
for i in reversed(range(1, 10, 1)):
    print(i)
```

**Output:** `9, 8, 7, 6, 5, 4, 3, 2, 1`

| Elemen | Penjelasan |
|--------|-----------|
| `range(1, 10, 1)` | Angka dari 1 sampai 9 (10 tidak termasuk) |
| `reversed()` | Membalik urutan → dari 9 ke 1 |

---

## Ringkasan Teknik Looping

| Teknik | Fungsi | Contoh Kasus |
|--------|--------|-------------|
| `enumerate()` | Dapat indeks + nilai | Nomor urut otomatis |
| `zip()` | Gabungkan 2+ list | Pasangkan nama dengan data |
| `sorted()` | Urutkan sebelum looping | Cetak dalam urutan alfabet |
| `dict.items()` | Looping key-value | Iterasi seluruh isi dictionary |
| `reversed()` | Balik urutan | Hitung mundur |

---

## Analogi

- **`enumerate()`** = Seperti **nomor antrian** di rumah sakit. Kamu tidak perlu menghitung manual, nomor sudah tercetak di kertas (0, 1, 2, ...).

- **`zip()`** = Seperti **menjodohkan** pasangan dansa. Laki-laki dari baris kiri (nama_band), perempuan dari baris kanan (kumpulan_lagu). Masing-masing berpasangan berdasarkan urutan.

- **`sorted()`** = Seperti **menyusun buku di rak** berdasarkan abjad A→Z sebelum kamu mulai membacanya.

- **`dict.items()`** = Seperti **membuka MAP setiap siswa** satu per satu, melihat nama (key) dan nilai ujian (value) di dalamnya.

- **`reversed()`** = Seperti **hitung mundur** saat tahun baru: "3... 2... 1... Selamat Tahun Baru!"
