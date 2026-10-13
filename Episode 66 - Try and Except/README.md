# BAB 6 - Episode 66: Try and Except

## Apa yang Dipelajari

- Menangani **error/exception** saat program berjalan menggunakan **`try`** dan **`except`**
- Mencegah program **crash** (berhenti mendadak) saat terjadi error
- Menangani error **pembagian dengan nol** (`ZeroDivisionError`)
- Menangani error **file tidak ditemukan** (`FileNotFoundError`)
- Menggunakan **`as`** untuk menangkap pesan error
- Membuat **exception sendiri** menggunakan **`raise`**
- Perbedaan exception umum vs spesifik

---

## Penjelasan Kode

### File: `main_app.py`

### Bagian 1 — Konsep Dasar Try-Except (Komentar)

```python
# try:
#     hasil = 10 / input_user
# except:
#     print("input tidak boleh 0")
```

Ini adalah contoh sederhana yang dikomentari:

- **`try`**: "Coba jalankan kode ini"
- **`except`**: "Kalau ada error, jangan crash — jalankan kode ini sebagai gantinya"

> **Analogi:** Seperti pakai helm saat naik motor — kalau jatuh (error), helm (except) melindungi kamu agar tidak cedera (program tidak crash).

---

### Bagian 2 — Aplikasi Try-Except: Pembagian

```python
while(True):
    angka = int(input("masukan angka pembagi: "))
    try:
        hasil = 10 / angka
        print(f"hasil = {hasil}")
        is_done = input("lanjutkan (y/n)? ")
        if is_done == "n":
            break
    except:
        print("pembagi nol, silahkan masukan input lagi")

print("Akhir dari program 1")
```

**Alur program:**

```
1. Minta input angka dari user
2. Coba bagi 10 dengan angka tersebut (try)
   - Jika berhasil → cetak hasil
   - Jika angka = 0 → error! masuk except → cetak pesan error
3. Tanya apakah mau lanjut
4. Ulangi sampai user pilih "n"
```

**Kondisi yang ditangani:**

| Input | Hasil | Blok |
|---|---|---|
| `angka = 5` | `hasil = 2.0` | `try` berhasil |
| `angka = 0` | `ZeroDivisionError` | Masuk `except` |
| `angka = "abc"` | `ValueError` | Masuk `except` |

> **Tanpa try-except**, input `0` akan menyebabkan program **crash** dengan pesan error yang menakutkan. **Dengan try-except**, program tetap berjalan dan menampilkan pesan yang ramah.

---

### Bagian 3 — Try-Except: Membaca File

```python
try:
    with open("data.txt", 'r') as file:
        print(file.read())
except:
    print("file data.txt tidak ditemukan, membuat file baru")
    with open("data.txt", 'w', encoding='utf-8') as file:
        file.write("file baru")

print("akhir dari program 2")
```

**Alur program:**

```
1. Coba buka file data.txt untuk dibaca (try)
   - Jika file ada → cetak isi file
   - Jika file TIDAK ada → error! masuk except → buat file baru
2. Program berakhir dengan normal
```

**Output jika file tidak ada:**
```
file data.txt tidak ditemukan, membuat file baru
akhir dari program 2
```

**Output jika file sudah ada:**
```
file baru
akhir dari program 2
```

> Ini pola yang sangat umum: **"coba buat file, kalau sudah ada则 baca, kalau belum则 buat"**.

---

### File: `main_app_2.py`

### Bagian 4 — Membuat Exception Sendiri dengan `raise`

```python
from numbers import Number

def tambah(a, b):
    if not isinstance(a, Number) or not isinstance(b, Number):
        raise "input harus angka"
    return a + b

print(tambah(5, 6))
```

| Baris | Penjelasan |
|---|---|
| `isinstance(a, Number)` | Mengecek apakah `a` bertipe angka (int, float) |
| `raise "input harus angka"` | **Membuat error sendiri** jika input bukan angka |

> **Catatan:** Sebenarnya `raise "string"` bukan cara yang benar (harusnya `raise TypeError("...")`), tapi ini menunjukkan konsep `raise`.

---

### Bagian 5 — Menangkap Pesan Error dengan `as`

```python
angka = 0

try:
    hasil = 10 / angka
except ZeroDivisionError as error_message:
    print(error_message)
```

- `ZeroDivisionError` adalah **tipe error spesifik** untuk pembagian dengan nol.
- `as error_message` menyimpan **pesan error** ke variabel `error_message`.
- Output: `division by zero`

---

### Perbedaan `except` Umum vs Spesifik

| Kode | Penjelasan |
|---|---|
| `except:` | Menangkap **SEMUA** error (tidak disarankan karena terlalu umum) |
| `except ZeroDivisionError:` | Hanya menangkap error **pembagian nol** |
| `except FileNotFoundError:` | Hanya menangkap error **file tidak ditemukan** |
| `except Exception as e:` | Menangkap semua error tapi menyimpan pesannya |

> **Best practice:** Gunakan **exception spesifik** agar debugging lebih mudah.

---

### Output Program

```
# main_app.py (jika user input 5 lalu n):
masukan angka pembagi: 5
hasil = 2.0
lanjutkan (y/n)? n
Akhir dari program 1

# main_app.py (jika file tidak ada):
file data.txt tidak ditemukan, membuat file baru
akhir dari program 2

# main_app_2.py:
5 + 6 = 11
division by zero
```

---

## Ringkasan Tipe Error yang Sering Dijumpai

| Error | Penyebab | Contoh |
|---|---|---|
| `ZeroDivisionError` | Bagi dengan 0 | `10 / 0` |
| `FileNotFoundError` | File tidak ditemukan | `open("xyz.txt")` |
| `ValueError` | Tipe data salah | `int("abc")` |
| `TypeError` | Operasi pada tipe yang salah | `"abc" + 5` |
| `IndexError` | Index di luar batas | `[1,2,3][99]` |
| `KeyError` | Key dictionary tidak ada | `{"a":1}["b"]` |

---

## Analogi

Bayangkan kamu sedang **memasak di dapur**:

- **`try`** = "Saya coba masak resep baru ini..."
- **`except`** = "...eh, ternyata kompornya mati! Tidak masalah, saya pakai microwave sebagai gantinya."
- **`raise`** = Sengaja **melempar panci** ke lantai sambil berteriak "TIDAK BAHAN YANG BENAR!" (membuat error sendiri)

Tanpa `try-except`, memasak resep baru yang gagal = **dapur meledak** (program crash).
Dengan `try-except`, memasak resep baru yang gagal = **masih bisa masak dengan cara lain** (program jalan terus).

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Try | `try:` | Blok kode yang mungkin error |
| Except | `except:` | Blok yang dijalankan saat error terjadi |
| Spesifik error | `except ZeroDivisionError:` | Menangkap tipe error tertentu |
| Pesan error | `except Error as msg:` | Menangkap pesan error |
| Raise | `raise Error("pesan")` | Membuat error sendiri |
| Finally | `finally:` | Selalu dijalankan (baik error atau tidak) |
