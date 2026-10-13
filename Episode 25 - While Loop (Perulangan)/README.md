# BAB 5 - While Loop (Perulangan)

## Apa yang Dipelajari

- Perulangan `while` untuk mengulang aksi selama kondisi terpenuhi
- Cara membuat kondisi perulangan
- Increment (penambahan nilai) di dalam loop
- Perbedaan `while` dan `for`

---

## Penjelasan Kode

### Membuat Variabel Awal

```python
angka = 0
print(f"angka sekarang -> {angka}")
```

Variabel `angka` diinisialisasi dengan nilai `0`. Ini akan menjadi penghitung dalam perulangan.

---

### While Loop

```python
while angka < 5:
	angka += 1
	print(f"angka sekarang -> {angka}")
	print("otong ganteng maxsyimaal!")
```

| Komponen | Penjelasan |
|---|---|
| `while` | Kata kunci untuk memulai perulangan |
| `angka < 5` | **Kondisi**: selama angka kurang dari 5, loop terus berjalan |
| `angka += 1` | **Increment**: tambah nilai angka sebesar 1 setiap iterasi |
| `print(...)` | Aksi yang diulang |

**Cara Kerja:**

```
angka = 0
    |
    v
angka < 5? ----YES----> angka = 0+1 = 1 → cetak
    |                      |
    v                      v
angka < 5? ----YES----> angka = 1+1 = 2 → cetak
    |                      |
    v                      v
angka < 5? ----YES----> angka = 2+1 = 3 → cetak
    |                      |
    v                      v
angka < 5? ----YES----> angka = 3+1 = 4 → cetak
    |                      |
    v                      v
angka < 5? ----YES----> angka = 4+1 = 5 → cetak
    |                      |
    v                      v
angka < 5? ----NO-----> lanjut ke luar loop
```

**Output:**
```
angka sekarang -> 0
angka sekarang -> 1
otong ganteng maxsyimaal!
angka sekarang -> 2
otong ganteng maxsyimaal!
angka sekarang -> 3
otong ganteng maxsyimaal!
angka sekarang -> 4
otong ganteng maxsyimaal!
angka sekarang -> 5
otong ganteng maxsyimaal!
cukuuup
```

---

### Setelah Loop

```python
print("cukuuup")
```

Dicetak setelah loop selesai (ketika kondisi `angka < 5` menjadi `False`).

---

## Perbedaan `while` vs `for`

| Aspek | `for` | `while` |
|---|---|---|
| Kapan digunakan | Tahu **berapa kali** mengulang | Tahu **kondisi kapan berhenti** |
| Contoh | "Ulangi 10 kali" | "Ulangi sampai angka > 5" |
| Increment manual | Tidak perlu | **Wajib** (agar loop bisa berhenti) |
| Risiko infinite loop | Rendah | **Tinggi** (jika lupa increment) |

---

## Analogi

Bayangkan kamu sedang push-up:

- Kamu bilang: "Aku akan push-up **selama** tubuhku masih bisa angkat" → seperti `while`
- Kamu menghitung setiap push-up: 1, 2, 3, ... sampai lelah (kondisi tidak terpenuhi)
- Setelah lelah, kamu berhenti → loop berakhir

---

## Bahaya Infinite Loop

Jika kamu lupa increment (`angka += 1`), loop akan berjalan **selamanya** karena kondisi `angka < 5` tidak akan pernah berubah dari `True`.

```python
# JANGAN LAKUKAN INI:
while angka < 5:
	print(angka)  # angka tidak pernah berubah → loop tak terbatas!
```

Untuk menghentikan paksa: tekan **Ctrl + C** di terminal.
