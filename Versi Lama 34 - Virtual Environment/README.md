# BAB 10 - Virtual Environment

## Apa yang Dipelajari

- **Virtual Environment (venv)** : Lingkungan Python terisolasi untuk mengelola dependensi per proyek
- **`venv`** : Module bawaan Python untuk membuat virtual environment
- **`requirements.txt`** : File daftar package yang dibutuhkan suatu proyek
- **`pip install -r requirements.txt`** : Menginstall semua package dari file requirements
- **Mengapa virtualenv dibutuhkan** : Menghindari konflik versi antar proyek

## Struktur Folder

```
Versi Lama 34 - Virtual Environment/
└── Environment/
    ├── main.py                 ← Program utama (menggunakan numpy)
    ├── requirement.txt         ← Daftar package yang dibutuhkan
    └── project1/               ← Virtual environment yang sudah dibuat
        ├── bin/                ← Script executable (Linux/Mac)
        ├── lib/                ← Package yang terinstall di venv
        ├── pip-selfcheck.json  ← Metadata pip
        └── pyvenv.cfg          ← Konfigurasi virtual environment
```

## Penjelasan Kode

### 1. File `main.py`

```python
import numpy as np

a = np.array([1,2,3,4])
b = np.array([5,6,7,8])

print(a+b)
```

- `import numpy as np` - Mengimport package **NumPy** (library untuk komputasi numerik) dengan alias `np`.
- `np.array([1,2,3,4])` - Membuat array NumPy bernama `a` dengan isi `[1, 2, 3, 4]`.
- `np.array([5,6,7,8])` - Membuat array NumPy bernama `b` dengan isi `[5, 6, 7, 8]`.
- `print(a+b)` - Menjumlahkan kedua array **elemen per elemen**:
  - `[1+5, 2+6, 3+7, 4+8]` = `[6, 8, 10, 12]`

**Output:**
```
[ 6  8 10 12]
```

### 2. File `requirement.txt`

```
Django==2.0.2
pytz==2018.3
```

- `Django==2.0.2` - Package **Django** versi 2.0.2 (framework web Python).
- `pytz==2018.3` - Package **pytz** versi 2018.3 (untuk timezone).
- `==` berarti **lock/harus persis** versi tersebut. Bisa juga menggunakan `>=` (minimal) atau tanpa versi (versi terbaru).

### 3. Struktur `project1/` (Virtual Environment)

Folder `project1/` adalah **virtual environment** yang sudah dibuat. Strukturnya:

| Folder/File | Fungsi |
|-------------|--------|
| `pyvenv.cfg` | File konfigurasi virtual environment (path Python, versi, dll.) |
| `lib/` | Folder berisi package-package yang terinstall khusus di venv ini |
| `bin/` | Script executable seperti `python`, `pip`, `activate` (Linux/Mac) |
| `pip-selfcheck.json` | Metadata untuk pip |

## Cara Membuat Virtual Environment

### Langkah 1: Membuat Virtual Environment

```bash
python -m venv project1
```

- `python -m venv` - Menjalankan module `venv` dari Python.
- `project1` - Nama folder untuk virtual environment. Folder baru akan dibuat.

### Langkah 2: Mengaktifkan Virtual Environment

**Windows:**
```bash
project1\Scripts\activate
```

**Linux/Mac:**
```bash
source project1/bin/activate
```

Setelah diaktifkan, prompt terminal akan berubah misalnya menjadi:
```
(project1) C:\Users\...\Environment>
```

### Langkah 3: Install Package

```bash
pip install numpy
```

Package hanya terinstall di dalam virtual environment, **bukan di seluruh sistem Python**.

### Langkah 4: Install dari requirements.txt

```bash
pip install -r requirement.txt
```

- `-r` = **recursive** (baca file). Perintah ini akan menginstall semua package yang terdaftar di `requirement.txt` dengan versi yang sesuai.

### Langkah 5: Menonaktifkan Virtual Environment

```bash
deactivate
```

## Mengapa Virtual Environment Dibutuhkan?

| Tanpa Virtual Environment | Dengan Virtual Environment |
|---|---|
| Semua proyek share package yang sama | Setiap proyek punya package sendiri |
| Proyek A butuh Django 2.0, Proyek B butuh Django 4.0 = **KONFLIK!** | Django 2.0 di Proyek A, Django 4.0 di Proyek B = **AMAN** |
| Sulit membedakan versi package antar proyek | Setiap venv terisolasi dan mandiri |
| `pip install` mempengaruhi seluruh sistem | `pip install` hanya mempengaruhi venv aktif |

## Analogi

Bayangkan **ruangan laboratorium**:

- **Python global (tanpa venv)** = **Ruang kelas umum**. Semua siswa (proyek) berada di ruangan yang sama. Jika Siswa A membawa bahan kimia untuk eksperimen A dan Siswa B membawa bahan kimia untuk eksperimen B, bisa terjadi **tumpang tindih dan kontaminasi**.
- **Virtual environment** = **Bilik laboratorium pribadi**. Setiap siswa punya ruang terpisah dengan peralatan dan bahan sendiri-sendiri. Tidak ada kontaminasi antar proyek.
- **`requirements.txt`** = **Daftar bahan kimia** yang dibutuhkan. Jika kamu pindah ke lab baru, cukup serahkan daftar ini ke petugas (`pip install -r`) dan mereka akan menyiapkan semua bahan yang sama.
- **`activate`** = **Masuk ke bilik lab**. Saat aktif, semua perintah (`pip install`) hanya berpengaruh di dalam bilikmu.
- **`deactivate`** = **Keluar dari bilik lab**. Kembali ke ruang kelas umum.
