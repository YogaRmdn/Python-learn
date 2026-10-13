# BAB 9 - Episode 69: Write - Project CRUD

## Apa yang Dipelajari

- Mengimplementasikan operasi **Create** (menambah data baru) pada database file teks
- Menulis data ke file menggunakan mode **append (`a`)** agar data baru ditambahkan di akhir
- Validasi input tahun harus **4 digit angka**
- Menampilkan data terbaru setelah penambahan
- **Stacking view**: `create_console()` memanggil `read_console()` untuk menampilkan hasil

---

## Penjelasan Kode

### File: `CRUD/__init__.py`

```python
from .Database import init_console
from .View import read_console, create_console
```

- Sekarang **`create_console`** ikut di-export dari package `CRUD`.
- `main.py` bisa memanggil `CRUD.create_console()`.

---

### File: `CRUD/Database.py`

Tidak berubah dari Episode 68. Berisi konfigurasi database:
- `DB_NAME = "data.txt"`
- `TEMPLATE` dengan format kolom dan panjang

---

### File: `CRUD/Operasi.py` — Fungsi `create()`

```python
def create(tahun, judul, penulis):
    data = Database.TEMPLATE.copy()

    data["pk"] = random_string(6)
    data["date_add"] = time.strftime("%Y-%m-%d-%H-%M-%S%z", time.gmtime())
    data["penulis"] = penulis + Database.TEMPLATE["penulis"][len(penulis):]
    data["judul"] = judul + Database.TEMPLATE["judul"][len(judul):]
    data["tahun"] = str(tahun)

    data_str = f'{data["pk"]},{data["date_add"]},{data["penulis"]},{data["judul"]},{data["tahun"]}\n'
    
    try:
        with open(Database.DB_NAME, 'a', encoding="utf-8") as file:
            file.write(data_str)
    except:
        print("Data sulit ditambahkan boooos, gagal maning")
```

**Perbedaan dengan `create_first_data()`:**

| Aspek | `create_first_data()` | `create()` |
|---|---|---|
| Mode file | `'w'` (tulis baru / timpa) | **`'a'` (append / tambah)** |
| Input | Minta input dari user via `input()` | Menerima parameter dari fungsi lain |
| Kapan dipakai | Saat database pertama kali dibuat | Saat menambah data baru |

**Penjelasan `create()`:**

| Langkah | Kode | Penjelasan |
|---|---|---|
| 1 | `Database.TEMPLATE.copy()` | Salin template agar data baru tidak mengubah template |
| 2 | `random_string(6)` | Generate ID unik 6 karakter |
| 3 | `time.strftime(...)` | Buat timestamp otomatis |
| 4 | Padding | Tambah spasi agar panjang kolom tetap 255 |
| 5 | Format string | Gabungkan kolom dengan koma |
| 6 | `open(..., 'a')` | Buka file mode **append** — tulis di akhir |
| 7 | `file.write(data_str)` | Tulis satu baris data baru |

> **Kunci:** Mode `'a'` memastikan data baru **ditambahkan di baris baru** tanpa menghapus data lama.

---

### Fungsi `create_first_data()` — Versi Episode 69

```python
def create_first_data():
    penulis = input("Penulis: ")
    judul = input("Judul: ")
    while(True):
        try:
            tahun = int(input("Tahun\t: "))
            if len(str(tahun)) == 4:
                break
            else:
                print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")    
        except:
            print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")

    data = Database.TEMPLATE.copy()
    # ... (sama seperti Episode 68, tapi dengan validasi tahun)
```

**Yang baru di Episode 69:** Ada **validasi input tahun**:

```python
while(True):
    try:
        tahun = int(input("Tahun\t: "))
        if len(str(tahun)) == 4:     # Pastikan 4 digit
            break
        else:
            print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")    
    except:
        print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")
```

| Validasi | Penjelasan |
|---|---|
| `int(input(...))` | Pastikan input bisa dikonversi ke integer |
| `len(str(tahun)) == 4` | Pastikan tahun 4 digit (misal: 2023, bukan 23) |
| Loop `while(True)` | Terus minta input sampai valid |

---

### File: `CRUD/View.py` — Fungsi `create_console()`

