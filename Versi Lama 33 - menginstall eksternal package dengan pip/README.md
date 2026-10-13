# BAB 9 - Menginstall Eksternal Package dengan Pip

## Apa yang Dipelajari

- **Package eksternal** : Package/pustaka Python yang tidak bawaan (built-in) dan harus diinstall secara terpisah
- **`pip`** : Package manager bawaan Python untuk menginstall, mengupdate, dan menghapus package
- **`PIL / Pillow`** : Library untuk memproses gambar (Image) dalam Python
- **`import`** : Cara menggunakan package yang sudah diinstall

## Penjelasan Kode

### Langkah 1: Menginstall Package

Sebelum menjalankan kode, package `Pillow` harus diinstall terlebih dahulu melalui terminal:

```bash
pip install Pillow
```

| Perintah | Fungsi |
|----------|--------|
| `pip install nama_package` | Menginstall package |
| `pip install --upgrade nama_package` | Mengupdate package ke versi terbaru |
| `pip uninstall nama_package` | Menghapus package |
| `pip list` | Melihat semua package yang terinstall |

### Langkah 2: Kode Program

Berikut adalah kode lengkap dari program ini:

```python
from PIL import Image

im = Image.open("foto.jpg")

print("format file: " + im.format)
print("ukuran file: " + str(im.size))
print("mode file: " + im.mode)

im.show()
```

### Blok 1: Import Package

```python
from PIL import Image
```

- `from PIL import Image` - Mengimport **modul `Image`** dari package `PIL` (Pillow). `PIL` adalah nama package-nya, sedangkan `Image` adalah modul di dalamnya yang berfungsi untuk membaca, memanipulasi, dan menyimpan gambar.
- `from ... import ...` hanya mengimport modul tertentu, bukan seluruh package. Ini lebih efisien daripada `import PIL`.

### Blok 2: Membuka Gambar

```python
im = Image.open("foto.jpg")
```

- `Image.open("foto.jpg")` - Membuka file gambar `foto.jpg` dari direktori yang sama dengan file Python.
- `im` - Variabel yang menyimpan objek gambar. Objek ini berisi semua informasi tentang gambar: format, ukuran, mode warna, dsb.

### Blok 3: Mencetak Informasi Gambar

```python
print("format file: " + im.format)
print("ukuran file: " + str(im.size))
print("mode file: " + im.mode)
```

- `im.format` - Mendapatkan format file gambar (contoh: `JPEG`, `PNG`, `GIF`).
- `im.size` - Mendapatkan ukuran gambar dalam format **tupel** `(lebar, tinggi)` dalam piksel. Karena `im.size` berupa tuple (bukan string), kita harus mengonversinya dengan `str()` agar bisa digabungkan dengan string.
- `im.mode` - Mendapatkan mode warna gambar (contoh: `RGB` untuk warna, `L` untuk grayscale, `RGBA` untuk warna dengan transparansi).

**Contoh output:**
```
format file: JPEG
ukuran file: (800, 600)
mode file: RGB
```

### Blok 4: Menampilkan Gambar

```python
im.show()
```

- `im.show()` - Membuka gambar menggunakan **application viewer default** di sistem operasi (misalnya Windows Photo Viewer di Windows, Preview di Mac).

## Perbedaan Package Built-in vs Eksternal

| Aspek | Built-in (contoh: `tkinter`) | Eksternal (contoh: `PIL/Pillow`) |
|-------|------|------|
| **Sudah ada?** | Ya, otomatis ada di Python | Tidak, harus diinstall manual |
| **Cara install** | Tidak perlu | `pip install nama_package` |
| **Import** | `import tkinter` | `from PIL import Image` |
| **Contoh lain** | `os`, `sys`, `math` | `numpy`, `pandas`, `requests` |

## Analogi

Bayangkan **membeli peralatan masak**:

- **Package built-in (`tkinter`, `os`)** = **Peralatan yang sudah ada di dapur** saat kamu pindah ke rumah baru: kompor, panci, spatula. Langsung bisa dipakai.
- **Package eksternal (`Pillow`)** = **Peralatan khusus** seperti mesin kopi atau blender. Kamu harus **pergi ke toko** (pip) dan **beli/install** dulu sebelum bisa dipakai.
- **`pip install Pillow`** = Pergi ke toko dan membeli blender.
- **`from PIL import Image`** = Mengeluarkan blender dari kardus dan siap dipakai.
- **`im.show()`** = Menyalakan blender dan melihat hasilnya.

> **Tips:** Selalu cek apakah package sudah ada di Python sebelum install. Beberapa package sudah built-in (seperti `os`, `math`, `random`) dan tidak perlu diinstall.
