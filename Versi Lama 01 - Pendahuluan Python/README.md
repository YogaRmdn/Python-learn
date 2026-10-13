# BAB 1 - Pendahuluan Python

## Apa yang Dipelajari

- Menulis program Python pertama
- Menggunakan fungsi `print()` untuk menampilkan output
- Membuat variabel dan menyimpan nilai
- Operasi matematika dasar: penjumlahan, pengurangan, perkalian, pembagian
- Menulis komentar dalam Python
- Konvensi penulisan kode Python

---

## Penjelasan Kode

### File: `helloWorld.py`

#### 1. Membuat Variabel

```python
a = 5
b = 3
```

| Variabel | Nilai | Tipe Data |
|----------|-------|-----------|
| `a` | `5` | integer (bilangan bulat) |
| `b` | `3` | integer (bilangan bulat) |

- **Variabel** adalah "wadah" untuk menyimpan data. Seperti nampan yang menampung sesuatu.
- Kita memberi nama `a` dan `b`, lalu menyimpan angka di dalamnya.
- Tanda `=` bukan berarti "sama dengan" dalam matematika, tapi **"simpan nilai ini ke variabel"**.

---

#### 2. Penjumlahan

```python
# penjumlahan
c = a + b
print("hasil a + b = ", c)
```

- **Komentar** ditandai dengan tanda `#`. Python akan mengabaikan tulisan setelah tanda `#`.
- `a + b` menghasilkan `5 + 3 = 8`.
- Hasil disimpan di variabel `c`.
- `print()` menampilkan teks `"hasil a + b = "` diikuti nilai `c` ke layar.

---

#### 3. Pengurangan

```python
# pengurangan
c = a - b
print("hasil a - b = ", c)
```

- `a - b` menghasilkan `5 - 3 = 2`.
- Variabel `c` **di-isi ulang** (di-overwrite) dengan nilai baru.

---

#### 4. Perkalian

```python
# perkalian
c = a*b
print("hasil a*b = ", c)
```

- Tanda `*` digunakan untuk perkalian di Python (bukan `×`).
- `a * b` menghasilkan `5 * 3 = 15`.

---

#### 5. Pembagian

```python
# pembagian
c = a / b
print("hasil a/b =", c)
```

- Tanda `/` untuk pembagian.
- `a / b` menghasilkan `5 / 3 = 1.6666...` (selalu menghasilkan **float**/bilangan desimal di Python 3).

---

#### 6. Komentar yang Belum Diisi

```python
# pembagian pembulatan keatas

# modulus

# pangkat
```

Bagian ini masih kosong. Untuk referensi:
- **Modulus** (`%`): sisa pembagian. Contoh: `5 % 3 = 2`
- **Pangkat** (`**`): Contoh: `5 ** 3 = 125`

---

## Ringkasan Operasi Matematika

| Operasi | Simbol | Contoh | Hasil |
|---------|--------|--------|-------|
| Penjumlahan | `+` | `5 + 3` | `8` |
| Pengurangan | `-` | `5 - 3` | `2` |
| Perkalian | `*` | `5 * 3` | `15` |
| Pembagian | `/` | `5 / 3` | `1.6667` |
| Modulus | `%` | `5 % 3` | `2` |
| Pangkat | `**` | `5 ** 3` | `125` |

---

## Analogi

Bayangkan kamu punya **kalkulator sederhana**:
- Variabel `a = 5` artinya kamu menekan tombol angka **5**.
- Variabel `b = 3` artinya kamu menekan tombol angka **3**.
- `c = a + b` artinya kamu menekan tombol **+** lalu **=**, dan hasilnya disimpan.
- `print(c)` artinya kamu melihat hasilnya di layar kalkulator.

---

## Komentar

Komentar ditulis dengan tanda `#` di awal baris. Komentar **tidak dijalankan** oleh Python — hanya untuk catatan manusia.

```python
# Ini komentar satu baris
```

---

## Tips untuk Pemula

- Nama variabel sebaiknya jelas dan deskriptif (misalnya `harga`, `jumlah`, bukan `a`, `b`).
- Gunakan huruf kecil untuk nama variabel, pisahkan dengan underscore jika panjang: `harga_total`.
- Python **sensitif huruf besar-kecil** (`A` berbeda dengan `a`).
