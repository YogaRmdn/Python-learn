# BAB 2 - Membuat Method

## Apa yang Dipelajari

- **Method** : Fungsi yang didefinisikan di dalam sebuah class
- **Parameter `self`** : Referensi ke objek itu sendiri yang selalu menjadi parameter pertama method
- **Memanggil method** : Cara memanggil fungsi yang ada di dalam class melalui objek

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
#class
class Mahasiswa():
    nama = 'nama'

    def belajar(self, kondisi):
        print(self.nama,'sedang belajar', kondisi)

    def tidur(self):
        print(self.nama,'tidur di kelas')

# main programnya

otong = Mahasiswa()
ucup = Mahasiswa()

otong.nama = "otong surotong"
ucup.nama = "michael ucup"

otong.belajar('dengan giat')
ucup.tidur()
```

### Blok 1: Class dengan Method

```python
class Mahasiswa():
    nama = 'nama'

    def belajar(self, kondisi):
        print(self.nama,'sedang belajar', kondisi)

    def tidur(self):
        print(self.nama,'tidur di kelas')
```

- `class Mahasiswa():` - Mendefinisikan class `Mahasiswa`.
- `nama = 'nama'` - Attribute default bernama `nama`.
- `def belajar(self, kondisi):` - Mendefinisikan sebuah **method** bernama `belajar` di dalam class.
  - `self` - Parameter wajib yang merepresentasikan **objek itu sendiri**. Dengan `self`, method bisa mengakses attribute dan method lain dari objek yang memanggilnya.
  - `kondisi` - Parameter tambahan yang bisa dikirim saat method dipanggil.
  - `print(self.nama,'sedang belajar', kondisi)` - Mencetak nama objek (`self.nama`), teks `'sedang belajar'`, dan nilai parameter `kondisi`.
- `def tidur(self):` - Mendefinisikan method `tidur` yang hanya butuh parameter `self`.
  - `print(self.nama,'tidur di kelas')` - Mencetak bahwa si mahasiswa sedang tidur di kelas.

### Blok 2: Membuat Object

```python
otong = Mahasiswa()
ucup = Mahasiswa()

otong.nama = "otong surotong"
ucup.nama = "michael ucup"
```

- Membuat dua objek dari class `Mahasiswa` dan mengatur nilai atribut `nama` masing-masing. (Sama seperti BAB 1.)

### Blok 3: Memanggil Method

```python
otong.belajar('dengan giat')
ucup.tidur()
```

- `otong.belajar('dengan giat')` - Memanggil method `belajar` pada objek `otong` dengan parameter `kondisi = 'dengan giat'`.
  - Output: `otong surotong sedang belajar dengan giat`
- `ucup.tidur()` - Memanggil method `tidur` pada objek `ucup`.
  - Output: `michael ucup tidur di kelas`

## Analogi

Bayangkan **Mahasiswa** adalah sebuah robot:

- **Attribute `nama`** = Label nama yang ditempel di dada robot.
- **Method `belajar`** = Tombol "Aktifkan Mode Belajar". Saat ditekan, robot akan menyapa dengan namanya dan mengatakan sedang belajar dalam kondisi tertentu.
- **Method `tidur`** = Tombol "Aktifkan Mode Tidur". Robot akan mengatakan bahwa dia sedang tidur di kelas.
- **Parameter `self`** = Setiap robot tahu **siapa dirinya sendiri**. `self` seperti robot yang melihat ke cermin dan mengenali namanya sendiri sebelum berbicara.

Tanpa `self`, method tidak tahu milik objek siapa yang sedang dijalankan. Bayangkan robot yang berbicara tapi tidak tahu namanya sendiri - pasti kacau!
