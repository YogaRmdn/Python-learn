# BAB 10 - Episode 70: Update - Project CRUD

## Apa yang Dipelajari

- Mengimplementasikan operasi **Update** (mengubah data) pada database file teks
- Membaca **satu record** berdasarkan nomor indeks menggunakan **keyword arguments (`**kwargs`)**
- Menulis ulang data di posisi tertentu menggunakan **`file.seek()`** dan mode `r+`
- User memilih field mana yang ingin diubah (judul, penulis, atau tahun)
- Loop konfirmasi agar user bisa merevisi sebelum menyimpan

---

## Penjelasan Kode

### File: `CRUD/__init__.py`

```python
from .Database import init_console
from .View import read_console, create_console, update_console
```

- `update_console` sekarang di-export dari package `CRUD`.

---

### File: `CRUD/Operasi.py` — Fungsi `read(**kwargs)`

```python
def read(**kwargs):
    try:
        with open(Database.DB_NAME, 'r') as file:
            content = file.readlines()
            jumlah_buku = len(content)
            if "index" in kwargs:
                index_buku = kwargs["index"] - 1
                if index_buku < 0 or index_buku > jumlah_buku:
                    return False
                else:    
                    return content[index_buku]
            else:
                return content
    except:
        print("Membaca database error")
        return False
```

**Versi Episode 70 punya fitur baru:** bisa membaca **satu record tertentu**.

| Pemanggilan | Hasil |
|---|---|
| `Operasi.read()` | Mengembalikan **semua data** (list) |
| `Operasi.read(index=3)` | Mengembalikan **satu baris** ke-3 |

**Penjelasan `**kwargs`:**

```python
def read(**kwargs):
```

- `**kwargs` adalah **keyword arguments** — menerima parameter bernama dalam bentuk dictionary.
- Jika dipanggil `read(index=3)`, maka `kwargs = {"index": 3}`.
- Jika dipanggil `read()` tanpa argumen, maka `kwargs = {}`.

```python
if "index" in kwargs:
    index_buku = kwargs["index"] - 1  # -1 karena user mulai dari 1
```

- User memasukkan nomor buku **mulai dari 1**, tapi index list mulai dari **0**.
- `index_buku = kwargs["index"] - 1` melakukan konversi.

```python
if index_buku < 0 or index_buku > jumlah_buku:
    return False
```

- Validasi: jika index di luar batas, kembalikan `False`.

---

### File: `CRUD/Operasi.py` — Fungsi `update()`

```python
def update(no_buku, pk, data_add, tahun, judul, penulis):
    data = Database.TEMPLATE.copy()

    data["pk"] = pk
    data["date_add"] = data_add
    data["penulis"] = penulis + Database.TEMPLATE["penulis"][len(penulis):]
    data["judul"] = judul + Database.TEMPLATE["judul"][len(judul):]
    data["tahun"] = str(tahun)

    data_str = f'{data["pk"]},{data["date_add"]},{data["penulis"]},{data["judul"]},{data["tahun"]}\n'
    
    panjang_data = len(data_str)

    try:
        with open(Database.DB_NAME, 'r+', encoding="utf-8") as file:
            file.seek(panjang_data * (no_buku - 1))
            file.write(data_str)
    except:
        print("error dalam update data")
```

**Penjelasan kunci:**

| Kode | Penjelasan |
|---|---|
| `pk = pk` | Primary key **tetap** (tidak diubah) |
| `data_add = data_add` | Timestamp **tetap** (tidak diubah) |
| `file.seek(panjang_data * (no_buku - 1))` | Pindahkan cursor ke posisi record yang akan diupdate |
| `file.write(data_str)` | Tulis data baru di posisi tersebut (menimpa yang lama) |

**Bagaimana `file.seek()` bekerja:**

```
File data.txt (setiap baris punya panjang yang SAMA karena padding):

Baris 1: [================ panjang_data ================]\n
Baris 2: [================ panjang_data ================]\n
Baris 3: [================ panjang_data ================]\n

Posisi byte:
Baris 1: mulai dari 0
Baris 2: mulai dari panjang_data × 1
Baris 3: mulai dari panjang_data × 2

Jika update baris 2:
  file.seek(panjang_data × 1)  → cursor di awal baris 2
  file.write(data_baru)         → timpa baris 2 dengan data baru
```

> **Kenapa `r+`?** Mode ini memungkinkan **baca sekaligus tulis**. File harus sudah ada. `seek()` memindahkan cursor ke posisi tertentu, lalu `write()` menulis dari posisi itu.

---

### File: `CRUD/View.py` — Fungsi `update_console()`

