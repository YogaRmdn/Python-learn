# BAB 9 - While Loop

## Apa yang Dipelajari

- Perulangan `while` (loop bersyarat)
- Menggunakan variabel penghitung untuk mengontrol while
- Variabel boolean sebagai pengontrol loop
- `break` untuk menghentikan while loop
- `continue`, `pass`, dan `else` dalam while loop

---

## Penjelasan Kode

### File: `while.py`

#### 1. While Loop Sederhana dengan Penghitung

```python
angka = 0

while angka < 5:
    print('nilai angka adalah:', angka)
    angka = angka + 1

print('di luar while')
```

**Cara kerja:**

| Iterasi | `angka` | `angka < 5`? | Aksi |
|---------|---------|---------------|------|
| 1 | 0 | True | Cetak 0, tambah jadi 1 |
| 2 | 1 | True | Cetak 1, tambah jadi 2 |
| 3 | 2 | True | Cetak 2, tambah jadi 3 |
| 4 | 3 | True | Cetak 3, tambah jadi 4 |
| 5 | 4 | True | Cetak 4, tambah jadi 5 |
| 6 | 5 | False | Loop berhenti |

- `angka = angka + 1` bisa ditulis lebih singkat: `angka += 1`.

---

#### 2. While Loop dengan Boolean

```python
start = True
angka = 0

while start:
    print("di dalam while")
    if angka is 100:
        start = False
        print('oke angka 100 diketemukan')
    angka += 1
```

**Cara kerja:**
1. `start = True` → loop akan berjalan selama `start` bernilai `True`.
2. Setiap iterasi, `angka` bertambah 1.
3. Ketika `angka == 100`:
   - `start = False` → loop akan berhenti di iterasi berikutnya.
   - `"oke angka 100 diketemukan"` dicetak.
4. Loop berhenti setelah `angka` mencapai 100.

> **Perhatian:** Ini contoh **infinite loop yang dikontrol**. Tanpa `if angka is 100`, loop akan berjalan selamanya!

---

### File: `while2.py`

#### 3. While Loop dengan Break, Continue, Pass, dan Else

```python
angka = 0

while angka < 10:
    if angka is 5:
        # print('checkpoint 1')
        break
        continue
        pass
        # print('checkpoint 2')

    print('nilai angka adalah:', angka)
    angka += 1
else:
    print('nilai angka diakhir while adalah', angka)

print('di luar while')
```

**Cara kerja:**

| Iterasi | `angka` | Kondisi | Aksi |
|---------|---------|---------|------|
| 1 | 0 | `angka < 10` ✅, `angka != 5` | Cetak 0, tambah jadi 1 |
| 2 | 1 | `angka < 10` ✅, `angka != 5` | Cetak 1, tambah jadi 2 |
| 3 | 2 | `angka < 10` ✅, `angka != 5` | Cetak 2, tambah jadi 3 |
| 4 | 3 | `angka < 10` ✅, `angka != 5` | Cetak 3, tambah jadi 4 |
| 5 | 4 | `angka < 10` ✅, `angka != 5` | Cetak 4, tambah jadi 5 |
| 6 | 5 | `angka < 10` ✅, `angka == 5` | `break` → loop berhenti |

- `break` menghentikan loop → `else` **tidak dijalankan**.
- `continue` dan `pass` **tidak pernah tercapai** karena `break` sudah dijalankan lebih dulu.

---

## Ringkasan While Loop

| Konsep | Penjelasan |
|--------|------------|
| `while kondisi:` | Loop berjalan selama kondisi bernilai `True` |
| Penghitung | Variabel yang ditambah agar loop tidak infinite |
| Boolean controller | Variabel `True/False` untuk mengontrol loop |
| `break` | Menghentikan loop segera |
| `continue` | Melompat ke iterasi berikutnya |
| `else` | Dijalankan jika loop selesai tanpa `break` |

---

## Perbandingan For vs While

| For Loop | While Loop |
|----------|------------|
| Cocok untuk **mengetahui jumlah iterasi** | Cocok untuk **kondisi yang tidak diketahui** |
| Menggunakan `range()` atau iterable | Menggunakan kondisi boolean |
| Otomatis berhenti | Perlu pengontrol manual |

---

## Analogi

Bayangkan kamu sedang **berlari di trek**:

**While dengan penghitung:**
- "Lari selama kurang dari 5 putaran."
- Setiap putaran, hitungan bertambah 1.
- Setelah 5 putaran, berhenti.

**While dengan boolean:**
- "Lari terus sampai saya bilang berhenti."
- Ada orang yang membawa bendera, setiap 100 langkah dia cek: "Sudah cukup?"
- Kalau sudah, dia ambil bendera → berhenti.

**Break:**
- "Lari, tapi kalau lihat kucing, langsung berhenti."

---

## Tips untuk Pemula

- **Selalu pastikan** while loop punya cara untuk berhenti (penghitung atau break).
- `while True:` akan berjalan selamanya — gunakan hanya jika ada `break` di dalamnya.
- `angka += 1` lebih pendek dan Pythonic dari `angka = angka + 1`.
- Gunakan `while` saat kamu tidak tahu berapa kali loop harus berjalan.
