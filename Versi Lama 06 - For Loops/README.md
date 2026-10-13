# BAB 6 - For Loops (Perulangan For)

## Apa yang Dipelajari

- Perulangan `for` dengan iterable (list)
- Perulangan `for` pada string
- Nested loop (for di dalam for)
- Fungsi `len()` di dalam loop

---

## Penjelasan Kode

### File: `forloops.py`

#### 1. For Loop dengan List (Iterable)

```python
gorengan = ['bakwan', 'cireng', 'tahu isi', 'tempe goreng', 'ubi goreng']

for g in gorengan:
    print(g)
    print(len(g))
```

**Cara kerja:**
1. Variabel `g` akan mengambil **satu per satu** elemen dari list `gorengan`.
2. Setiap kali mengambil elemen, kode di dalam blok `for` dijalankan.
3. `len(g)` menghitung panjang teks (jumlah karakter).

| Iterasi | `g` | `len(g)` |
|---------|-----|----------|
| 1 | `'bakwan'` | `6` |
| 2 | `'cireng'` | `6` |
| 3 | `'tahu isi'` | `8` |
| 4 | `'tempe goreng'` | `12` |
| 5 | `'ubi goreng'` | `10` |

---

#### 2. For Loop dengan String

```python
bakwan = 'bakwan'

for i in bakwan:
    print(i)
```

- String juga bisa di-loop! Setiap iterasi, `i` akan mengambil **satu huruf** dari string `'bakwan'`.
- Hasil: huruf `b`, `a`, `k`, `w`, `a`, `n` ditampilkan satu per satu.

---

#### 3. Nested Loop (For di Dalam For)

```python
gorengan = ['bakwan', 'cireng', 'tahu isi', 'tempe goreng', 'ubi goreng']
buah = ['semangka', 'jeruk', 'apel', 'anggur']
sayur = ['kangkung', 'wortel', 'tomat', 'kentang']

Daftar_belanja = [gorengan, buah, sayur]
```

- `Daftar_belanja` adalah **list yang berisi tiga list lain** (gorengan, buah, sayur).

```python
for subDaftarBelanja in Daftar_belanja:
    print(subDaftarBelanja)
    for komponen in subDaftarBelanja:
        print(komponen)
```

**Cara kerja:**
1. **Loop luar**: `subDaftarBelanja` mengambil satu list dari `Daftar_belanja`.
   - Iterasi 1: `subDaftarBelanja` = `['bakwan', 'cireng', ...]`
   - Iterasi 2: `subDaftarBelanja` = `['semangka', 'jeruk', ...]`
   - Iterasi 3: `subDaftarBelanja` = `['kangkung', 'wortel', ...]`

2. **Loop dalam**: Untuk setiap sub-daftar, ambil satu elemen dan cetak.
   - Iterasi 1.1: `komponen` = `'bakwan'`
   - Iterasi 1.2: `komponen` = `'cireng'`
   - ...dst.

---

## Ringkasan

| Konsep | Penjelasan |
|--------|------------|
| `for x in iterable` | Ulangi untuk setiap elemen di dalam iterable |
| List sebagai iterable | Setiap elemen list diambil satu per satu |
| String sebagai iterable | Setiap karakter diambil satu per satu |
| Nested loop | Loop di dalam loop untuk list multidimensi |

---

## Analogi

Bayangkan kamu sedang **berbelanja di pasar**:
- **Loop luar**: Kamu jalan dari satu lapak ke lapak lain.
  - Lapak 1: Gorengan
  - Lapak 2: Buah
  - Lapak 3: Sayur

- **Loop dalam**: Di setiap lapak, kamu lihat satu per satu barang yang dijual.
  - Di lapak gorengan: bakwan, cireng, tahu isi, ...
  - Di lapak buah: semangka, jeruk, apel, ...

---

## Tips untuk Pemula

- `for` di Python otomatis mengambil elemen satu per satu — tidak perlu indeks manual.
- Loop bersarang (nested) berguna untuk memproses **list of lists**.
- Gunakan nama variabel yang deskriptif: `for makanan in daftar_makanan:` lebih jelas dari `for x in y:`.
