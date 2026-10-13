# BAB 5 - Class Variable dan Docstring

## Apa yang Dipelajari

- **Class variable** : Attribute yang dimiliki oleh **class itu sendiri**, bukan oleh masing-masing objek
- **Perbedaan class variable vs instance variable** : Class variable dibagi semua objek; instance variable milik masing-masing objek
- **Docstring** : Dokumentasi tertulis di dalam kode yang menjelaskan apa yang dilakukan kode tersebut

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
# class
class mahasiswa():

    jumlah_mahasiswa = 0

    def __init__(self, input_nama, input_nim):
        self.nama = input_nama # public
        self.nim = input_nim  # public
        mahasiswa.jumlah_mahasiswa += 1

# main programnya

otong = mahasiswa("otong surotong", 13317001)
ucup = mahasiswa("michael ucup", 13317002)
cassandra = mahasiswa("cassandra aja", 13317002)

print(mahasiswa.jumlah_mahasiswa)
```

### Blok 1: Class Variable

```python
class mahasiswa():

    jumlah_mahasiswa = 0
```

- `jumlah_mahasiswa = 0` - Ini adalah **class variable** (variabel kelas). Didefinisikan **di dalam class tapi di luar method** (tidak ada `self.` di depannya).
- Class variable **dimiliki oleh class itu sendiri** (`mahasiswa.jumlah_mahasiswa`), bukan oleh objek tertentu. Semua objek yang dibuat dari class ini **berbagi** nilai yang sama.
- Default nilainya adalah `0`.

### Blok 2: Constructor yang Memperbarui Class Variable

```python
def __init__(self, input_nama, input_nim):
    self.nama = input_nama # public
    self.nim = input_nim  # public
    mahasiswa.jumlah_mahasiswa += 1
```

- `self.nama` dan `self.nim` adalah **instance variable** - dimiliki masing-masing objek.
- `mahasiswa.jumlah_mahasiswa += 1` - Setiap kali objek baru dibuat, jumlah mahasiswa di class **bertambah 1**. Perhatikan kita menggunakan `mahasiswa.jumlah_mahasiswa` (bukan `self.jumlah_mahasiswa`) untuk memastikan yang diubah adalah milik **class**, bukan milik objek.

### Blok 3: Membuat 3 Objek

```python
otong = mahasiswa("otong surotong", 13317001)    # jumlah_mahasiswa = 1
ucup = mahasiswa("michael ucup", 13317002)       # jumlah_mahasiswa = 2
cassandra = mahasiswa("cassandra aja", 13317002) # jumlah_mahasiswa = 3
```

Setiap kali `mahasiswa(...)` dipanggil, `__init__()` dijalankan dan `jumlah_mahasiswa` bertambah 1.

### Blok 4: Mencetak Class Variable

```python
print(mahasiswa.jumlah_mahasiswa)  # Output: 3
```

- Kita mengakses class variable melalui **nama class** (`mahasiswa.jumlah_mahasiswa`), bukan melalui objek.
- Output: `3` karena ada 3 objek yang dibuat.

### Perbandingan Instance Variable vs Class Variable

| Aspek | Instance Variable | Class Variable |
|---|---|---|
| **Deklarasi** | Di dalam method (`self.nama`) | Di luar method (`jumlah_mahasiswa`) |
| **Dimiliki oleh** | Masing-masing objek | Class (dibagi semua objek) |
| **Contoh** | `self.nama` | `mahasiswa.jumlah_mahasiswa` |
| **Bisa diakses lewat** | `objek.variabel` | `class.variabel` |

### Tentang Docstring

Docstring adalah teks dokumentasi yang ditulis di dalam kode menggunakan tanda kutip tiga (`"""`). Contoh:

```python
class mahasiswa():
    """
    Class mahasiswa untuk menyimpan data mahasiswa.

    Attributes:
        nama (str): Nama mahasiswa
        nim (int): Nomor Induk Mahasiswa
        jumlah_mahasiswa (int): Jumlah total mahasiswa yang terdaftar
    """
    jumlah_mahasiswa = 0
    # ...
```

Docstring bisa diakses dengan `mahasiswa.__doc__` dan membantu programmer lain memahami kode kamu.

## Analogi

Bayangkan **sebuah kelas di sekolah**:

- **Class `mahasiswa`** = Kelas X IPA 1.
- **Instance variable (`nama`, `nim`)** = Nama dan NISN masing-masing siswa. Setiap siswa punya data pribadi sendiri-sendiri.
- **Class variable (`jumlah_mahasiswa`)** = **Papan nama kelas** yang tertulis "Jumlah Siswa: X". Papan ini **satu untuk seluruh kelas**. Ketika ada siswa baru masuk, angka di papan bertambah 1. Papan ini bukan milik satu siswa tertentu, tapi milik **kelas secara keseluruhan**.
- **Docstring** = **Daftar nama siswa** yang ditempel di depan kelas. Berfungsi sebagai dokumentasi agar guru/pengunjung tahu siapa saja yang ada di kelas ini tanpa perlu masuk dan menghitung satu per satu.
