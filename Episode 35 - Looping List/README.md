# BAB 15 - Looping List

## Apa yang Dipelajari

- For loop biasa untuk melooping list
- For loop dengan `range()` dan index
- While loop untuk melooping list
- **List comprehension** untuk mencetak atau mengolah data
- `enumerate()` untuk mendapatkan index dan value sekaligus

---

## Penjelasan Kode

### 1. For Loop Biasa

```python
print("For Loop")
kumpulan_angka = [4,3,2,5,6,1]

for angka in kumpulan_angka:
	print(f"angka = {angka}")
```

Setiap iterasi, variabel `angka` berisi elemen list saat ini.

**Output:**
```
angka = 4
angka = 3
angka = 2
angka = 5
angka = 6
angka = 1
```

---

### 2. For Loop dengan String

```python
peserta = ["ucup","otong","dadang","diding","dudung"]

for nama in peserta:
	print(f"nama = {nama}")
```

**Output:**
```
nama = ucup
nama = otong
nama = dadang
nama = diding
nama = dudung
```

---

### 3. For Loop dengan `range()` dan Index

```python
print("\nFor Loop dan range")
kumpulan_angka = [10,5,4,2,6,5]

panjang = len(kumpulan_angka)

for i in range(panjang):
	print(f"angka = {kumpulan_angka[i]}")
```

| Komponen | Penjelasan |
|---|---|
| `len(kumpulan_angka)` | Jumlah elemen = 6 |
| `range(panjang)` | Deret angka 0, 1, 2, 3, 4, 5 |
| `kumpulan_angka[i]` | Mengakses elemen berdasarkan index |

> **Kapan pakai cara ini?** Saat kamu perlu **index** (misal untuk mengubah elemen atau mencetak posisi).

---

### 4. While Loop untuk Melooping List

```python
print("\nWhile loop")
kumpulan_angka = [10,5,4,2,6,5]

panjang = len(kumpulan_angka)
i = 0

while i < panjang:
	print(f"angka = {kumpulan_angka[i]}")
	i += 1
```

| Komponen | Penjelasan |
|---|---|
| `i = 0` | Index dimulai dari 0 |
| `while i < panjang` | Loop selama index masih kurang dari jumlah elemen |
| `i += 1` | Increment index setiap iterasi |

---

### 5. List Comprehension untuk Mencetak

```python
print("\nList Comprehension")
data = ["ucup",1,2,3,"otong"]

[print(f"data={i}") for i in data]
```

List comprehension **bukan hanya untuk membuat list baru** — bisa juga digunakan untuk menjalankan aksi seperti `print()`.

---

### 6. List Comprehension untuk Mengolah Data

```python
angka = [10,5,4,2,6,5]

angka_kuadrat = [i**2 for i in angka]
print(angka_kuadrat)
```

**Output:** `[100, 25, 16, 4, 36, 25]`

Setiap elemen dikuadratkan dan dimasukkan ke list baru.

---

### 7. enumerate() — Index + Value

```python
print("\nEnumerate")
data_list = ["ucup",1,2,3,"otong"]

for index,data in enumerate(data_list):
	print(f"index = {index}, data = {data}")
```

| Komponen | Penjelasan |
|---|---|
| `enumerate(data_list)` | Mengembalikan pasangan **(index, value)** untuk setiap elemen |
| `index` | Variabel untuk index saat ini |
| `data` | Variabel untuk nilai saat ini |

**Output:**
```
index = 0, data = ucup
index = 1, data = 1
index = 2, data = 2
index = 3, data = 3
index = 4, data = otong
```

---

## Perbandingan Cara Looping

| Cara | Kapan Digunakan | Contoh |
|---|---|---|
| `for x in list` | Hanya butuh **nilai** | `for angka in angka_list` |
| `for i in range(len(list))` | Butuh **index** untuk akses | `angka_list[i]` |
| `while` | Loop **kondisional** | Saat jumlah iterasi tidak diketahui |
| `enumerate()` | Butuh **index + nilai** | `for i, val in enumerate(list)` |
| List comprehension | **Membuat list baru** atau aksi ringkas | `[i**2 for i in list]` |

---

## Analogi

Bayangkan kamu memeriksa **lemari baju**:

- **For loop biasa**: Kamu mengambil satu per satu baju dan melihat warnanya
- **For + range**: Kamu melihat nomor hanger + warna baju
- **While loop**: Kamu terus mengambil baju selama hanger masih ada
- **enumerate**: Kamu mencatat: "Hanger 1: baju merah, Hanger 2: baju biru, ..."

---

## Tips

1. `enumerate()` adalah cara paling **Pythonic** untuk mendapatkan index + value.
2. List comprehension sangat **efisien** untuk membuat list baru dari list yang ada.
3. Pilih metode looping sesuai kebutuhan: nilai saja → `for x in list`, nilai + index → `enumerate()`.
