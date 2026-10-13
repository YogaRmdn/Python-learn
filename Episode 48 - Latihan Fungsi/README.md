# BAB 8 - Latihan Fungsi

## Apa yang Dipelajari

- Menggabungkan semua konsep fungsi dalam program nyata
- Membuat program kalkulator luas dan keliling persegi panjang
- Menggunakan fungsi untuk input, proses, dan output
- Fungsi yang mengembalikan **banyak nilai** (tuple unpacking)
- Loop interaktif dengan fungsi

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Kode Tanpa Fungsi (Versi Lama - Dikomentari)

```python
# os.system("clear")
# print(f"{'PROGRAM MENGHITUNG LUAS':^40}")
# print(f"{'DAN KELILING PERSEGI PANJANG':^40}")
# print(f"{'-'*40:^40}")
#
# LEBAR = int(input("Masukan nilai lebar: "))
# PANJANG = int(input("Masukan nilai panjang: "))
#
# LUAS = PANJANG*LEBAR
# KELILING = 2*(PANJANG+LEBAR)
#
# print(f"hasil perhitungan luas = {LUAS}")
# print(f"hasil perhitungan keliling = {KELILING}")
```

- Kode lama **tidak pakai fungsi**, ditulis lurus (linear).
- Kelemahan: sulit dipelihara, tidak modular, sulit diulang.

#### 2. Fungsi Header

```python
def header():
    '''fungsi Header'''
    os.system("clear")
    print(f"{'PROGRAM MENGHITUNG LUAS':^40}")
    print(f"{'DAN KELILING PERSEGI PANJANG':^40}")
    print(f"{'-'*40:^40}")
```

- Membersihkan layar dan menampilkan judul program.
- Dipanggil setiap kali loop berputar agar layar selalu bersih.

#### 3. Fungsi Input User (Return Tuple)

```python
def input_user():
    '''fungsi input user'''
    lebar = int(input("Masukan nilai lebar: "))
    panjang = int(input("Masukan nilai panjang: "))
    return lebar,panjang
```

- Mengembalikan **2 nilai** sekaligus: `lebar` dan `panjang`.
- Saat dipanggil, hasilnya di-unpack ke 2 variabel:

```python
LEBAR,PANJANG = input_user()
```

- `LEBAR` mendapat nilai lebar, `PANJANG` mendapat nilai panjang.

#### 4. Fungsi Menghitung Luas

```python
def hitung_luas(lebar,panjang):
    '''fungsi luas'''
    return lebar*panjang
```

- Formula: `luas = lebar × panjang`
- Mengembalikan hasil perhitungan.

#### 5. Fungsi Menghitung Keliling

```python
def hitung_keliling(lebar,panjang):
    '''fungsi keliling'''
    return 2*(lebar+panjang)
```

- Formula: `keliling = 2 × (lebar + panjang)`
- Mengembalikan hasil perhitungan.

#### 6. Fungsi Display

```python
def display(message,value):
    '''fungsi display'''
    print(f"hasil perhitungan {message} = {value}")
```

- Fungsi generik untuk menampilkan hasil.
- `message` = keterangan (contoh: "luas"), `value` = nilai hasil.

#### 7. Program Utama (Main Loop)

```python
while True:
    header()
    LEBAR,PANJANG = input_user()
    LUAS = hitung_luas(LEBAR,PANJANG)
    KELILING = hitung_keliling(LEBAR,PANJANG)

    display("luas", LUAS)
    display("keliling", KELILING)

    isContinue = input("apakah lanjut (y/n)? ")
    if isContinue == "n":
        break

print("Program selesai, terima kasih")
```

**Alur kerja:**

1. Clear layar + tampilkan header.
2. Input lebar dan panjang dari user.
3. Hitung luas dan keliling.
4. Tampilkan hasil.
5. Tanya user: mau lanjut atau berhenti.

---

## Struktur Program Modular

```
┌─────────────────┐
│   header()      │  ← Menampilkan judul
└────────┬────────┘
         ▼
┌─────────────────┐
│  input_user()   │  ← Mengambil input dari user
└────────┬────────┘
         ▼
┌──────────────────────────────────┐
│  hitung_luas(lebar, panjang)     │  ← Proses perhitungan luas
│  hitung_keliling(lebar, panjang) │  ← Proses perhitungan keliling
└────────┬─────────────────────────┘
         ▼
┌─────────────────┐
│  display(...)   │  ← Menampilkan hasil
└────────┬────────┘
         ▼
    Lanjut / Berhenti?
```

---

## Analogi

Bayangkan program ini adalah **karyawan di toko**:

1. **`header()`** = Karyawan **menyapa** pelanggan: "Selamat datang di Toko Persegi Panjang!"
2. **`input_user()`** = Karyawan **bertanya**: "Berapa lebar dan panjang yang Anda butuhkan?"
3. **`hitung_luas()`** = Karyawan **menghitung** luas di kalkulator.
4. **`hitung_keliling()`** = Karyawan **menghitung** keliling.
5. **`display()`** = Karyawan **memberitahu** hasilnya: "Luasnya 20 m², kelilingnya 18 m."
6. Ditanya lagi: "Mau hitung lagi?"

---

## Kenapa Program Ini Lebih Baik dari Kode Lama?

| Kode Lama (Tanpa Fungsi) | Kode Baru (Dengan Fungsi)         |
|---------------------------|-----------------------------------|
| Semua kode di satu tempat | Kode terpisah per fungsi         |
| Sulit mengubah satu bagian | Tinggal ubah di fungsi tertentu  |
| Tidak bisa diulang mudah | Panggil fungsi untuk mengulang   |
| Sulit dibaca | Mudah dipahami karena modular    |
