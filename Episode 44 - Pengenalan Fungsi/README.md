# BAB 4 - Pengenalan Fungsi

## Apa yang Dipelajari

- Apa itu **fungsi** dan kenapa fungsi penting
- Cara membuat fungsi dengan keyword `def`
- Cara memanggil fungsi
- Docstring: komentar dokumentasi di dalam fungsi
- Fungsi bisa dipanggil **berulang kali**
- Pemanggilan fungsi harus dilakukan **setelah** fungsi didefinisikan

---

## Penjelasan Kode

### File 1: `main_app.py`

#### 1. Membuat Fungsi `hello_world()`

```python
def hello_world():
    '''fungsi menampilkan hello world'''
    print("hello world")
    print("Kepada Ucup Surucup")
    print("Dan juga kepada Otong Surotong")
```

- **`def`** → keyword Python untuk mendefinisikan (membuat) fungsi.
- **`hello_world()`** → nama fungsi diikuti tanda kurung `()`. Kosong berarti tidak menerima input (argument).
- **`'''fungsi menampilkan hello world'''`** → **docstring**, yaitu komentar dokumentasi yang menjelaskan apa yang dilakukan fungsi. Bisa diakses dengan `help(hello_world)`.
- **Badan fungsi** → semua baris yang di-**indentasi** (dikunci 4 spasi) di bawah `def`. Ini yang akan dijalankan saat fungsi dipanggil.

#### 2. Memanggil Fungsi

```python
hello_world()
hello_world()
```

- Fungsi dipanggil dengan menulis **nama fungsi + tanda kurung**.
- `hello_world()` dipanggil **2 kali**, sehingga isi fungsi dieksekusi 2 kali.
- Output:

```
hello world
Kepada Ucup Surucup
Dan juga kepada Otong Surotong
hello world
Kepada Ucup Surucup
Dan juga kepada Otong Surotong
```

#### 3. Fungsi Harus Didefinisikan Dulu

```python
# fungsi()

def fungsi():
    '''pemanggilan fungsi harus setelah dibuat'''
    print("Ini adalah fungsi")

fungsi()
```

- Baris `# fungsi()` yang dikomentari menunjukkan: jika fungsi `fungsi()` dipanggil **sebelum** didefinisikan, akan terjadi **error** (`NameError`).
- Fungsi baru bisa dipanggil **setelah** baris `def`-nya ditulis.

---

### File 2: `latihan_fungsi.py`

#### 1. Membuat Fungsi `header()`

```python
def header():
    os.system("clear")
    print(f"{'SELAMAT DATANG':^20}")
    print(f"{'DATA MAHASISWA':^20}")
    print(f"{'TAHUN 2045':^20}")
    print("-"*20)
```

- Fungsi `header()` berisi kode untuk menampilkan header program (judul di layar).
- Dengan membuat fungsi, kode header **tidak perlu ditulis berulang** di dalam loop.
- Cukup panggil `header()` di dalam loop.

#### 2. Menggunakan Fungsi di Dalam Loop

```python
while True:
    header()  # ← memanggil fungsi header
    mahasiswa = dict.fromkeys(mahasiswa_template.keys())
    # ... input data ...
    # ... tampilkan data ...
    is_done = input("Mau tambah lagi bro (y/n)? ")
    if is_done == "n":
        break
```

- Di dalam `while True`, fungsi `header()` dipanggil di setiap iterasi.
- Ini membuat kode lebih **rapi** dan **mudah dirawat**.
- Jika ingin mengubah header, cukup ubah di satu tempat (di dalam fungsi).

---

## Struktur Fungsi

```
def nama_fungsi(argument):     ← Header fungsi
    '''docstring'''             ← Dokumentasi
    # badan fungsi              ← Indentasi 4 spasi
    return output               ← (opsional) mengembalikan nilai
```

| Bagian       | Keterangan                                    |
|--------------|-----------------------------------------------|
| `def`        | Keyword untuk mendefinisikan fungsi           |
| `nama_fungsi`| Nama fungsi (ikuti penamaan snake_case)       |
| `()`         | Tanda kurung (kosong jika tanpa argument)     |
| `docstring`  | String dokumentasi (opsional tapi disarankan) |
| Badan fungsi | Blok kode yang dijalankan saat dipanggil      |
| `return`     | Mengembalikan nilai ke pemanggil (opsional)   |

---

## Analogi

Bayangkan fungsi itu seperti **mesin minuman otomatis**:

1. **`def mesin():`** → Kamu membangun mesin minumannya.
2. **`print("minuman jadi")`** → Di dalam mesin, ada proses membuat minuman.
3. **`mesin()`** → Kamu menekan tombol, dan mesin mengeluarkan minuman.
4. Kamu bisa menekan tombol **berulang kali** tanpa harus membangun mesin lagi.
5. **Docstring** → Stiker di mesin yang tertulis "Mesin ini untuk membuat minuman".

---

## Manfaat Menggunakan Fungsi

| Tanpa Fungsi                      | Dengan Fungsi                          |
|-----------------------------------|----------------------------------------|
| Kode berulang di banyak tempat    | Kode ditulis sekali, dipanggil berkali |
| Sulit debug (perbaiki banyak tempat)| Debug cukup di satu fungsi           |
| Kode panjang dan berantakan       | Kode rapi dan terstruktur              |
| Sulit dipahami                    | Mudah dibaca karena modular            |
