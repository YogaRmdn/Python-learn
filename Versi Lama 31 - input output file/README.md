# BAB 7 - Input Output File

## Apa yang Dipelajari

- **Membuka file** : Fungsi `open()` dengan berbagai mode
- **Mode file** : `w` (write), `r` (read), `a` (append), `r+` (read & write)
- **Menulis file** : Fungsi `write()` untuk menulis teks ke file
- **Membaca file** : Fungsi `read()` dan `readline()` untuk membaca isi file
- **Menutup file** : Fungsi `close()` untuk menutup file setelah selesai digunakan

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
# input output file

"""
w = write mode / mode menulis dan menghapus file lama, jika file tidak ada maka akan dibuat file baru
r = read mode only / hanya bisa baca
a = appending mode / menambahkan data di akhir baris
r+ = write and read mode
"""

# membuat file text

file = open("data.txt",'w')

file.write("ini adalah data text yang dibuat dengan menggunakan python")
file.write("\nini baris kedua")
file.write("\nini baris ketiga")
file.write("\nini baris keempat")

file.close()

# membaca file text

file2 = open("data.txt",'r')

print(file2.readline())

file2.close()

# appending mode

file3 = open("data.txt", 'a')

file3.write("\nbaris ini dibuat dengan menggunakan mode append")

file3.close()
```

### Blok 1: Penjelasan Mode File (Docstring)

```python
"""
w = write mode / mode menulis dan menghapus file lama, jika file tidak ada maka akan dibuat file baru
r = read mode only / hanya bisa baca
a = appending mode / menambahkan data di akhir baris
r+ = write and read mode
"""
```

| Mode | Nama | Fungsi |
|------|------|--------|
| `'w'` | Write | Menulis file. **Menghapus isi file lama**. Jika file belum ada, membuat file baru. |
| `'r'` | Read | Membaca file. File harus sudah ada. Ini mode default. |
| `'a'` | Append | Menambahkan data di **akhir** file. Tidak menghapus data lama. |
| `'r+'` | Read+Write | Bisa membaca dan menulis. File harus sudah ada. |

### Blok 2: Menulis File (Write Mode)

```python
file = open("data.txt",'w')
```

- `open("data.txt", 'w')` - Membuka file `data.txt` dalam mode write. Jika file belum ada, akan dibuat baru. Jika sudah ada, **isi lamanya dihapus**.
- `file` - Variabel yang menyimpan "file handle" (pengendali file) yang bisa digunakan untuk berinteraksi dengan file.

```python
file.write("ini adalah data text yang dibuat dengan menggunakan python")
file.write("\nini baris kedua")
file.write("\nini baris ketiga")
file.write("\nini baris keempat")
```

- `file.write("...")` - Menulis teks ke dalam file. Setiap pemanggilan `write()` menambahkan teks setelah teks sebelumnya. **Tidak otomatis menambahkan baris baru** - kita harus menambahkan `\n` secara manual.

```python
file.close()
```

- `file.close()` - **Sangat penting!** Menutup file setelah selesai menulis. Ini memastikan semua data benar-benar tersimpan ke disk. Jika lupa `close()`, data mungkin tidak tersimpan.

**Isi `data.txt` setelah blok ini:**
```
ini adalah data text yang dibuat dengan menggunakan python
ini baris kedua
ini baris ketiga
ini baris keempat
```

### Blok 3: Membaca File (Read Mode)

```python
file2 = open("data.txt",'r')
print(file2.readline())
file2.close()
```

- `open("data.txt", 'r')` - Membuka file dalam mode read (hanya baca).
- `file2.readline()` - Membaca **satu baris** dari file (sampai menemukan `\n`). Baris pertama yang dibaca adalah: `"ini adalah data text yang dibuat dengan menggunakan python"`.
- `file2.close()` - Menutup file.

> **Catatan:** Ada juga `file2.read(n)` untuk membaca `n` karakter sekaligus, atau `file2.read()` tanpa parameter untuk membaca seluruh isi file.

### Blok 4: Mode Append

```python
file3 = open("data.txt", 'a')
file3.write("\nbaris ini dibuat dengan menggunakan mode append")
file3.close()
```

- `open("data.txt", 'a')` - Membuka file dalam mode **append**. Data baru akan ditambahkan di **akhir** file tanpa menghapus data yang sudah ada.
- `file3.write("\nbaris ini dibuat dengan menggunakan mode append")` - Menambahkan baris baru di akhir file.

**Isi `data.txt` setelah blok ini (lengkap):**
```
ini adalah data text yang dibuat dengan menggunakan python
ini baris kedua
ini baris ketiga
ini baris keempat
baris ini dibuat dengan menggunakan mode append
```

## Analogi

Bayangkan **buku catatan**:

- **Mode `w` (write)** = Membeli buku baru yang masih kosong, atau **menghapus semua isi** buku lama dan menulis ulang dari awal. Hati-hati: semua data lama hilang!
- **Mode `r` (read)** = Membuka buku dan **membaca** isinya. Tidak ada yang berubah.
- **Mode `a` (append)** = Membuka buku dan **menambahkan tulisan di halaman terakhir**. Isi lama tetap aman.
- **`file.close()`** = **Menutup buku** dan meletakkannya kembali di rak. Jika lupa menutup, buku tetap terbuka di meja dan bisa terkena tumpahan kopi (data bisa rusak/corrupt).

> **Tips:** Dalam praktik nyata, lebih baik menggunakan `with open(...) as file:` agar file otomatis ditutup meskipun terjadi error. Ini akan dipelajari di materi selanjutnya.
