# BAB 3 - Latihan Dictionary

## Apa yang Dipelajari

- Membuat program interaktif menggunakan dictionary
- Menggunakan `dict.fromkeys()` untuk membuat dictionary dari template
- Menggabungkan loop `while True` dengan dictionary untuk input berulang
- Menggunakan `random` dan `string` untuk generate key acak
- Konsep `.update()` untuk menambah elemen dictionary
- Menampilkan data dalam format tabel

---

## Penjelasan Kode

### File: `Main.py`

#### 1. Import Modules

```python
import datetime
import os
import string
import random
```

| Module     | Fungsi                                                      |
|------------|-------------------------------------------------------------|
| `datetime` | Untuk membuat objek tanggal lahir mahasiswa                 |
| `os`       | Untuk menjalankan perintah sistem (clear/cls screen)        |
| `string`   | Untuk mengakses karakter huruf (`string.ascii_uppercase`)   |
| `random`   | Untuk memilih karakter secara acak                          |

#### 2. Template Dictionary Mahasiswa

```python
mahasiswa_template = {
    'nama':'nama',
    'nim':'00000000',
    'sks_lulus':0,
    'lahir':datetime.datetime(1111,1,11)
}
```

- Ini adalah **template** atau cetakan yang berisi struktur data mahasiswa.
- Nilai di dalamnya hanyalah **placeholder** (nilai semu), nanti akan diisi oleh user.
- Berguna sebagai panduan untuk `dict.fromkeys()`.

#### 3. Dictionary Kosong untuk Menyimpan Data

```python
data_mahasiswa = {}
```

- Dictionary kosong yang akan diisi oleh data-data mahasiswa dari input user.
- Setiap mahasiswa akan ditambahkan dengan **key acak**.

#### 4. Loop Utama Program

```python
while True:
```

- Loop tanpa batas (`while True`) agar user bisa terus memasukkan data sampai memilih untuk berhenti.

#### 5. Membersihkan Layar dan Menampilkan Header

```python
    os.system("clear")
    print(f"{'SELAMAT DATANG':^20}")
    print(f"{'DATA MAHASISWA':^20}")
    print("-"*20)
```

- `os.system("clear")` → membersihkan layar terminal (untuk Linux/Mac). Di Windows diganti `os.system("cls")`.
- `:^20` → teks ditampilkan di **tengah** dengan lebar 20 karakter.

#### 6. Membuat Dictionary Mahasiswa dari Template

```python
    mahasiswa = dict.fromkeys(mahasiswa_template.keys())
```

- `dict.fromkeys()` membuat dictionary baru dari list keys.
- `mahasiswa_template.keys()` mengambil semua key: `['nama', 'nim', 'sks_lulus', 'lahir']`.
- Hasilnya: `{'nama': None, 'nim': None, 'sks_lulus': None, 'lahir': None}`.
- Semua value menjadi `None` karena tidak ada default value.

#### 7. Input Data dari User

```python
    mahasiswa['nama'] = input("Nama Mahasiswa: ")
    mahasiswa['nim'] = input("NIM Mahasiswa: ")
    mahasiswa['sks_lulus'] = int(input("SKS Lulus: "))
    TAHUN_LAHIR = int(input("Tahun lahir (YYYY): "))
    BULAN_LAHIR = int(input("Bulan lahir (1-12): "))
    TANGGAL_LAHIR = int(input("Tanggal lahir (1-31): "))
    mahasiswa['lahir'] = datetime.datetime(TAHUN_LAHIR,BULAN_LAHIR,TANGGAL_LAHIR)
```

- `input()` mengambil teks dari user.
- `int()` mengubah input string menjadi integer untuk SKS dan tanggal.
- `datetime.datetime()` membuat objek tanggal dari tahun, bulan, tanggal yang diinput user.

#### 8. Generate Key Acak dan Simpan ke Dictionary

```python
    KEY = ''.join((random.choice(string.ascii_uppercase) for i in range(6)))
    data_mahasiswa.update({KEY:mahasiswa})
```

- `string.ascii_uppercase` = `"ABCDEFGHIJKLMNOPQRSTUVWXYZ"`
- `random.choice(...)` memilih 1 huruf acak dari string tersebut.
- `for i in range(6)` → diulang 6 kali.
- `''.join(...)` menggabungkan 6 huruf acak menjadi string, contoh: `"XKRTMB"`.
- `.update({KEY: mahasiswa})` menambah pasangan key-value baru ke dictionary `data_mahasiswa`.

#### 9. Menampilkan Semua Data dalam Tabel

```python
    print(f"\n{'KEY':<6} {'Nama':<17} {'NIM':<8} {'SKS Lulus':<10} {'Tanggal Lahir':<10}")
    print('-'*60)

    for mahasiswa in data_mahasiswa:
        KEY = mahasiswa
        NAMA = data_mahasiswa[KEY]['nama']
        NIM = data_mahasiswa[KEY]['nim']
        SKS = data_mahasiswa[KEY]['sks_lulus']
        LAHIR = data_mahasiswa[KEY]['lahir'].strftime("%x")
        print(f"{KEY:<6} {NAMA:<17} {NIM:<8} {SKS:^10} {LAHIR:^10}")
```

- Sama seperti Episode 42, tapi ditambah kolom NIM.
- `.strftime("%x")` → format tanggal lokal.

#### 10. Tanya User untuk Lanjut atau Berhenti

```python
    is_done = input("Mau tambah lagi bro (y/n)? ")
    if is_done == "n":
        break

print("\nAkhir dari program, terima kasih")
```

- Jika user mengetik `"n"`, loop `while` dihentikan dengan `break`.
- Program berjalan terus selama user tidak mengetik `"n"`.

---

## Alur Program

```
┌─────────────────────────────┐
│        Mulai Program        │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│     Clear Layar + Header    │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│  Input: Nama, NIM, SKS,    │
│         Tanggal Lahir       │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│  Generate Key Acak 6 Huruf │
│  Simpan ke data_mahasiswa  │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│  Tampilkan Semua Data       │
│  dalam Format Tabel         │
└─────────────┬───────────────┘
              ▼
┌─────────────────────────────┐
│  Mau tambah lagi? (y/n)     │
│  ┌─── y ──→ Kembali ke atas │
│  └─── n ──→ Selesai         │
└─────────────────────────────┘
```

---

## Analogi

Program ini seperti **petugas resepsionis kampus** yang mendaftarkan mahasiswa baru:

1. Meletakkan **form kosong** di meja (template dictionary).
2. User mengisi nama, NIM, SKS, tanggal lahir.
3. Petugas **memberi nomor registrasi acak** (key acak 6 huruf).
4. Data dimasukkan ke **buku induk** (dictionary `data_mahasiswa`).
5. Ditampilkan **rekap data** di layar.
6. Ditanya lagi: "Mau daftarkan mahasiswa lain?"
7. Kalau tidak, program selesai.

---

## Istilah Penting

| Istilah             | Penjelasan                                                       |
|---------------------|------------------------------------------------------------------|
| `dict.fromkeys()`   | Membuat dictionary baru dari list key dengan value default `None`|
| `.update()`         | Menambah/memperbarui pasangan key-value di dictionary            |
| `random.choice()`   | Memilih satu elemen acak dari sequence                           |
| `string.ascii_uppercase` | String berisi huruf besar A-Z                              |
| `.strftime("%x")`   | Mengubah datetime menjadi string format tanggal lokal            |
