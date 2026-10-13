# BAB 5 - Fungsi dengan Argument

## Apa yang Dipelajari

- Memberikan **input (argument)** ke dalam fungsi
- **Positional argument**: argument berdasarkan urutan
- **Keyword argument**: argument berdasarkan nama parameter
- Fungsi bisa menerima **satu atau lebih** argument
- Fungsi bisa menerima argument berupa **list**

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Template Fungsi dengan Argument

```python
# def nama_fungsi(argument):
#     Badan fungsi
```

- Ini adalah **sintaks dasar** fungsi dengan argument.
- `argument` adalah **parameter** (nama variabel di dalam fungsi) yang akan menerima nilai dari luar.

#### 2. Fungsi `hello_world(nama)`

```python
def hello_world(nama):
    '''fungsi hello world menerima input dengan variable nama'''
    print(f"Selamat datang dunia wahai {nama}")

hello_world("ucup")
hello_world("Asyep")
```

- **Parameter**: `nama` → variabel penampung di dalam fungsi.
- **Argument**: `"ucup"` dan `"Asyep"` → nilai aktual yang dikirim saat pemanggilan.
- Saat `hello_world("ucup")` dipanggil:
  - `nama` = `"ucup"`
  - Output: `Selamat datang dunia wahai ucup`
- Saat `hello_world("Asyep")` dipanggil:
  - `nama` = `"Asyep"`
  - Output: `Selamat datang dunia wahai Asyep`

#### 3. Fungsi `tambah(angka_1, angka_2)`

```python
def tambah(angka_1,angka_2):
    '''fungsi tambah'''
    hasil = angka_1 + angka_2
    print(f"{angka_1} + {angka_2} = {hasil}")

tambah(1,5)
tambah(100000,1)
```

- Fungsi ini menerima **2 argument positional**: `angka_1` dan `angka_2`.
- **Positional argument** berarti urutan sangat penting:
  - `tambah(1,5)` → `angka_1=1`, `angka_2=5` → Output: `1 + 5 = 6`
  - `tambah(100000,1)` → `angka_1=100000`, `angka_2=1` → Output: `100000 + 1 = 100001`

#### 4. Fungsi dengan Argument List

```python
def say_hi(list_peserta):
    '''fungsi say hi'''
    data_peserta = list_peserta.copy()
    for peserta in data_peserta:
        print(f"Yang terhormat {peserta}")

anggota_boyband = ["Ucup","Otong","Dudung"]
say_hi(anggota_boyband)
```

- `list_peserta` menerima sebuah **list** sebagai argument.
- `list_peserta.copy()` → menyalin list agar tidak mengubah list asli di luar fungsi.
- Loop `for` mencetak sapaan untuk setiap nama di dalam list.

---

## Perbedaan Parameter vs Argument

| Istilah     | Definisi                                        | Contoh                    |
|-------------|-------------------------------------------------|---------------------------|
| **Parameter** | Nama variabel di dalam definisi fungsi        | `def tambah(a, b):` → `a` dan `b` adalah parameter |
| **Argument**  | Nilai aktual yang dikirim saat pemanggilan    | `tambah(1, 5)` → `1` dan `5` adalah argument |

---

## Jenis Argument

### 1. Positional Argument

```python
def sapa(nama, pesan):
    print(f"{nama}: {pesan}")

sapa("Ucup", "Halo")  # urutan penting: nama="Ucup", pesan="Halo"
```

- Argument diurutkan sesuai posisi parameter.
- **Tidak boleh** melewati urutan atau mengubah posisi.

### 2. Keyword Argument

```python
sapa(pesan="Halo", nama="Ucup")  # pakai nama parameter, urutan bebas
```

- Argument ditulis dengan **nama parameter** diikuti `=`.
- Urutan **tidak penting** karena sudah ditentukan oleh nama parameter.

---

## Analogi

Bayangkan fungsi itu seperti **resep masakan**:

- **Parameter** (`angka_1`, `angka_2`) = **Bahan-bahan** yang tertulis di resep (telur, garam).
- **Argument** (`1`, `5`) = **Jumlah aktual** bahan yang kamu pakai (1 butir telur, 5 gram garam).
- Saat kamu membuat resep yang sama untuk porsi berbeda, kamu mengganti jumlah bahannya saja.

---

## Kesalahan Umum Pemula

- **Jumlah argument tidak cocok**: `tambah(1)` akan error karena fungsi `tambah` butuh 2 argument, tapi cuma dikasih 1.
- **Urutan salah** (positional): `tambah("hello", 5)` akan error karena Python mencoba `100000 + "hello"` (string + number).
- **Lupa `.copy()` pada list**: Jika tidak dicopy, perubahan di dalam fungsi akan mengubah list asli.
