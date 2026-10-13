# BAB 16 - Operasi dan Manipulasi String (Part 2)

## Apa yang Dipelajari

- Method case: `upper()`, `lower()`
- Method pengecekan: `isupper()`, `islower()`, `isalpha()`, `isalnum()`, `isdecimal()`, `isspace()`, `istitle()`
- Method pencocokan: `startswith()`, `endswith()`
- Method penggabungan/pemisahan: `join()`, `split()`
- Alokasi karakter: `rjust()`, `ljust()`, `center()`
- Method pembersihan: `strip()`

## Penjelasan Kode

---

### 1. Mengubah Case (Huruf Besar/Kecil)

```python
salam = "bro!"
print("normal " + salam)
salam = salam.upper()
print("upper " + salam)          # BRO!
```
- `upper()` mengubah **semua huruf menjadi huruf besar**.

```python
alay = "aKu KeCe AbieeZZZ"
print("normal " + alay)
alay = alay.lower()
print("lower " + alay)           # aku kece abieezzz
```
- `lower()` mengubah **semua huruf menjadi huruf kecil**.

---

### 2. Method Pengecekan (is...)

```python
salam = "SIST"
apakah_upper = salam.isupper()
print(salam + " is upper? " + str(apakah_upper))  # True

salam = salam.lower()  # "sist"
apakah_upper = salam.isupper()
print(salam + " is upper? " + str(apakah_upper))  # False
```

| Method | Fungsi | Contoh | Hasil |
|--------|--------|--------|-------|
| `isupper()` | Semua huruf besar? | `"SIST".isupper()` | `True` |
| `islower()` | Semua huruf kecil? | `"sist".islower()` | `True` |
| `isalpha()` | Hanya huruf? | `"abc".isalpha()` | `True` |
| `isalnum()` | Huruf + angka? | `"abc123".isalnum()` | `True` |
| `isdecimal()` | Hanya angka? | `"123".isdecimal()` | `True` |
| `isspace()` | Hanya spasi/tab/newline? | `" ".isspace()` | `True` |
| `istitle()` | Title case? (Huruf pertama kapital) | `"Hello World".istitle()` | `True` |

```python
judul = "It Is Okay To Not Be Orkay"
cek_judul = judul.istitle()
print(judul + " is title? " + str(cek_judul))  # True
```

---

### 3. startswith() dan endswith()

```python
cek_start = "Sangjangnim Oppa".startswith("Sangjangnim")
print("start " + str(cek_start))  # True

cek_end = "Sangjangnim Oppak".endswith("Oppak")
print("end " + str(cek_end))      # True
```
- `startswith("teks")` → mengecek **apakah string diawali** dengan teks tertentu.
- `endswith("teks")` → mengecek **apakah string diakhiri** dengan teks tertentu.

---

### 4. join() dan split()

```python
# join → menggabungkan list menjadi string
pisah = ['aku', 'sayang', 'kamu']
gabungan = ' ehm '.join(pisah)
print(pisah)         # ['aku', 'sayang', 'kamu']
print(gabungan)      # aku ehm sayang ehm kamu
```
- `join()` menggabungkan elemen list dengan **pemisah** yang ditentukan.
- `' ehm '.join(pisah)` → menyisipkan `" ehm "` di antara setiap elemen.

```python
# split → memecah string menjadi list
gabungan = "naik vespa keliling kota"
pisah = gabungan.split()
print(gabungan)      # naik vespa keliling kota
print(pisah)         # ['naik', 'vespa', 'keliling', 'kota']
```
- `split()` tanpa argumen memecah berdasarkan **spasi**.

```python
# split dengan pemisah khusus
gabungan = "naikehmvespaehmkelilingehmkota"
pisah = gabungan.split("ehm")
print(gabungan)      # naikehmvespaehmkelilingehmkota
print(pisah)         # ['naik', 'vespa', 'keliling', 'kota']
```
- `split("ehm")` memecah string di setiap kemunculan `"ehm"`.

