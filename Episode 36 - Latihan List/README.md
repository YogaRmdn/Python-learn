# BAB 16 - Latihan List

## Apa yang Dipelajari

- Membuat program **manajemen data buku** interaktif
- Menggabungkan konsep: list, while loop, for loop, enumerate, append, input
- Pola program interaktif dengan `while True` + `break`

---

## Penjelasan Kode

### Program List Buku

```python
list_buku = []
while True:
	print("\nMasukan data buku")
	judul = input("Judul buku\t: ")
	penulis = input("Nama penulis\t: ")

	buku_baru = [judul, penulis]
	list_buku.append(buku_baru)

	print("\n\n","="*10,"Data Buku","="*10)
	for index, buku in enumerate(list_buku):
		print(f"{index+1} | {buku[0]} | {buku[1]}")

	print("\n\n","="*20)
	isLanjut = input("Apakah dilanjutkan?(y/n) ")

	if isLanjut == "n":
		break

print("PROGRAM SELESAI")
```

---

### Penjelasan Baris per Baris

#### 1. Inisialisasi List Kosong

```python
list_buku = []
```

List kosong `[]` disiapkan untuk menampung data buku yang akan dimasukkan.

---

#### 2. Loop Utama

```python
while True:
```

Loop tak terbatas yang akan terus meminta input buku sampai pengguna memilih berhenti.

---

#### 3. Membaca Input

```python
	print("\nMasukan data buku")
	judul = input("Judul buku\t: ")
	penulis = input("Nama penulis\t: ")
```

| Variabel | Penjelasan |
|---|---|
| `judul` | Judul buku yang dimasukkan pengguna |
| `penulis` | Nama penulis buku |

`\t` = tab untuk rapi.

---

#### 4. Membuat Sub-List dan Menambahkannya

```python
	buku_baru = [judul, penulis]
	list_buku.append(buku_baru)
```

| Komponen | Penjelasan |
|---|---|
| `buku_baru = [judul, penulis]` | Membuat list berisi judul dan penulis sebagai **satu entri buku** |
| `list_buku.append(buku_baru)` | Menambahkan entri buku ke list utama |

---

#### 5. Menampilkan Semua Buku

```python
	print("\n\n","="*10,"Data Buku","="*10)
	for index, buku in enumerate(list_buku):
		print(f"{index+1} | {buku[0]} | {buku[1]}")
```

| Komponen | Penjelasan |
|---|---|
| `"="*10` | Garis pembatas (`==========`) |
| `enumerate(list_buku)` | Memberikan index + data buku |
| `index+1` | Nomor urut (mulai dari 1, bukan 0) |
| `buku[0]` | Judul buku |
| `buku[1]` | Nama penulis |

**Output contoh:**
```
========== Data Buku ==========
1 | Laskar Pelangi | Andrea Hirata
2 | Bumi | Tere Liye
```

---

#### 6. Mengecek Kelanjutan

```python
	print("\n\n","="*20)
	isLanjut = input("Apakah dilanjutkan?(y/n) ")

	if isLanjut == "n":
		break
```

Jika pengguna mengetik `"n"`, loop dihentikan dengan `break`.

---

## Contoh Jalankan

```
Masukan data buku
Judul buku   : Laskar Pelangi
Nama penulis : Andrea Hirata

========== Data Buku ==========
1 | Laskar Pelangi | Andrea Hirata

Apakah dilanjutkan?(y/n) y

Masukan data buku
Judul buku   : Bumi
Nama penulis : Tere Liye

========== Data Buku ==========
1 | Laskar Pelangi | Andrea Hirata
2 | Bumi | Tere Liye

Apakah dilanjutkan?(y/n) n
PROGRAM SELESAI
```

---

## Konsep yang Digabungkan

| Konsep | Penggunaan dalam Program |
|---|---|
| `list` | Menyimpan semua data buku |
| `append()` | Menambah buku baru ke list |
| `while True` + `break` | Loop interaktif sampai pengguna berhenti |
| `enumerate()` | Menampilkan nomor urut + data |
| `input()` | Membaca input dari pengguna |
| Index `buku[0]`, `buku[1]` | Mengakses judul dan penulis |

---

## Analogi

Program ini seperti **resepsionis hotel** yang:

1. Menamu tamu baru satu per satu
2. Mencatat nama dan kamar di buku tamu
3. Setiap kali tamu baru datang, mencetak **daftar semua tamu** yang sudah ada
4. Bertanya: "Masih ada tamu lagi?" → jika tidak, selesai bekerja

---

## Tips

1. Pola `while True` + `break` + `input()` sangat umum untuk program **interaktif**.
2. Gunakan **nested list** untuk menyimpan data berelasi (judul + penulis = satu entri).
3. `enumerate()` memudahkan menampilkan data dengan nomor urut yang rapi.
