# BAB 1 - Pengenalan Class

## Apa yang Dipelajari

- **Class** : Sebuah cetak biru/blueprint untuk membuat objek
- **Object** : Instance (contoh nyata) dari sebuah class
- **Attribute** : Data/property yang dimiliki oleh sebuah objek

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
class Mahasiswa():
    nama = 'nama'

otong = Mahasiswa()
ucup = Mahasiswa()

otong.nama = "otong surotong"
ucup.nama = "michael ucup"

print(otong.nama)
print(ucup.nama)
```

### Blok 1: Mendefinisikan Class

```python
class Mahasiswa():
    nama = 'nama'
```

- `class Mahasiswa():` - Mendefinisikan sebuah class bernama `Mahasiswa`. Kata kunci `class` digunakan untuk membuat class baru. Nama class diawali dengan huruf kapital (PascalCase). Tanda kurung `()` setelah nama class bersifat opsional di Python 3.
- `nama = 'nama'` - Mendefinisikan sebuah **attribute** (atribut) bernama `nama` dengan nilai default berupa string `'nama'`. Ini berarti setiap objek yang dibuat dari class `Mahasiswa` akan memiliki atribut `nama` dengan nilai awal `'nama'`.

### Blok 2: Membuat Object (Instance)

```python
otong = Mahasiswa()
ucup = Mahasiswa()
```

- `otong = Mahasiswa()` - Membuat sebuah **objek** (instance) dari class `Mahasiswa` dan menyimpannya di variabel `otong`. Proses ini disebut **instansiasi**. Setiap objek memiliki salinan atribut `nama` sendiri-sendiri.
- `ucup = Mahasiswa()` - Membuat objek kedua dari class `Mahasiswa` yang sama, disimpan di variabel `ucup`. `ucup` dan `otong` adalah dua objek terpisah meskipun berasal dari class yang sama.

### Blok 3: Mengubah Nilai Attribute

```python
otong.nama = "otong surotong"
ucup.nama = "michael ucup"
```

- `otong.nama = "otong surotong"` - Mengubah nilai atribut `nama` pada objek `otong` dari `'nama'` menjadi `"otong surotong"`. Kita menggunakan **dot notation** (`objek.atribut`) untuk mengakses dan mengubah atribut.
- `ucup.nama = "michael ucup"` - Sama seperti di atas, tapi untuk objek `ucup`.

### Blok 4: Mencetak Output

```python
print(otong.nama)
print(ucup.nama)
```

- `print(otong.nama)` - Mencetak nilai atribut `nama` dari objek `otong`, yaitu `"otong surotong"`.
- `print(ucup.nama)` - Mencetak nilai atribut `nama` dari objek `ucup`, yaitu `"michael ucup"`.

**Output:**
```
otong surotong
michael ucup
```

## Analogi

Bayangkan sebuah **formulir pendaftaran sekolah**:

- **Class `Mahasiswa`** = Cetak biru formulir pendaftaran. Di dalamnya sudah ada kolom `nama` (attribute) yang harus diisi.
- **Objek `otong`** = Formulir pendaftaran milik Otong. Kolom `nama` diisi "otong surotong".
- **Objek `ucup`** = Formulir pendaftaran milik Ucup. Kolom `nama` diisi "michael ucup".

Setiap siswa punya formulir sendiri-sendiri, meskipun format formulirnya sama (dari class yang sama). Nilai attribute pada satu objek **tidak mempengaruhi** objek lainnya.
