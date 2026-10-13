# BAB 7 - Break

## Apa yang Dipelajari

- Perintah `break` untuk menghentikan loop secara paksa
- Penggunaan `while True` sebagai loop tak terbatas
- Kombinasi `while True` + `break` untuk input pengguna
- Perbedaan `break` dengan kondisi loop normal

---

## Penjelasan Kode

### 1. Break dalam While Loop

```python
angka = 0

while angka < 5:
	angka += 1
	print(f"angka sekarang = {angka}")

	if angka == 3:
		print("nice!")
		break

	print("wassup!")
```

| Komponen | Penjelasan |
|---|---|
| `break` | Menghentikan loop **secara langsung**, tidak peduli kondisi `while` |
| `angka == 3` | Kondisi yang memicu `break` |

**Cara Kerja:**

```
angka=1 → cetak "angka=1" → 1!=3 → cetak "wassup!"
angka=2 → cetak "angka=2" → 2!=3 → cetak "wassup!"
angka=3 → cetak "angka=3" → 3==3 → cetak "nice!" → BREAK! (loop berhenti)
```

**Output:**
```
angka sekarang = 1
wassup!
angka sekarang = 2
wassup!
angka sekarang = 3
nice!
cukuuup finish!
```

Perhatikan: angka 4 dan 5 **tidak pernah dicetak** karena loop sudah dihentikan oleh `break`.

---

### 2. While True + Break (Loop Interaktif)

```python
data_int = int(input("hitung sampai = "))
angka = 0

while True:
	angka += 1
	print(f"count = {angka}")

	if angka == data_int:
		print("nice!")
		break

	print("wassup!")
```

| Komponen | Penjelasan |
|---|---|
| `while True` | Loop yang **tidak akan pernah berhenti** sendirinya (infinite loop terkendali) |
| `int(input(...))` | Membaca input pengguna dan mengonversi ke integer |
| `break` | Satu-satunya cara untuk keluar dari `while True` |

**Cara Kerja:**
1. Program meminta pengguna memasukkan angka target
2. Loop menghitung dari 1 sampai angka target
3. Saat mencapai target, `break` dijalankan dan loop berhenti

> **`while True` + `break`** adalah pola umum dalam pemrograman untuk membuat loop yang berjalan sampai kondisi tertentu terpenuhi.

---

## Analogi

Bayangkan kamu sedang berjalan di lorong:

- **Break**: Kamu berhenti berjalan **seketika** saat menemukan pintu keluar
- Tanpa `break`: Kamu terus berjalan sampai ujung lorong (kondisi while)

---

## Perbedaan `break` vs Kondisi Normal

| Aspek | `break` | Kondisi normal (`while angka < 5`) |
|---|---|---|
| Kapan berhenti | Saat `break` dieksekusi | Saat kondisi menjadi `False` |
| Kontrol | Di dalam loop | Di awal loop |
| Fleksibilitas | Lebih fleksibel | Tergantung logika kondisi |

---

## Tips

1. Gunakan `while True` + `break` saat kamu ingin loop yang berjalan sampai **pengguna memutuskan berhenti**.
2. **Selalu pastikan** ada jalur `break` agar loop tidak berjalan selamanya.
3. `break` hanya menghentikan **satu level** loop (jika ada nested loop, hanya loop terdalam yang berhenti).
