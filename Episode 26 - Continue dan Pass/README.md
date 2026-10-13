# BAB 6 - Continue dan Pass

## Apa yang Dipelajari

- Perintah `continue` untuk melompati satu iterasi
- Perintah `pass` sebagai placeholder (tidak melakukan apa-apa)
- Cara kerja `continue` dalam loop
- Perbedaan `continue`, `pass`, dan `break`

---

## Penjelasan Kode

### Pass (Komentar)

```python
# angka = 0
# while angka < 5:
# 	angka += 1
# 	if angka == 3:
# 		pass  # ini tidak akan dieksekusi
# 	print(angka)
```

`pass` berfungsi sebagai **placeholder** — ia tidak melakukan apa-apa. Kode di atas dikomentari, tetapi jika dijalankan:

- Saat `angka == 3`, `pass` dilewati begitu saja
- `print(angka)` tetap dijalankan
- **Tidak ada perbedaan output** dari tanpa `pass`

> **Kapan `pass` berguna?** Saat kamu ingin membuat struktur kode dulu (misal fungsi kosong atau blok `if` kosong) tapi belum menulis logikanya.

---

### Continue

```python
angka = 0
print(f"angka sekarang -> {angka}")

while angka < 5:
	angka += 1
	print(f"angka sekarang -> {angka}")  # aksi 1

	if angka == 3:
		print("nice!")
		continue  # loncat ke iterasi berikutnya

	print("whassup!")  # aksi 2
```

| Komponen | Penjelasan |
|---|---|
| `continue` | Memerintahkan Python untuk **melompat** ke awal loop berikutnya |
| `angka == 3` | Kondisi yang memicu `continue` |

**Cara Kerja:**

```
angka=1 → cetak "angka=1" → 1!=3 → cetak "whassup!"
angka=2 → cetak "angka=2" → 2!=3 → cetak "whassup!"
angka=3 → cetak "angka=3" → 3==3 → cetak "nice!" → CONTINUE (skip "whassup!")
angka=4 → cetak "angka=4" → 4!=3 → cetak "whassup!"
angka=5 → cetak "angka=5" → 5!=3 → cetak "whassup!" → loop berhenti
```

**Output:**
```
angka sekarang -> 0
angka sekarang -> 1
whassup!
angka sekarang -> 2
whassup!
angka sekarang -> 3
nice!
angka sekarang -> 4
whassup!
angka sekarang -> 5
whassup!
Pinish!
```

Perhatikan: saat `angka == 3`, **`"whassup!"` tidak dicetak** karena `continue` melompati sisa blok loop.

---

## Ringkasan: `continue` vs `pass` vs `break`

| Perintah | Fungsi |
|---|---|
| `continue` | **Lompat** ke iterasi berikutnya (lewati sisa blok loop) |
| `pass` | **Tidak melakukan apa-apa** (placeholder, lanjut normal) |
| `break` | **Hentikan** loop sepenuhnya |

---

## Analogi

Bayangkan kamu sedang makan 5 macam makanan:

- **Pass**: Kamu melihat makanan ke-3 tapi tidak mengapa apa — kamu tetap lanjut makan seperti biasa
- **Continue**: Kamu **melewati** makanan ke-3 (tidak kamu makan), tapi lanjut ke makanan ke-4 dan seterusnya
- **Break**: Kamu **berhenti makan** sama sekali setelah makanan ke-3

---

## Tips

- `continue` berguna saat kamu ingin **skip** beberapa kasus tertentu saja.
- `pass` sering digunakan dalam kode yang sedang dalam proses pengembangan.
- Hati-hati dengan `continue` yang membuat loop berjalan lebih lama dari yang diharapkan.
