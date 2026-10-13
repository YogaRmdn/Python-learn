# BAB 2 - Multikey Dictionary (Nested Dictionary)

## Apa yang Dipelajari

- Membuat **dictionary bersarang** (nested dictionary), yaitu dictionary di dalam dictionary
- Mengakses data multi-level dari nested dictionary
- Menggunakan `datetime` untuk menyimpan tanggal lahir
- Menampilkan data dalam format tabel rapi menggunakan **f-string formatting**

---

## Penjelasan Kode

### File: `Main.py`

#### 1. Import Module datetime

```python
import datetime
```

- `datetime` adalah module bawaan Python untuk bekerja dengan tanggal dan waktu.
- Digunakan untuk menyimpan data tanggal lahir mahasiswa.

#### 2. Membuat Dictionary Mahasiswa (Data Level 1)

```python
mahasiswa1 = {
    'nama':'Ucup Surucup',
    'nim':'19022001',
    'sks_lulus':130,
    'beasiswa':False,
    'lahir':datetime.datetime(2001,4,10)
}
```

- Setiap mahasiswa punya dictionary sendiri dengan key:
  - `'nama'` -> string nama lengkap
  - `'nim'` -> string NIM (Nomor Induk Mahasiswa)
  - `'sks_lulus'` -> integer jumlah SKS yang sudah lulus
  - `'beasiswa'` -> boolean (`True`/`False`), apakah dapat beasiswa
  - `'lahir'` -> objek `datetime` untuk tanggal lahir (tahun, bulan, tanggal)

```python
mahasiswa2 = {
    'nama':'Otong Surotong',
    'nim':'19022002',
    'sks_lulus':140,
    'beasiswa':True,
    'lahir':datetime.datetime(2002,10,10)
}

mahasiswa3 = {
    'nama':'Asep Si Kasyep',
    'nim':'19022003',
    'sks_lulus':100,
    'beasiswa':False,
    'lahir':datetime.datetime(2000,2,29)
}
```

- Tiga mahasiswa dibuat dengan data yang berbeda-beda.

#### 3. Membuat Dictionary Bersarang (Nested Dictionary)

```python
data_mahasiswa = {
    'MAH001':mahasiswa1,
    'MAH002':mahasiswa2,
    'MAH003':mahasiswa3
}
```

- `data_mahasiswa` adalah **dictionary level atas**.
- Setiap **key** (`'MAH001'`, `'MAH002'`, `'MAH003'`) memiliki **value** berupa dictionary mahasiswa.
- Inilah yang disebut **nested dictionary** (dictionary bersarang).
- Strukturnya seperti ini:
  ```
  data_mahasiswa
    ├── 'MAH001' → {nama: 'Ucup', nim: '19022001', ...}
    ├── 'MAH002' → {nama: 'Otong', nim: '19022002', ...}
    └── 'MAH003' → {nama: 'Asep', nim: '19022003', ...}
  ```

#### 4. Menampilkan Header Tabel

```python
print(f"{'KEY':<6} {'Nama':<17} {'SKS':<3} {'Beasiswa':<9} {'Lahir':<10}")
print("-"*50)
```

- F-string formatting digunakan untuk membuat **header tabel** yang rapi.
- `:<6` berarti teks **rata kiri** dengan lebar 6 karakter.
- `:-`50`` membuat garis putus-putus sepanjang 50 karakter sebagai pemisah.

#### 5. Looping dan Mengakses Data Multi-Level

```python
for mahasiswa in data_mahasiswa:
    KEY = mahasiswa

    NAMA = data_mahasiswa[KEY]['nama']
    NIM = data_mahasiswa[KEY]['nim']
    SKS = data_mahasiswa[KEY]['sks_lulus']
    BEASISWA = data_mahasiswa[KEY]['beasiswa']
    LAHIR = data_mahasiswa[KEY]['lahir'].strftime("%x")

    print(f"{KEY:<6} {NAMA:<17} {SKS:<3} {BEASISWA:^9} {LAHIR:<10}")
```

- `for mahasiswa in data_mahasiswa:` → iterasi setiap **key** di dictionary `data_mahasiswa` (MAH001, MAH002, MAH003).
- `data_mahasiswa[KEY]` → mengambil dictionary mahasiswa (level 1).
- `data_mahasiswa[KEY]['nama']` → mengambil nilai nama dari dictionary mahasiswa (level 2).
- `.strftime("%x")` → mengubah objek datetime menjadi string format tanggal lokal (contoh: `04/10/01`).
- `:^9` → teks **center** (tengah) dengan lebar 9 karakter (untuk kolom beasiswa).
- Hasil output berupa tabel yang rapi seperti:

```
KEY    Nama              SKS  Beasiswa  Lahir
--------------------------------------------------
MAH001 Ucup Surucup      130  False     04/10/01
MAH002 Otong Surotong    140  True      10/10/02
MAH003 Asep Si Kasyep    100  False     02/29/00
```

---

## Struktur Data Nested Dictionary

```
data_mahasiswa (Dictionary Utama)
│
├── Key: 'MAH001'
│   └── Value: Dictionary Mahasiswa 1
│       ├── 'nama': 'Ucup Surucup'
│       ├── 'nim': '19022001'
│       ├── 'sks_lulus': 130
│       ├── 'beasiswa': False
│       └── 'lahir': datetime(2001, 4, 10)
│
├── Key: 'MAH002'
│   └── Value: Dictionary Mahasiswa 2
│       └── ...
│
└── Key: 'MAH003'
    └── Value: Dictionary Mahasiswa 3
        └── ...
```

---

## Analogi

Bayangkan kamu punya **lemari arsip**:

- **Dictionary level atas** (`data_mahasiswa`) = **Lemari arsipnya** dengan label folder: MAH001, MAH002, MAH003.
- **Dictionary level 1** (mahasiswa1, mahasiswa2, mahasiswa3) = **Isi setiap folder**: ada kartu nama, kartu NIM, kartu beasiswa, dll.
- Untuk mengambil nama mahasiswa MAH001, kamu harus:
  1. Buka lemari → cari folder `MAH001`
  2. Ambil kartu bernama `nama` → dapat "Ucup Surucup"

---

## Kesalahan Umum Pemula

- **Akses salah level**: `data_mahasiswa['nama']` akan error karena `'nama'` bukan key di level atas, tapi di level dalam.
- **Lupa `import datetime`**: Tanpa import, `datetime.datetime(...)` tidak bisa dipanggil.
- **Key sensitif huruf besar/kecil**: `'MAH001'` berbeda dari `'mah001'`.
