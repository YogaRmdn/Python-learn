# BAB 3 - Menggunakan `__init__()`

## Apa yang Dipelajari

- **`__init__()`** : Method khusus (constructor) yang otomatis dipanggil saat objek dibuat
- **Constructor** : Fungsi pembuat objek yang bisa langsung mengisi attribute
- **Parameter instance** : Nilai yang dikirim saat pembuatan objek

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
#class
class Mahasiswa():
    nama = 'nama'

    def __init__(self, input_nama, input_nim):
        self.nama = input_nama
        self.nim = input_nim

    def belajar(self, kondisi):
        print(self.nama,'sedang belajar', kondisi)

    def tidur(self):
        print(self.nama,'tidur di kelas')

# main programnya

otong = Mahasiswa("otong surotong", 13317001)

print(otong.nama)
otong.nama = "atong suratang"
print(otong.nama)

otong.belajar('dengan giat')
```

### Blok 1: Method `__init__()`

```python
class Mahasiswa():
    nama = 'nama'

    def __init__(self, input_nama, input_nim):
        self.nama = input_nama
        self.nim = input_nim
```

- `def __init__(self, input_nama, input_nim):` - Mendefinisikan **constructor** (pembuat objek). Method `__init__()` adalah method khusus yang **otomatis dipanggil** oleh Python setiap kali objek baru dibuat dari class.
  - `self` - Referensi ke objek yang baru saja dibuat.
  - `input_nama` - Parameter untuk nama mahasiswa.
  - `input_nim` - Parameter untuk NIM (Nomor Induk Mahasiswa).
- `self.nama = input_nama` - Mengisi attribute `nama` objek dengan nilai dari parameter `input_nama`.
- `self.nim = input_nim` - Membuat attribute baru bernama `nim` dan mengisinya dengan nilai dari parameter `input_nim`.

> **Perbedaan dengan BAB 1-2:** Sebelumnya, kita harus mengisi attribute secara terpisah setelah objek dibuat. Dengan `__init__()`, attribute bisa langsung diisi saat objek dibuat.

### Blok 2: Membuat Object dengan Parameter

```python
otong = Mahasiswa("otong surotong", 13317001)
```

- Saat baris ini dijalankan, Python akan:
  1. Membuat objek baru dari class `Mahasiswa`.
  2. Memanggil `__init__(self, "otong surotong", 13317001)`.
  3. `self.nama` menjadi `"otong surotong"`.
  4. `self.nim` menjadi `13317001`.

### Blok 3: Mengubah dan Mencetak Attribute

```python
print(otong.nama)           # Output: otong surotong
otong.nama = "atong suratang"
print(otong.nama)           # Output: atong suratang
```

- Attribute tetap bisa diubah kapan saja menggunakan **dot notation**.

### Blok 4: Memanggil Method

```python
otong.belajar('dengan giat')
```

- Output: `otong surotong sedang belajar dengan giat`

## Analogi

Bayangkan **membuat Kartu Tanda Mahasiswa (KTM)**:

- **`__init__()`** = Mesin cetak KTM. Saat kamu mendaftar, mesin ini langsung mencetak KTM dengan nama dan NIM yang kamu berikan. Tidak perlu mengisi datanya satu per satu secara manual.
- **Sebelum `__init__` (BAB 1-2)** = Kamu dapat KTM kosong, lalu harus menulis nama dan NIM sendiri pakai pulpen.
- **Setelah `__init__`** = Kamu serahkan foto dan data ke petugas, KTM langsung jadi dengan data lengkap.

**Kenapa `__init__()` dinamakan "init"?** Karena singkatan dari *initialize* (inisialisasi) yang berarti "mengisi nilai awal". Method ini memastikan setiap objek lahir dengan data yang lengkap dan benar.