---

### 5. Alokasi Karakter (rjust, ljust, center)

```python
kanan = "kanan".rjust(20)        # rata kanan, lebar 20
print("'" + kanan + "'")

kiri = "kiri".ljust(20)          # rata kiri, lebar 20
print("'" + kiri + "'")

tengah = "tengah".center(20)     # rata tengah, lebar 20
print("'" + tengah + "'")

tengah = "tengah".center(20, '-') # rata tengah dengan pengisi '-'
print("'" + tengah + "'")
```

| Method | Keterangan | Contoh |
|--------|------------|--------|
| `rjust(n)` | Rata kanan, lebar `n` | `"hi".rjust(5)` → `"   hi"` |
| `ljust(n)` | Rata kiri, lebar `n` | `"hi".ljust(5)` → `"hi   "` |
| `center(n)` | Rata tengah, lebar `n` | `"hi".center(5)` → `" hi "` |
| `center(n, '-')` | Rata tengah dengan pengisi | `"hi".center(5, '-')` → `"--hi-"` |

---

### 6. strip() - Menghapus Spasi/Pengisi

```python
kanan = kanan.strip()
print("'" + kanan + "'")

tengah = tengah.strip('-')
print("'" + tengah + "'")
```
- `strip()` → menghapus **spasi** di awal dan akhir string.
- `strip('-')` → menghapus karakter `'-'` di awal dan akhir string.

## Tabel Ringkasan Semua Method

| Method | Keterangan | Contoh | Hasil |
|--------|------------|--------|-------|
| `upper()` | Huruf besar semua | `"hi".upper()` | `"HI"` |
| `lower()` | Huruf kecil semua | `"HI".lower()` | `"hi"` |
| `isupper()` | Cek huruf besar | `"HI".isupper()` | `True` |
| `islower()` | Cek huruf kecil | `"hi".islower()` | `True` |
| `isalpha()` | Cek hanya huruf | `"abc".isalpha()` | `True` |
| `isalnum()` | Cek huruf+angka | `"a1".isalnum()` | `True` |
| `isdecimal()` | Cek angka saja | `"123".isdecimal()` | `True` |
| `isspace()` | Cek spasi | `" ".isspace()` | `True` |
| `istitle()` | Cek title case | `"Hello".istitle()` | `True` |
| `startswith(x)` | Cek awalan | `"Hi".startswith("H")` | `True` |
| `endswith(x)` | Cek akhiran | `"Hi".endswith("i")` | `True` |
| `join(list)` | Gabung list → string | `"-".join(["a","b"])` | `"a-b"` |
| `split()` | Pecah string → list | `"a b".split()` | `["a","b"]` |
| `rjust(n)` | Rata kanan | `"hi".rjust(5)` | `"   hi"` |
| `ljust(n)` | Rata kiri | `"hi".ljust(5)` | `"hi   "` |
| `center(n)` | Rata tengah | `"hi".center(5)` | `" hi "` |
| `strip()` | Hapus spasi/char | `" hi ".strip()` | `"hi"` |

## Analogi

Bayangkan kamu sedang **mengedit teks di Microsoft Word**:
- `upper()`/`lower()` = Tombol **Caps Lock** atau mengubah semua huruf besar/kecil.
- `startswith()`/`endswith()` = Mengecek **apakah paragraf dimulai/diakhiri** dengan kata tertentu.
- `join()` = Menyambungkan **beberapa kalimat** dengan koma atau pemisah lain.
- `split()` = Memecah **kalimat panjang** menjadi kata-kata terpisah.
- `center()`/`rjust()`/`ljust()` = **Mengatur posisi teks**: rata kiri, rata kanan, atau rata tengah.
- `strip()` = **Menghapus spasi berlebih** di awal dan akhir teks.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, operasi dan manipulasi string part 2 |
