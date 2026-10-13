# BAB 3 - Episode 63: Menggunakan `__main__`

## Apa yang Dipelajari

- Memahami variabel spesial **`__name__`** di Python
- Perbedaan `__name__` saat file dijalankan **langsung** vs saat file **diimpor**
- Menggunakan blok **`if __name__ == "__main__":`** agar kode hanya berjalan saat file dijalankan langsung
- Konsep **package** (folder dengan `__init__.py`)
- File **`__init__.py`** dan **`__main__.py`** dalam sebuah package

---

## Penjelasan Kode

### File: `main_app.py` (File Utama)

```python
print(f"nilai __name__ pada main.py = '{__name__}'")
```

- Setiap file Python memiliki variabel bawaan **`__name__`**.
- Saat file dijalankan **langsung** (`python main_app.py`), maka `__name__` bernilai **`"__main__"`**.
- Ini adalah cara Python menandai "file mana yang menjadi titik awal program".

---

### Mengimpor File Eksternal

```python
import fungsi
```

- Baris ini mengimpor file `fungsi.py` dari **direktori yang sama**.
- Saat `fungsi.py` diimpor, **semua kode di dalamnya langsung dijalankan**.
- Ini penting untuk dipahami: mengimpor module = menjalankan kodenya.

---

### Fungsi dan Blok `__main__`

```python
def fungsi_tambah(a: int, b: int) -> int:
    return a + b

if __name__ == "__main__":
    angka1 = 5
    angka2 = 10
    hasil = fungsi_tambah(angka1, angka2)
    print(f"hasil tambah = {hasil}")
```

**Pembahasan per baris:**

| Baris | Penjelasan |
|---|---|
| `def fungsi_tambah(a: int, b: int) -> int:` | Mendefinisikan fungsi dengan **type hint**: parameter `a` dan `b` harus `int`, mengembalikan `int` |
| `return a + b` | Mengembalikan hasil penjumlahan `a + b` |
| `if __name__ == "__main__":` | **Kondisi khusus**: kode di dalamnya HANYA berjalan jika file ini dijalankan langsung |
| `angka1 = 5` | Menetapkan variabel `angka1` bernilai 5 |
| `angka2 = 10` | Menetapkan variabel `angka2` bernilai 10 |
| `hasil = fungsi_tambah(angka1, angka2)` | Memanggil fungsi → menghasilkan 15 |
| `print(f"hasil tambah = {hasil}")` | Mencetak: `hasil tambah = 15` |

> **Kenapa pakai `if __name__ == "__main__":`?**
> Agar kode percobaan di dalamnya **tidak ikut berjalan** saat file ini diimpor oleh file lain. Ini adalah best practice di Python.

---

### Mengimpor Package

```python
import package
```

- `package` adalah **folder** (bukan file `.py`) yang dijadikan package karena memiliki file `__init__.py` di dalamnya.

---

### File: `fungsi.py`

```python
print(f"nilai __name__ pada fungsi.py = '{__name__}'")
```

- Saat `fungsi.py` diimpor oleh `main_app.py`, `__name__` bernilai **`"fungsi"`** (nama modulnya).
- Ini berbeda dengan file utama yang `__name__`-nya `"__main__"`.
- Jadi saat `main_app.py` dijalankan, output-nya:
  ```
  nilai __name__ pada main.py = '__main__'
  nilai __name__ pada fungsi.py = 'fungsi'
  ```

---

### Struktur Folder `package/`

```
package/
├── __init__.py      ← File kosong, menandakan folder ini adalah package
├── __main__.py      ← Kode yang dijalankan saat package dijalankan langsung
├── module.py        ← Module lain (kosong untuk saat ini)
```

#### File `package/__init__.py`

```python
# (kosong)
```

- File `__init__.py` **wajib ada** di dalam folder agar Python mengenali folder tersebut sebagai **package**.
- Bisa kosong atau berisi kode inisialisasi package.

#### File `package/__main__.py`

```python
print("ini adalah main dari package")
print("package ini berfungsi untuk")
print(f"nilai __name__ = '{__name__}'")
```

- `__main__.py` adalah file khusus yang **otomatis dijalankan** saat package dijalankan langsung dari terminal:
  ```
  python package
  ```
- `__name__` bernilai `"__main__"` karena package dijalankan langsung.

#### File `package/module.py`

```python
# (kosong)
```

- Module kosong, siap diisi kode nanti.

---

### Bagaimana `__name__` Bekerja?

```
┌─────────────────────────────────────────────────────┐
│  python main_app.py                                │
│                                                     │
│  main_app.py  → __name__ = "__main__"  (dijalankan) │
│  fungsi.py    → __name__ = "fungsi"    (diimpor)    │
│  package/     → __name__ = "package"   (diimpor)    │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│  python package                                     │
│                                                     │
│  package/__main__.py → __name__ = "__main__"        │
└─────────────────────────────────────────────────────┘
```

---

### Output Program

```
nilai __name__ pada main.py = '__main__'
nilai __name__ pada fungsi.py = 'fungsi'
hasil tambah = 15
ini adalah main dari package
package ini berfungsi untuk
nilai __name__ = '__main__'
```

---

## Analogi

Bayangkan **buku resep masakan**:

- **`__name__ == "__main__"`** = Kamu **memasak sendiri** di rumah. Resep itu kamu pakai langsung.
- **`import fungsi`** = Kamu **meminjam resep** dari teman. Kamu tidak memasak semua resepnya, tapi kamu bisa memanggil resep tertentu.
- **`package`** = Sebuah **buku kumpulan resep**. Di dalamnya ada banyak chapter (module). Kalau kamu beli bukunya langsung (`python package`), kamu membuka halaman utama (`__main__.py`). Kalau kamu cuma pinjam satu chapter (`import package.module`), kamu cuma baca chapter itu saja.

> `if __name__ == "__main__":` seperti **tulisan di awal resep**: "Masak langsung jika kamu mau makan sekarang." Kalau kamu cuma meminjam repet untuk ditulis ulang, bagian itu tidak perlu kamu ikuti.

---

## Ringkasan Konsep Penting

| Konsep | Penjelasan |
|---|---|
| `__name__` | Variabel bawaan Python yang bernilai `"__main__"` jika file dijalankan langsung, atau nama modul jika diimpor |
| `if __name__ == "__main__":` | Blok kode yang hanya berjalan saat file dijalankan langsung |
| `__init__.py` | File penanda bahwa folder adalah package Python |
| `__main__.py` | File yang dijalankan saat package dijalankan langsung (`python nama_package`) |
| `import module` | Mengimpor module → menjalankan semua kode di module tersebut |
| Type hint | `def f(a: int) -> int:` → petunjuk tipe data untuk parameter dan return value |
