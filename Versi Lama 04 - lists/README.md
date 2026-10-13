# BAB 4 - Lists (Daftar)

## Apa yang Dipelajari

- Membuat list (daftar) di Python
- Mengakses elemen list dengan indexing
- Negative index untuk mengakses dari belakang
- Slicing (memotong list)
- Menggabungkan list
- Mengubah isi list
- Menyalin list
- List multidimensi (list dalam list)
- Method `append()` untuk menambah elemen
- Fungsi `len()` untuk mengetahui panjang list

---

## Penjelasan Kode

### File: `lists.py`

#### 1. Membuat List

```python
Data = [1, 4, 9, 16, 25, 36, 49, 64]
```

- **List** adalah kumpulan data yang diapit tanda kurung siku `[...]`.
- Setiap elemen dipisahkan koma `,`.
- Elemen bisa berupa angka, teks, atau tipe data lainnya.
- Di sini `Data` berisi 8 angka.

---

#### 2. Mengakses Elemen dengan Indexing

```python
Subdata1 = Data[3]
Subdata2 = Data[-3]
```

| Kode | Arti | Nilai |
|------|------|-------|
| `Data[3]` | Ambil elemen indeks ke-3 (ke-4 dari awal) | `16` |
| `Data[-3]` | Ambil elemen ke-3 dari belakang | `36` |

> **Ingat:** Index dimulai dari `0`. Jadi `Data[0]` = `1`, `Data[1]` = `4`, dst.

---

#### 3. Slicing (Memotong List)

```python
Subdata3 = Data[2:4]
Subdata4 = Data[:4]
```

| Kode | Arti | Hasil |
|------|------|-------|
| `Data[2:4]` | Dari indeks 2 sampai 3 (4 tidak termasuk) | `[9, 16]` |
| `Data[:4]` | Dari awal sampai indeks 3 | `[1, 4, 9, 16]` |

> Slicing selalu **tidak termasuk** indeks terakhir. `Data[2:4]` hanya mengambil indeks 2 dan 3.

---

#### 4. Menggabungkan List (Concatenation)

```python
Data2 = [100, 200, 300, 400, 500, 600, 700, 800]
Data3 = Data + Data2
```

- `Data + Data2` menggabungkan dua list jadi satu.
- `Data3` berisi semua elemen `Data` diikuti semua elemen `Data2`.

---

#### 5. Mengubah Isi List

```python
Data[4] = 87
```

- Mengganti elemen di indeks `4` (yang awalnya `25`) menjadi `87`.
- List di Python **bisa diubah** (mutable).

---

#### 6. Menyalin List

```python
a = Data[:]
a[7] = 87
```

- `Data[:]` membuat **salinan** dari seluruh list. Bukan referensi, tapi copy baru.
- Mengubah `a` **tidak** akan mempengaruhi `Data` asli.

> **Perbedaan `a = Data` vs `a = Data[:]`:**
> - `a = Data` → `a` dan `Data` menunjuk ke list yang sama (ubah satu, yang lain ikut berubah).
> - `a = Data[:]` → `a` adalah salinan baru (ubah satu, yang lain tetap).

---

#### 7. Mengubah dengan Slicing

```python
Data[3:5] = [11, 12]
```

- Mengganti elemen indeks 3 dan 4 sekaligus dengan nilai baru `[11, 12]`.
- Slicing bisa digunakan untuk **mengganti beberapa sekaligus**.

---

#### 8. List dalam List (Multidimensi)

```python
x = [Data, Data2]
```

- `x` adalah list yang berisi **dua list lain** di dalamnya.
- `x[0]` = `Data`, `x[1]` = `Data2`.

---

#### 9. Mengakses Elemen dalam List Multidimensi

```python
y = x[1][4]
```

- `x[1]` = `Data2` = `[100, 200, 300, 400, 500, 600, 700, 800]`
- `x[1][4]` = elemen ke-4 dari `Data2` = `500`
- Seperti **koordinat**: baris dulu, lalu kolom.

---

#### 10. Method `append()` dan Fungsi `len()`

```python
Data.append(30)
panjang_list = len(Data)
print(Data)
print(panjang_list)
```

- `Data.append(30)` → menambahkan `30` di **akhir** list.
- `len(Data)` → menghitung **jumlah elemen** dalam list.
- `print(Data)` → menampilkan seluruh isi list.
- `print(panjang_list)` → menampilkan jumlah elemen.

---

## Ringkasan Operasi List

| Operasi | Kode | Penjelasan |
|---------|------|------------|
| Akses | `Data[i]` | Ambil elemen indeks ke-i |
| Negative index | `Data[-i]` | Ambil elemen ke-i dari belakang |
| Slicing | `Data[2:5]` | Ambil dari indeks 2 sampai 4 |
| Concat | `Data + Data2` | Gabungkan dua list |
| Ubah | `Data[i] = x` | Ganti elemen indeks ke-i |
| Salin | `a = Data[:]` | Buat salinan list |
| Append | `Data.append(x)` | Tambah elemen di akhir |
| Panjang | `len(Data)` | Jumlah elemen |

---

## Analogi

Bayangkan list adalah **rak sepatu**:
- Setiap pasang sepatu punya **nomor slot** (index). Slot pertama bernomor `0`.
- `Data[0]` = sepatu di slot pertama.
- `Data[-1]` = sepatu di slot terakhir.
- `Data.append(x)` = menaruh sepatu baru di slot paling ujung.
- `Data[:]` = membuat **daftar salinan** seluruh sepatu.
- `x = [Data, Data2]` = dua rak sepatu ditaruh di dalam rak yang lebih besar.

---

## Tips untuk Pemula

- Index Python selalu mulai dari **0**, bukan 1.
- Slicing `Data[2:5]` **tidak termasuk** indeks 5 (hanya 2, 3, 4).
- Gunakan `append()` untuk menambah elemen, **bukan** `+` (kecuali untuk menggabungkan dua list).
- Hati-hati saat menyalin list: gunakan `[:]` atau `.copy()` agar perubahan tidak saling mempengaruhi.
