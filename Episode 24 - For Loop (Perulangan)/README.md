# BAB 4 - For Loop (Perulangan)

## Apa yang Dipelajari

- Perulangan `for` untuk mengulang aksi beberapa kali
- Menggunakan `for` dengan **list** (kumpulan data)
- Fungsi `range()` untuk membuat deret angka
- `range(stop)` dan `range(start, stop)`
- Melooping karakter dalam **string**

---

## Penjelasan Kode

### 1. For Loop dengan List

```python
angka2_list = [0,2,4,8,10]
print(angka2_list)

for i in angka2_list:
	print(f"i sekarang -> {i}")
```

| Komponen | Penjelasan |
|---|---|
| `angka2_list` | List berisi angka: `[0, 2, 4, 8, 10]` |
| `for i in angka2_list:` | Untuk setiap elemen di dalam list, simpan di variabel `i`, lalu jalankan blok di bawahnya |
| `i` | Variabel sementara (iterator) yang berisi elemen list saat ini |

**Output:**
```
[0, 2, 4, 8, 10]
i sekarang -> 0
i sekarang -> 2
i sekarang -> 4
i sekarang -> 8
i sekarang -> 10
```

---

### 2. For Loop dengan `range(5)`

```python
angka2_range = range(5)

for i in angka2_range:
	print(f"i sekarang -> {i}")
```

| Komponen | Penjelasan |
|---|---|
| `range(5)` | Membuat deret angka dari **0** sampai **4** (total 5 angka) |
| `i` | Variabel iterator |

> **Penting:** `range(5)` menghasilkan `[0, 1, 2, 3, 4]`, bukan `[1, 2, 3, 4, 5]`. Python selalu mulai dari 0 dan tidak termasuk angka terakhir.

**Output:**
```
i sekarang -> 0
i sekarang -> 1
i sekarang -> 2
i sekarang -> 3
i sekarang -> 4
```

---

### 3. For Loop dengan `range(1, 10)`

```python
angka2_range = range(1,10)

for i in angka2_range:
	print(f"i sekarang -> {i}")
```

| Komponen | Penjelasan |
|---|---|
| `range(1, 10)` | Deret angka dari **1** sampai **9** (10 tidak termasuk) |

**Output:**
```
i sekarang -> 1
i sekarang -> 2
...
i sekarang -> 9
```

---

### 4. For Loop dengan String

```python
data_str = "saya ganteng abiees"

for huruf in data_str:
	print(huruf)
```

String diperlakukan seperti list of karakter. Setiap iterasi mengambil **satu karakter** dan mencetaknya.

**Output:**
```
s
a
y
a
 
g
a
n
t
e
n
g
...
```

---

## Referensi `range()`

| Sintaks | Hasil | Keterangan |
|---|---|---|
| `range(5)` | 0, 1, 2, 3, 4 | Mulai dari 0, sampai sebelum 5 |
| `range(1, 5)` | 1, 2, 3, 4 | Mulai dari 1, sampai sebelum 5 |
| `range(0, 10, 2)` | 0, 2, 4, 6, 8 | Mulai 0, loncat 2, sampai sebelum 10 |
| `range(5, 0, -1)` | 5, 4, 3, 2, 1 | Mundur dari 5 ke 1 |

---

## Analogi

Bayangkan kamu sedang makan cilok satu per satu dari piring:

- Piringmu berisi 5 cilok → seperti `range(5)`
- Kamu mengambil **satu per satu** dari awal sampai habis
- Setiap kali mengambil, kamu bilang: "Cilok nomor 1 sedang saya makan" → seperti `print(f"i sekarang -> {i}")`

---

## Tips

- `for` sangat berguna saat kamu tahu **berapa kali** ingin mengulang.
- Gunakan `range()` dengan 3 parameter: `range(start, stop, step)` untuk kontrol lebih.
- Variabel iterator (`i`, `huruf`, dll) boleh dinamai apa saja.
