# BAB 8 - Latihan Perulangan

## Apa yang Dipelajari

- Membuat pola segitiga dengan loop
- Menggunakan `for` dan `while` untuk membuat pola yang sama
- Operator modulus (`%`) untuk mengecek bilangan ganjil/genap
- Nested `if` dalam loop
- Nested loop dengan `break` dan `continue`

---

## Penjelasan Kode

### 1. Segitiga dengan For Loop

```python
sisi = 10
count = 1

for i in range(sisi):
	print("*"*count)
	count += 1
```

| Komponen | Penjelasan |
|---|---|
| `sisi = 10` | Tinggi segitiga (jumlah baris) |
| `count = 1` | Jumlah bintang per baris, dimulai dari 1 |
| `"*"*count` | Mengulang karakter `*` sebanyak `count` kali |
| `count += 1` | Setiap baris, jumlah bintang bertambah 1 |

**Output:**
```
*
**
***
****
*****
******
*******
********
*********
**********
```

---

### 2. Segitiga dengan While Loop

```python
count = 1

while True:
	print("*"*count)
	count += 1

	if count > sisi:
		break
```

| Komponen | Penjelasan |
|---|---|
| `while True` | Loop tak terbatas, dikontrol dengan `break` |
| `if count > sisi: break` | Berhenti jika sudah melebihi tinggi segitiga |

Hasilnya **sama** dengan versi `for` — ini menunjukkan bahwa `for` dan `while` bisa saling menggantikan.

---

### 3. Hanya Bilangan Ganjil

```python
count = 1

while True:
	if (count%2):
		print("*"*count)
		count += 1
	else:
		count += 1
		continue

	if count > sisi:
		break
```

| Komponen | Penjelasan |
|---|---|
| `count%2` | Modulus: sisa bagi `count` dengan 2. Jika **ganjil** → hasilnya 1 (True). Jika **genap** → hasilnya 0 (False) |
| `continue` | Jika genap, lompat ke iterasi berikutnya (tidak cetak bintang) |
| `if count > sisi: break` | Berhenti setelah melebihi tinggi segitiga |

**Output:**
```
*
***
*****
*******
*********
```

---

### 4. Segitiga Terpusat dengan Spasi

```python
count = 1
spasi = int(sisi/2)

while True:
	if (count%2):
		print(" "*spasi,"+"*count)
		spasi -= 1
		count += 1
	else:
		count += 1
		continue

	if count > sisi:
		break
```

| Komponen | Penjelasan |
|---|---|
| `spasi = int(sisi/2)` | Spasi awal = setengah dari tinggi segitiga |
| `" "*spasi` | Karakter spasi untuk menggeser bintang ke kanan |
| `"+"*count` | Karakter `+` sebagai isi segitiga |
| `spasi -= 1` | Setiap baris, spasi berkurang 1 (segitiga semakin lebar ke kiri) |

**Output:**
```
    +
   +++
  +++++
 +++++++
+++++++++
```

---

## Analogi

Bayangkan kamu sedang menggambar pola bintang di buku:

1. **Baris 1**: Tulis 1 bintang
2. **Baris 2**: Tulis 2 bintang
3. **Baris 3**: Tulis 3 bintang
4. ... dst sampai tinggi yang diinginkan

Untuk segitiga terpusat, kamu menambahkan **spasi di depan** agar bintang-center berada di tengah.

---

## Tips

1. Pola `while True` + `break` memungkinkan kontrol yang lebih fleksibel.
2. Operator `%` (modulus) sangat berguna untuk mengecek ganjil/genap: `angka % 2 == 0` berarti genap.
3. Mulai dari pola sederhana dulu, lalu tambahkan fitur (spasi, karakter berbeda, dll).