```python
def update_console():
    read_console()          # Tampilkan semua data
    while(True):
        print("Silahkan pilih nomor buku yang akan di update")
        no_buku = int(input("Nomor Buku: "))
        data_buku = Operasi.read(index=no_buku)

        if data_buku:
            break
        else:
            print("nomor tidak valid, silahkan masukan lagi")
    
    data_break = data_buku.split(',')
    pk = data_break[0]
    data_add = data_break[1]
    penulis = data_break[2]
    judul = data_break[3]
    tahun = data_break[4][:-1]   # [:-1] untuk hapus \n di akhir

    while(True):
        print("\n" + "="*100)
        print("Silahkan pilih data apa yang ingin anda ubah")
        print(f"1. Judul\t: {judul:.40}")
        print(f"2. Penulis\t: {penulis:.40}")
        print(f"3. Tahun\t: {tahun:4}")

        user_option = input("Pilih data [1,2,3]: ")
        print("\n" + "="*100)
        match user_option:
            case "1": judul = input("judul\t: ")
            case "2": penulis = input("penulis\t: ")
            case "3": 
                while(True):
                    try:
                        tahun = int(input("Tahun\t: "))
                        if len(str(tahun)) == 4:
                            break
                        else:
                            print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")    
                    except:
                        print("tahun harus angka, silahkan masukan tahun lagi (yyyy)")
            case _: print("index tidak cuocuoook")

        print("Data baru anda")
        print(f"1. Judul\t: {judul:.40}")
        print(f"2. Penulis\t: {penulis:.40}")
        print(f"3. Tahun\t: {tahun:4}")
        is_done = input("Apakah data sudah sesuai(y/n)? ")
        if is_done == "y" or is_done == "Y":
            break
    
    Operasi.update(no_buku, pk, data_add, tahun, judul, penulis)
```

**Alur `update_console()`:**

```
1. Tampilkan semua data (read_console)
2. Minta nomor buku yang ingin diupdate
3. Baca data buku tersebut (Operasi.read(index=...))
4. Pecah data jadi variabel (pk, data_add, judul, penulis, tahun)
5. Tampilkan field-field yang bisa diubah
6. User pilih field mana yang diubah
7. Minta input nilai baru
8. Konfirmasi: "Apakah data sudah sesuai?"
   - Jika "n" → ulangi langkah 5-8
   - Jika "y" → simpan perubahan
9. Panggil Operasi.update() → tulis ke file
```

> **Yang unik:** `pk` dan `data_add` **tidak diubah** — mereka dipertahankan dari data asli. Hanya `judul`, `penulis`, dan `tahun` yang bisa diubah.

---

### Contoh Proses Update

```
Sebelum update (data ke-3):
  pk: lJLs22
  penulis: otong
  judul: abang abangan
  tahun: 1998

User memilih: ubah judul jadi "Galaxy bima sakti: sebuah rahasia"

Sesudah update:
  pk: lJLs22              ← tetap
  data_add: 2022-10-13... ← tetap
  penulis: otong           ← tetap
  judul: Galaxy bima sakti: sebuah rahasia  ← BERUBAH
  tahun: 1998              ← tetap
```

---

### Alur Komunikasi antar Module

```
main.py → CRUD.update_console()
                │
                ▼
        View.update_console()
                │
                ├── read_console()         → tampilan tabel
                ├── Operasi.read(index=N)  → ambil 1 record
                │
                ▼
        User pilih field + input nilai baru
                │
                ▼
        Operasi.update(no, pk, data_add, tahun, judul, penulis)
                │
                ├── file.seek(posisi)      → pindah cursor
                ├── file.write(data_baru)  → timpa data lama
                │
                ▼
        Data ter-update di data.txt
```

---

## Analogi

Bayangkan kamu **mengedit kartu katalog perpustakaan**:

1. **`read_console()`** = Kamu memajang semua kartu di meja supaya pelanggan bisa melihat.
2. **User pilih nomor 3** = "Saya mau edit kartu nomor 3."
3. **`Operasi.read(index=3)`** = Kamu mengambil kartu ke-3 dari tumpukan.
4. **User pilih "ubah judul"** = Pelanggan mencoret judul lama dan menulis judul baru.
5. **Konfirmasi** = "Sudah benar belum datanya?" → "Sudah!"
6. **`file.seek()`** = Kamu menemukan **posisi tepat** kartu ke-3 di lemari arsip (berdasarkan jarak dari awal).
7. **`file.write()`** = Kamu **mengganti** kartu lama dengan kartu baru di posisi yang tepat — kartu lain tidak terganggu.

> Seperti mengedit satu halaman di buku tebal: kamu buka ke halaman yang tepat, sunting isinya, lalu tutup kembali. Halaman lain tetap utuh.

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| `**kwargs` | `def f(**kwargs)` | Menerima parameter bernama sebagai dictionary |
| `file.seek(n)` | Pindah cursor ke byte ke-n | Menulis di posisi tertentu |
| Mode `r+` | `open(f, 'r+')` | Baca + tulis (file harus ada) |
| `kwargs["index"]` | Akses parameter | Mengambil nilai dari keyword argument |
| `[:-1]` | Hapus karakter terakhir | Menghapus `\n` dari akhir string |
| `len(data_str)` | Panjang string | Digunakan untuk menghitung posisi byte |
| Konfirmasi | Loop `y/n` | User bisa merevisi sebelum menyimpan |
