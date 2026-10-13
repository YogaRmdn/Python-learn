# BAB 4 - Episode 64: Read External File - `open()` dan `with`

## Apa yang Dipelajari

- Membuka file teks eksternal menggunakan **`open()`**
- Mode **read (`r`)** untuk membaca isi file
- Membaca seluruh isi file dengan **`file.read()`**
- Membaca per baris dengan **`file.readline()`**
- Membaca semua baris sebagai list dengan **`file.readlines()`**
- Menutup file dengan **`file.close()`**
- Menggunakan **`with` statement** agar file otomatis tertutup
- Memeriksa status file: **`file.readable()`**, **`file.writable()`**, **`file.closed`**

---

## Penjelasan Kode

### File: `main_app.py`

### Bagian 1 — Membuka File dengan `open()`

```python
print(3*"=", " Membaca file txt ", 3*"=")
file = open("data.txt", mode="r")
```

- `open("data.txt", mode="r")` membuka file `data.txt` dalam mode **read** (membaca).
- `mode="r"` berarti file hanya bisa **dibaca**, tidak bisa diubah.
- Objek `file` adalah **file handle** — sebuah "pegangan" untuk berinteraksi dengan file.

---

### Mengecek Status File

```python
print(f"status read : {file.readable()}")
print(f"status write : {file.writable()}")
```

| Metode | Output | Penjelasan |
|---|---|---|
| `file.readable()` | `True` | File bisa dibaca (mode `r`) |
| `file.writable()` | `False` | File tidak bisa ditulis (mode `r`) |

---

### Membaca Seluruh File

```python
print(file.read())
```

- `file.read()` membaca **seluruh isi file** sebagai satu string panjang.
- Setelah dipanggil, **pointer file** berada di akhir file. Jika dipanggil lagi, hasilnya string kosong `""`.

---

### Membaca Per Baris (Komentar)

```python
# print(file.readline(), end="")  # baca baris pertama
# print(file.readline(), end="")  # baca baris kedua
```

- `file.readline()` membaca **satu baris** dari file (sampai karakter `\n`).
- `end=""` agar tidak ada newline ganda (karena `readline()` sudah menyertakan `\n`).

---

### Membaca Semua Baris sebagai List

```python
# print(file.readlines())
```

- `file.readlines()` mengembalikan **list** di mana setiap elemen adalah satu baris dari file.
- Contoh output: `['Ucup Surucup\n', 'Otong Surotong\n', 'Jhon si Jhonny\n']`

---

### Menutup File

```python
print(f"apakah file sudah diclose : {file.closed}")
file.close()
print(f"apakah file sudah diclose : {file.closed}")
```

| Saat | `file.closed` | Penjelasan |
|---|---|---|
| Sebelum `close()` | `False` | File masih terbuka |
| Sesudah `close()` | `True` | File sudah ditutup |

> **Penting:** Selalu tutup file setelah selesai digunakan agar resources sistem dibebaskan.

---

### Bagian 2 — Membuka File dengan `with` Statement

```python
print("\n", 3*"=", " Membaca file txt dengan with", 3*"=")

with open("data.txt", mode="r") as file:
    content = file.readline()
    print(content, end="")
    print(f"apakah file sudah diclose : {file.closed}")

print(f"apakah file sudah diclose : {file.closed}")
```

**`with` statement** adalah cara **terbaik** membuka file di Python:

| Aspek | Tanpa `with` | Dengan `with` |
|---|---|---|
| Tutup file | Harus `file.close()` manual | **Otomatis** tertutup |
| Error handling | Bisa lupa close → memory leak | Aman, selalu tertutup |
| Kode | Lebih panjang | Lebih ringkas |

- Di **dalam blok `with`**: `file.closed == False` (file masih terbuka).
- Di **luar blok `with`**: `file.closed == True` (file sudah otomatis tertutup).

---

### File: `data.txt` (File Pendukung)

```
Ucup Surucup
Otong Surotong
Jhon si Jhonny
```

File ini berisi 3 baris data teks yang dibaca oleh program.

---

### Output Program

```
===  Membaca file txt  ===
status read : True
status write : False
Ucup Surucup
Otong Surotong
Jhon si Jhonny
apakah file sudah diclose : False
apakah file sudah diclose : True

===  Membaca file txt dengan with  ===
Ucup Surucup
apakah file sudah diclose : False
apakah file sudah diclose : True
```

---

### Ringkasan Metode Membaca File

| Metode | Hasil | Penjelasan |
|---|---|---|
| `file.read()` | String | Seluruh isi file sebagai satu string |
| `file.readline()` | String | Satu baris per panggilan |
| `file.readlines()` | List | Semua baris sebagai list of string |

---

### Ringkasan Mode File

| Mode | Fungsi | Keterangan |
|---|---|---|
| `"r"` | Read | Membaca file (default). File harus ada |
| `"w"` | Write | Menulis file. Membuat baru atau menimpa |
| `"a"` | Append | Menambah di akhir file |
| `"r+"` | Read+Write | Baca dan tulis. File harus ada |

---

## Analogi

Bayangkan kamu pergi ke **perpustakaan**:

1. **`open("data.txt", "r")`** = Kamu meminjam buku dari rak. Kamu mendapatkan "buku"-nya (file handle).
2. **`file.read()`** = Kamu **membaca seluruh buku** dari awal sampai akhir sekaligus.
3. **`file.readline()`** = Kamu membaca **satu paragraf** saja, lalu berhenti.
4. **`file.readlines()`** = Kamu fotokopi buku itu → setiap halaman menjadi satu elemen dalam daftar (list).
5. **`file.close()`** = Kamu **mengembalikan buku** ke rak perpustakaan.
6. **`with open(...) as file:`** = Kamu meminjam buku di meja pinjaman. Begitu kamu selesai (keluar dari blok `with`), petugas perpustakaan **otomatis mengambil dan mengembalikan buku** ke rak. Jadi kamu tidak perlu khawatir lupa mengembalikan!

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Buka file | `open("file.txt", "r")` | Membuka file untuk dibaca |
| Baca semua | `file.read()` | Membaca seluruh isi file |
| Baca satu baris | `file.readline()` | Membaca satu baris |
| Baca sebagai list | `file.readlines()` | Semua baris jadi list |
| Tutup file | `file.close()` | Menutup file |
| Cek status | `file.closed` | `True` jika sudah ditutup |
| With statement | `with open(...) as f:` | Auto-close setelah selesai |
| Cek bisa baca | `file.readable()` | `True` jika mode `r` |
| Cek bisa tulis | `file.writable()` | `True` jika mode `w`/`a`/`r+` |
