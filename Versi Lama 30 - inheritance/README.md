# BAB 6 - Inheritance

## Apa yang Dipelajari

- **Inheritance (Pewarisan)** : Kemampuan class anak untuk mewarisi attribute dan method dari class induk
- **Parent class (superclass)** : Class yang diwarisi
- **Child class (subclass)** : Class yang mewarisi
- **Method overriding** : Child class mengganti method yang diwarisi dari parent class

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
class Ojek():

    def __init__(self, nama, transmisi, daerah):
        self.nama = nama
        self.transmisi = transmisi
        self.daerah = daerah

    def cek_id_abang(self):
        print('nama:',self.nama,'\nmotor:',self.transmisi,'\ndaerah:',self.daerah)

class Gojek(Ojek):

    def cek_id_abang(self):
        print('cek aplikasi gojek')


ojek1 = Ojek('mario','manual','bandung selatan')
ojek2 = Gojek('jackson','automatic','tasikmalaya')

ojek1.cek_id_abang()
ojek2.cek_id_abang()
```

### Blok 1: Parent Class (Class Induk)

```python
class Ojek():

    def __init__(self, nama, transmisi, daerah):
        self.nama = nama
        self.transmisi = transmisi
        self.daerah = daerah

    def cek_id_abang(self):
        print('nama:',self.nama,'\nmotor:',self.transmisi,'\ndaerah:',self.daerah)
```

- `class Ojek():` - Mendefinisikan **parent class** (class induk) bernama `Ojek`.
- `__init__(self, nama, transmisi, daerah)` - Constructor yang menerima tiga parameter: nama driver, jenis transmisi motor, dan daerah operasi.
- `self.nama = nama`, `self.transmisi = transmisi`, `self.daerah = daerah` - Mengisi attribute dari parameter.
- `cek_id_abang(self)` - Method yang mencetak identitas abang ojek: nama, motor, dan daerah.

### Blok 2: Child Class (Class Anak)

```python
class Gojek(Ojek):

    def cek_id_abang(self):
        print('cek aplikasi gojek')
```

- `class Gojek(Ojek):` - Mendefinisikan **child class** bernama `Gojek` yang **mewarisi** dari parent class `Ojek`. Parameter `(Ojek)` di nama class berarti `Gojek` adalah anak dari `Ojek`.
- `Gojek` **mewarisi SEMUA** attribute dan method dari `Ojek`, termasuk `__init__()` dan `cek_id_abang()`.
- `def cek_id_abang(self):` - Child class **mengoverride** (mengganti) method `cek_id_abang` dari parent. Sekarang method ini mencetak `"cek aplikasi gojek"` alih-alih data driver.

### Blok 3: Membuat Object

```python
ojek1 = Ojek('mario','manual','bandung selatan')
ojek2 = Gojek('jackson','automatic','tasikmalaya')
```

- `ojek1` adalah objek dari parent class `Ojek` biasa.
- `ojek2` adalah objek dari child class `Gojek`. Perhatikan `Gojek` tidak punya `__init__()` sendiri, tapi **tetap bisa** menerima 3 parameter karena mewarisi `__init__()` dari `Ojek`.

### Blok 4: Memanggil Method

```python
ojek1.cek_id_abang()
```

- `ojek1` adalah objek `Ojek`, jadi menggunakan method `cek_id_abang` versi `Ojek`:
  ```
  nama: mario
  motor: manual
  daerah: bandung selatan
  ```

```python
ojek2.cek_id_abang()
```

- `ojek2` adalah objek `Gojek`, jadi menggunakan method `cek_id_abang` versi `Gojek` (yang sudah di-override):
  ```
  cek aplikasi gojek
  ```

### Ringkasan Alur Pewarisan

```
Ojek (parent)
├── __init__(nama, transmisi, daerah)  ← diwarisi Gojek
├── cek_id_abang()                     ← di-override oleh Gojek
│
Gojek(Ojek) (child)
├── __init__()    ← diwarisi dari Ojek (tidak diubah)
├── cek_id_abang() ← VERSI BARU: "cek aplikasi gojek"
```

## Analogi

Bayangkan **kendaraan**:

- **Parent class `Ojek`** = Kendaraan biasa. Punya nama driver, jenis motor, dan daerah operasi. Cara cek identitas: lihat langsung di stiker motor.
- **Child class `Gojek`** = Ojek online. **Mewarisi** semua data dari ojek biasa (nama, motor, daerah), tapi **cara cek identitasnya beda**: tidak perlu lihat stiker, cukup buka **aplikasi Gojek** di HP.

Inilah kekuatan inheritance: kita tidak perlu mendefinisikan ulang attribute dan method yang sudah ada di parent class. Child class tinggal **mewarisi** yang sudah ada dan **mengubah** apa yang perlu diubah.
