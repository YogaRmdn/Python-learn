# BAB 11 - Error Handling: Try and Exception

## Apa yang Dipelajari

- **Error handling** : Teknik menangani error agar program tidak langsung berhenti/crash
- **`try`** : Blok kode yang "dicoba" dijalankan. Jika ada error, pindah ke `except`
- **`except`** : Blok yang dijalankan jika terjadi error tertentu di blok `try`
- **`Exception`** : Kelas dasar untuk semua jenis error di Python
- **Jenis-jenis exception** : `ValueError`, `ZeroDivisionError`, `ImportError`, dan lainnya
- **`while True` + `break`** : Pola looping yang terus berjalan sampai input valid

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
print("ini adalah program pembagian")

while True:
    try:
        import panda
        penyebut = int(input("masukan angka penyebut: "))
        pembilang = int(input("masukan angka pembilang: "))
        hasil = penyebut/pembilang
        break
    except ValueError:
        print("yang anda masukan bukan angka\n")
    except ZeroDivisionError:
        print("angka pembilang yang anda masukan adalah nol, pilih yang lain ya bro/sist\n")
    except ImportError:
        print("gak ada modulnya bro")
    except Exception as err:
        print(err)

"""
    type of exception errors:
    1. IOError
    2. ImportError
    3. ValueError
    4. Division by zero
    5. KeyboardInterupted
    6. EOFError
"""

print("berhasil, hasil pembagian adalah: ", hasil)
```

### Blok 1: Pendahuluan

```python
print("ini adalah program pembagian")
```

- Mencetak judul program ke layar.

### Blok 2: Looping Tak Terbatas

```python
while True:
```

- `while True` - Membuat **loop yang terus berjalan tanpa henti**. Loop ini hanya akan berhenti jika ada `break` di dalamnya. Tujuannya: meminta input terus-menerus sampai pengguna memberikan input yang valid.

### Blok 3: Blok Try

```python
    try:
        import panda
        penyebut = int(input("masukan angka penyebut: "))
        pembilang = int(input("masukan angka pembilang: "))
        hasil = penyebut/pembilang
        break
```

- `try:` - Menandai awal blok yang **akan dicoba** dijalankan. Jika terjadi error di baris mana pun, Python akan **langsung loncat** ke blok `except` yang sesuai.
- `import panda` - Mencoba mengimport module `panda`. **Module ini tidak ada** di Python (yang benar adalah `pandas`). Ini akan memicu `ImportError`.
- `penyebut = int(input("masukan angka penyebut: "))` - Meminta input pengguna dan mengonversinya ke integer.
  - Jika input bukan angka (misalnya "abc"), `int()` akan memicu **`ValueError`**.
- `pembilang = int(input("masukan angka pembilang: "))` - Sama seperti di atas, untuk pembilang.
- `hasil = penyebut/pembilang` - Membagi penyebut dengan pembilang.
  - Jika `pembilang = 0`, ini akan memicu **`ZeroDivisionError`**.
- `break` - Jika **semua baris di try berhasil** tanpa error, loop berhenti dan program lanjut ke baris setelah loop.

> **Penting:** Jika `import panda` memicu error, Python **langsung loncat** ke `except ImportError` dan **melewati** semua baris setelahnya (termasuk input dan pembagian). Artinya, pada eksekusi pertama, program langsung ke `except ImportError`.

### Blok 4: Blok Except

```python
    except ValueError:
        print("yang anda masukan bukan angka\n")
```

- Menangani error **`ValueError`** - terjadi saat `int()` menerima input yang bukan angka (misalnya string `"abc"`). Program mencetak pesan dan loop berlanjut meminta input lagi.

```python
    except ZeroDivisionError:
        print("angka pembilang yang anda masukan adalah nol, pilih yang lain ya bro/sist\n")
```

- Menangani error **`ZeroDivisionError`** - terjadi saat membagi dengan nol.

```python
    except ImportError:
        print("gak ada modulnya bro")
```

- Menangani error **`ImportError`** - terjadi saat module yang diimport tidak ditemukan (kita sengaja import `panda` yang tidak ada).

```python
    except Exception as err:
        print(err)
```

- Menangani **semua jenis error lain** yang belum ditangani di atas. `Exception` adalah parent class dari semua exception. `as err` menyimpan pesan error ke variabel `err` untuk ditampilkan.

### Blok 5: Setelah Loop Selesai

```python
print("berhasil, hasil pembagian adalah: ", hasil)
```

- Hanya dijalankan setelah loop berhenti (ada `break`), artinya input valid dan pembagian berhasil.

### Daftar Jenis Exception

| Exception | Kapan Terjadi | Contoh |
|-----------|---------------|--------|
| `ValueError` | Tipe data tidak sesuai | `int("abc")` |
| `ZeroDivisionError` | Membagi dengan nol | `10 / 0` |
| `ImportError` | Module tidak ditemukan | `import tidak_ada` |
| `TypeError` | Operasi pada tipe yang salah | `"abc" + 5` |
| `FileNotFoundError` | File tidak ditemukan | `open("tidak_ada.txt")` |
| `IndexError` | Index di luar batas | `[1,2,3][5]` |
| `KeyError` | Key tidak ada di dictionary | `{"a":1}["b"]` |
| `AttributeError` | Attribute tidak ada | `"abc".nonexistent()` |
| `IOError` | Gagal membaca/menulis file | File corrupt |

### Alur Program

```
START
  │
  ▼
while True ─────────────────────────────┐
  │                                      │
  ▼                                      │
try:                                     │
  │ import panda → ImportError? ──YES──→ except ImportError → LOOP LAGI
  │ input penyebut → ValueError? ─YES──→ except ValueError → LOOP LAGI
  │ input pembilang → ValueError? ─YES──→ except ValueError → LOOP LAGI
  │ pembagian → ZeroDivisionError? ─YES─→ except ZeroDivisionError → LOOP LAGI
  │ break ──→ EXIT LOOP                 │
  │                                      │
  └──────────────────────────────────────┘
  │
  ▼
print("berhasil, hasil pembagian adalah: ", hasil)
END
```

## Analogi

Bayangkan **mesin ATM**:

- **`while True`** = ATM tetap menyala dan siap melayani selama bank buka. Tidak akan mati sendiri.
- **`try`** = Kamu memasukkan kartu ATM dan mencoba bertransaksi.
- **`ValueError`** = Kamu **salah memasukkan PIN** (misalnya huruf, bukan angka). ATM menampilkan "PIN salah, coba lagi" dan meminta input ulang. Tidak mati/mogok.
- **`ZeroDivisionError`** = Kamu mencoba **membagi saldo ke 0 rekening**. ATM menampilkan "Transaksi tidak dapat dilakukan" dan meminta pilihan lain.
- **`ImportError`** = Mesin ATM **kehabisan kertas struk** (module tidak tersedia). ATM menampilkan pesan tapi tetap berfungsi untuk transaksi lain.
- **`break`** = Transaksi berhasil. Struk keluar, kartu dikeluarkan. **Selesai.**
- **`except Exception as err`** = Error yang tidak terduga (misalnya listrik padam sebentar). ATM mencatat error dan tetap mencoba lagi.
- **Setelah loop (print hasil)** = Kamu menerima **bukti transaksi** dan meninggalkan ATM dengan sukses.

> **Inti error handling:** Jangan biarkan program crash saat error. Tangani dengan elegan, beri pesan yang jelas ke pengguna, dan beri kesempatan untuk mencoba lagi.
