# BAB 5 - Episode 65: Write External File - Write and Append

## Apa yang Dipelajari

- Menulis ke file menggunakan mode **write (`w`)** — menimpa isi file
- Menambah isi file menggunakan mode **append (`a`)** — menambah di akhir
- Mode **`r+`** untuk membaca sekaligus menulis
- Pentingnya parameter **`encoding="utf-8"`**
- Perbedaan behavior `w`, `a`, dan `r+`

---

## Penjelasan Kode

### File: `main_app.py`

### Bagian 1 — Mode Write (`w`): Menimpa File

```python
with open("data_1.txt", 'w', encoding="utf-8") as file:
    file.write("jon si jhonny")

with open("data_1.txt", 'w', encoding="utf-8") as file:
    file.write("ucup surucup")

with open("data_1.txt", 'w', encoding="utf-8") as file:
    file.write("overwrite")
```

**Apa yang terjadi:**

| Operasi | Isi File Setelahnya | Penjelasan |
|---|---|---|
| Pertama (`"jon si jhonny"`) | `jon si jhonny` | File baru dibuat, ditulis |
| Kedua (`"ucup surucup"`) | `ucup surucup` | File ditimpa, isi lama hilang |
| Ketiga (`"overwrite"`) | `overwrite` | File ditimpa lagi |

> **Kunci:** Mode `w` **selalu menghapus isi file** yang lama sebelum menulis yang baru. Terakhir kali ditulis, itulah yang tersisa.

Hasil akhir file `data_1.txt`:
```
overwrite
```

---

### Bagian 2 — Mode Append (`a`): Menambah di Akhir

```python
with open("data_2.txt", 'w', encoding="utf-8") as file:
    file.write("jon si jhonny\n")
```

- Pertama, file dibuat baru dengan isi `jon si jhonny`.
- `\n` di akhir = ada **enter/newline** di akhir baris.

```python
with open("data_2.txt", 'a', encoding="utf-8") as file:
    file.write("ucup surucup\n")
```

- Mode `a` (append) **tidak menghapus** isi lama. Tulisan baru **ditambahkan di akhir**.

```python
with open("data_2.txt", 'a', encoding="utf-8") as file:
    file.write("tambah lagi dengan append\n")
```

- Lagi-lagi ditambahkan di akhir.

Hasil akhir file `data_2.txt`:
```
jon si jhonny
ucup surucup
tambah lagi dengan append
```

> **Perbedaan `w` vs `a`:**
> - `w` = **Timpa** (hapus lama, tulis baru)
> - `a` = **Tambah** (isi lama tetap, tulis di akhir)

---

### Bagian 3 — Mode `r+`: Baca + Tulis

```python
with open("data_3.txt", 'w', encoding="utf-8") as file:
    file.write("data ke 3\n")
```

- File baru dibuat dengan isi `data ke 3`.

```python
with open("data_3.txt", 'r+', encoding="utf-8") as file:
    file.write("baris-1 \n")
    file.write("baris-2 \n")
    file.write("baris-3 \n")
```

- Mode `r+` bisa baca **dan** tulis. File harus sudah ada.
- **PENTING:** `file.write()` menulis dari **posisi awal file** (pointer di awal). Jadi tulisan baru **menimpa** karakter lama dari depan.

| Karakter Asal | Ditulis Ulang | Hasil |
|---|---|---|
| `d a t a   k e   3 \n` (11 karakter) | `b a r i s - 1   \n` | Isi awal tertimpa |

```python
with open("data_3.txt", 'r+', encoding="utf-8") as file:
    data = file.read()
    print(data)
```

- Membaca isi file setelah ditulis. Pointer kembali ke awal karena `file.read()`.

```python
with open("data_3.txt", 'r+', encoding="utf-8") as file:
    file.write("otong")
```

- Menulis `otong` dari posisi awal file → menimpa 5 karakter pertama.

Hasil akhir `data_3.txt`:
```
otong-1 
baris-2 
baris-3 
```

- `otong` menggantikan `baris` di baris pertama → menjadi `otong-1 `

---

### Output Program

Program ini tidak mencetak ke layar, tapi menghasilkan 3 file:

| File | Isi Akhir |
|---|---|
| `data_1.txt` | `overwrite` |
| `data_2.txt` | `jon si jhonny` (baris 1) + `ucup surucup` (baris 2) + `tambah lagi dengan append` (baris 3) |
| `data_3.txt` | `otong-1 ` (baris 1) + `baris-2 ` (baris 2) + `baris-3 ` (baris 3) |

---

### Ringkasan Mode File

| Mode | Fungsi | Membuat file baru? | Menimpa isi? | Pointer di |
|---|---|---|---|---|
| `'w'` | Write | Ya | **Ya, selalu** | Awal |
| `'a'` | Append | Ya | **Tidak** | Akhir |
| `'r+'` | Read+Write | **Tidak** | Tergantung posisi | Awal |

---

### Parameter `encoding="utf-8"`

```python
with open("data_1.txt", 'w', encoding="utf-8") as file:
```

- **`encoding="utf-8"`** memastikan karakter khusus (é, ñ, 你好, 🎉) bisa ditulis dan dibaca dengan benar.
- Tanpa encoding, Python menggunakan encoding default sistem operasi yang bisa berbeda-beda.

---

## Analogi

Bayangkan kamu sedang **menulis di papan tulis**:

1. **Mode `w` (write)** = Kamu **menghapus seluruh papan tulis** dengan penghapus besar, lalu menulis tulisan baru dari awal. Semua tulisan lama hilang.

2. **Mode `a` (append)** = Kamu **tidak menghapus** tulisan lama. Kamu menulis tulisan baru **di baris paling bawah** papan tulis. Tulisan lama tetap ada.

3. **Mode `r+`** = Kamu menulis **dari pojok kiri atas** papan tulis, **menimpa karakter satu per satu** dari depan. Jadi kata baru menggantikan kata lama karakter per karakter.

> Ini seperti menulis di buku: `w` berarti mencoret semua halaman dan menulis baru, `a` berarti menambah halaman baru di belakang, dan `r+` berarti menulis langsung di atas teks yang sudah ada.

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Write mode | `open(f, 'w')` | Buat baru atau timpa file |
| Append mode | `open(f, 'a')` | Tambah di akhir file |
| Read+Write | `open(f, 'r+')` | Baca dan tulis dari awal |
| Write | `file.write("teks")` | Menulis string ke file |
| Encoding | `encoding="utf-8"` | Encoding karakter internasional |
| Newline | `\n` | Karakter enter/newline |
