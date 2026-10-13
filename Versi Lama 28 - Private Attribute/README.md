# BAB 4 - Private Attribute

## Apa yang Dipelajari

- **Private attribute** : Attribute yang hanya bisa diakses dari dalam class (dengan awalan `__`)
- **Name mangling** : Mekanisme Python untuk "menyembunyikan" attribute private
- **Public vs Private** : Perbedaan attribute yang bisa diakses dari luar class vs yang tidak bisa
- **Enkapsulasi** : Konsep OOP untuk membatasi akses ke data internal

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
# class
class mahasiswa():

    jurusan = "teknik tata boga"
    __nilai = 0 # private

    def __init__(self, input_nama, input_nim):
        self.nama = input_nama # public
        self.nim = input_nim  # public

    def uts(self,input_nilai):
        self.__nilai += input_nilai

    def uas(self,input_nilai):
        self.__nilai += input_nilai

    def check_status(self):
        if self.__nilai <= 50:
            print(self.nama,'tidak lulus')
        else:
            print(self.nama, 'lulus')

# main programnya

otong = mahasiswa("otong surotong", 13317001)
ucup = mahasiswa("michael ucup", 13317002)

otong.uts(10)
otong.uas(50)
otong.check_status()
ucup.uts(5)
ucup.uas(25)
ucup.__nilai = 60
ucup.check_status()
```

### Blok 1: Attribute Public vs Private

```python
class mahasiswa():

    jurusan = "teknik tata boga"
    __nilai = 0 # private
```

- `jurusan = "teknik tata boga"` - Attribute **public**. Bisa diakses dari mana saja (di dalam maupun di luar class).
- `__nilai = 0` - Attribute **private**. Ditandai dengan dua garis bawah ganda `__` di depan nama. Hanya bisa diakses dari **dalam class itu sendiri**. Jika coba diakses dari luar, akan muncul error.

### Blok 2: Constructor

```python
def __init__(self, input_nama, input_nim):
    self.nama = input_nama # public
    self.nim = input_nim  # public
```

- `self.nama` dan `self.nim` adalah attribute **public** - bisa diakses dari luar class.
- Tidak ada attribute private di constructor karena `__nilai` sudah didefinisikan langsung di class.

### Blok 3: Method yang Mengakses Private Attribute

```python
def uts(self,input_nilai):
    self.__nilai += input_nilai

def uas(self,input_nilai):
    self.__nilai += input_nilai

def check_status(self):
    if self.__nilai <= 50:
        print(self.nama,'tidak lulus')
    else:
        print(self.nama, 'lulus')
```

- `self.__nilai += input_nilai` - Method `uts()` dan `uas()` bisa mengakses `__nilai` karena berada **di dalam class**. Nilai input ditambahkan ke `__nilai`.
- `check_status()` - Mengecek apakah total nilai ≤ 50 (tidak lulus) atau > 50 (lulus). Juga mengakses `__nilai` dari dalam class.

### Blok 4: Percobaan Mengakses Private dari Luar

```python
otong.uts(10)          # __nilai otong = 0 + 10 = 10
otong.uas(50)          # __nilai otong = 10 + 50 = 60
otong.check_status()   # Output: otong surotong lulus (60 > 50)

ucup.uts(5)            # __nilai ucup = 0 + 5 = 5
ucup.uas(25)           # __nilai ucup = 5 + 25 = 30
ucup.__nilai = 60      # INI TIDAK MENGUBAH __nilai yang sebenarnya!
ucup.check_status()    # Output: michael ucup tidak lulus (masih 30, bukan 60)
```

> **PENTING:** Baris `ucup.__nilai = 60` **tidak mengubah** attribute `__nilai` yang asli! Yang terjadi adalah Python membuat attribute **baru** bernama `ucup.__nilai` (berbeda dari `__nilai` di class). Ini adalah efek dari **name mangling**. Nilai `__nilai` ucup tetap 30.

### Hasil Output

```
otong surotong lulus
michael ucup tidak lulus
```

## Analogi

Bayangkan **rekening bank**:

- **Attribute public (`nama`)** = Nama kamu yang tertera di kartu ATM. Siapa saja bisa melihatnya.
- **Attribute private (`__nilai`)** = Saldo rekening bank. Hanya **kamu dan bank** (class `mahasiswa`) yang bisa mengubahnya.
- **Method `uts()` dan `uas()`** = Mesin ATM. Satu-satunya cara yang sah untuk menambah/mengurangi saldo adalah melalui mesin ATM (method di dalam class).
- **`ucup.__nilai = 60`** = Seperti kamu menulis di secarik kertas "Saldo saya Rp60.000.000" dan menempelkannya di dinding. Itu **tidak mengubah saldo asli** di bank! Saldo tetapRp30.000.000 karena bank tidak mengenali cara itu.

Inilah inti dari **enkapsulasi**: data sensitif dilindungi dan hanya bisa diubah melalui jalur yang resmi (method).
