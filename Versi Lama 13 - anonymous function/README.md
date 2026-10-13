# BAB 1 - Versi Lama 13: Anonymous Function (Lambda)

## Apa yang Dipelajari

- Membuat fungsi biasa dengan `def`
- Membuat **anonymous function** (fungsi tanpa nama) dengan `lambda`
- Perbedaan `def` vs `lambda`
- Konsep `map()` dan `filter()` bersama `lambda`

---

## Penjelasan Kode

### File: `lambda.py`

#### 1. Fungsi Biasa dengan `def`

```python
def jumlah(a, b):
    c = a + b
    return c

hasil = jumlah(4, 5)
```

| Elemen | Penjelasan |
|--------|------------|
| `def jumlah(a, b)` | Mendefinisikan fungsi bernama `jumlah` dengan 2 parameter |
| `c = a + b` | Menjumlahkan `a` dan `b`, hasilnya disimpan di variabel `c` |
| `return c` | Mengembalikan nilai `c` ke pemanggil fungsi |
| `jumlah(4, 5)` | Memanggil fungsi `jumlah` dengan argumen 4 dan 5 → hasilnya 9 |

#### 2. Anonymous Function dengan `lambda`

```python
kali = lambda x, y: x * y
hasil = kali(3, 4)
print(hasil)  # Output: 12
```

| Elemen | Penjelasan |
|--------|------------|
| `lambda` | Kata kunci untuk membuat fungsi anonim (tanpa nama) |
| `x, y` | Parameter input |
| `x * y` | **Satu ekspresi** yang akan dihitung dan dikembalikan otomatis |
| `kali = lambda...` | Fungsi lambda disimpan dalam variabel `kali` supaya bisa dipanggil |
| `kali(3, 4)` | Memanggil fungsi → 3 × 4 = 12 |

#### Perbandingan `def` vs `lambda`

| Aspek | `def` | `lambda` |
|-------|-------|----------|
| Nama | Wajib ada nama fungsi | Tidak punya nama (anonim) |
| Baris kode | Bisa banyak baris | Hanya **satu ekspresi** |
| `return` | Ditulis manual | **Otomatis** mengembalikan hasil ekspresi |
| Penggunaan | Untuk fungsi kompleks | Untuk fungsi singkat/sederhana |

---

## Lanjutan: `map()` dan `filter()` dengan `lambda`

Meskipun tidak ada di file ini, topik lambda biasanya dipelajari bersama `map` dan `filter`:

```python
# map() → menerapkan fungsi ke SETIAP elemen list
angka = [1, 2, 3, 4]
kuadrat = list(map(lambda x: x ** 2, angka))
print(kuadrat)  # Output: [1, 4, 9, 16]

# filter() → menyaring elemen berdasarkan kondisi
genap = list(filter(lambda x: x % 2 == 0, angka))
print(genap)  # Output: [2, 4]
```

| Fungsi | Cara Kerja |
|--------|-----------|
| `map(fungsi, iterable)` | Jalankan `fungsi` untuk tiap elemen, kumpulkan hasilnya |
| `filter(fungsi, iterable)` | Simpan elemen yang menghasilkan `True` dari `fungsi` |

---

## Analogi

### Anonymous Function (lambda)

Bayangkan kamu sedang di **warung nasi**:

- **`def`** = Kamu menulis **resep lengkap** di buku resep (nama resep, bahan, langkah memasak). Kamu bisa kapan saja membuka buku dan mengikuti resepnya.
- **`lambda`** = Kamu langsung **membuat pesanan tanpa nama** ke penjual: "Pak, nasi goreng telur!" — singkat, langsung jadi, tidak perlu nama resep.

### `map()` dan `filter()`

- **`map()`** = Kamu punya **10 bungkus kopi** dan kamu minta toko **menambahkan gula ke semua** bungkus. Semua bungkus diproses satu per satu.
- **`filter()`** = Kamu punya **10 butir telur** dan kamu hanya ingin **mengambil yang bagus** (tidak retak). Yang retak dibuang.