```python
def create_console():
    print("\n\n" + "="*100)
    print("Silahkan tambah data buku\n")
    penulis = input("Penulis\t: ")
    judul = input("Judul\t: ")
    while(True):
        try:
            tahun = int(input("Tahun\t: "))
            if len(str(tahun)) == 4:
                break
            else:
                print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")    
        except:
            print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")

    Operasi.create(tahun, judul, penulis)
    print("\nBerikut adalah data baru anda")
    read_console()
```

**Alur `create_console()`:**

```
1. Tampilkan header "Silahkan tambah data buku"
2. Minta input: penulis, judul
3. Minta input tahun dengan validasi (4 digit angka)
4. Panggil Operasi.create() → tulis ke file
5. Panggil read_console() → tampilkan semua data (termasuk yang baru)
```

> **Pola menarik:** Setelah menambah data, `create_console()` langsung memanggil `read_console()` untuk menampilkan hasilnya. Ini memberikan **feedback visual** ke user bahwa data berhasil ditambahkan.

---

### File: `CRUD/View.py` — Fungsi `read_console()`

Sama seperti Episode 68 — menampilkan data dalam format tabel.

---

### File: `main.py`

```python
match user_option:
    case "1": CRUD.read_console()
    case "2": CRUD.create_console()    # ← Create sudah diimplementasi!
    case "3": print("Update Data")     # ← Belum
    case "4": print("Delete Data")     # ← Belum
```

Opsi `"2"` sekarang memanggil `CRUD.create_console()`.

---

### Alur Program Create (Penambahan Data)

```
User pilih "2. Create Data"
        │
        ▼
CRUD.create_console()
        │
        ▼
View.create_console()
        │
        ├── Input: penulis, judul, tahun
        │
        ▼
Operasi.create(tahun, judul, penulis)
        │
        ├── Generate pk (random 6 karakter)
        ├── Generate timestamp
        ├── Padding kolom
        ├── Format string
        │
        ▼
Buka data.txt mode 'a' → tulis baris baru
        │
        ▼
read_console() → tampilkan semua data (termasuk yang baru)
```

---

### Isi `data.txt` Setelah Penambahan

**Sebelum (3 data):**
```
lJLsFO,2022-10-13-13-45-52+0700,Faqihza Mukhlish,...,2085
lJLs55,2022-10-13-13-45-52+0700,Faqihza Mukhlish,...,2060
lJLs22,2022-10-13-13-45-52+0700,otong,...,1998
```

**Sesudah menambah data "Ucup" (5 data):**
```
lJLsFO,2022-10-13-13-45-52+0700,Faqihza Mukhlish,...,2085
lJLs55,2022-10-13-13-45-52+0700,Faqihza Mukhlish,...,2060
lJLs22,2022-10-13-13-45-52+0700,otong,...,1998
gNVOwg,2022-11-01-14-32-06+0700,Ucup,...,2050
idhrRg,2022-11-01-14-33-00+0700,Otong,...,2099
```

---

## Analogi

Bayangkan kamu **menambah kartu buku baru** ke lemari perpustakaan:

1. **`create_console()`** = Kamu memberikan formulir kosong ke pelanggan: "Silahkan isi nama, judul buku, dan tahun terbit."
2. **Validasi tahun** = Kamu memeriksa: "Tahun harus 4 digit ya, Kak. Kalau cuma 2 digit, tolong ulangi."
3. **`Operasi.create()`** = Kamu mengisi kartu baru sesuai format baku:
   - Cetak ID acak (misal `gNVOwg`)
   - Catat tanggal pengisian
   - Tulis nama, judul, tahun — rapi dengan spasi yang cukup
4. **Mode `'a'`** = Kartu baru diletakkan **di rak paling belakang** — kartu lama tetap di tempatnya.
5. **`read_console()`** = Kamu memasang ulang **semua kartu** di papan pengumuman (termasuk yang baru).

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Mode append | `open(f, 'a')` | Menambah data di akhir file |
| Mode write | `open(f, 'w')` | Menulis baru / menimpa file |
| Validasi input | `try-except` + `while` | Memastikan input valid sebelum diproses |
| `len(str(x)) == 4` | Cek jumlah digit | Memastikan tahun 4 digit |
| Template copy | `TEMPLATE.copy()` | Salin dict agar original tidak berubah |
| Padding | `teks + spasi[panjang-teks:]` | Kolom tetap panjang |
| Feedback | `read_console()` setelah create | Tampilkan hasil agar user tahu berhasil |
