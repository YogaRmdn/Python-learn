# BAB 11 - Function & Arguments (Argumen Fungsi)

## Apa yang Dipelajari

- Fungsi dengan argumen sederhana
- Keyword arguments (argumen bernama)
- Default arguments (argumen bawaan)
- Urutan parameter yang benar
- Kesalahan umum dalam penggunaan argumen

---

## Penjelasan Kode

### File: `function with argument.py`

#### 1. Fungsi dengan Argumen Sederhana (Positional)

```python
def siswa(nama):
    print('siswa ini bernama:', nama)

siswa('mario')
```

- Parameter `nama` akan menerima nilai `'mario'` saat fungsi dipanggil.
- Output: `"siswa ini bernama: mario"`

---

#### 2. Keyword Arguments (Argumen Bernama)

```python
def guru(nama, pelajaran):
    print('guru ini bernama:', nama)
    print('mengajar:', pelajaran)
```

Fungsi `guru` menerima dua parameter: `nama` dan `pelajaran`.

---

**Pemanggilan dengan urutan benar:**

```python
guru(nama='popong', pelajaran='seni rupa')
```

- Output: `"guru ini bernama: popong"` dan `"mengajar: seni rupa"`

---

**Pemanggilan dengan urutan terbalik (tetap benar karena pakai keyword):**

```python
guru(pelajaran='olah raga', nama='endang')
```

- Output: `"guru ini bernama: endang"` dan `"mengajar: olah raga"`
- Karena menggunakan **keyword arguments**, urutan tidak masalah.

---

**Pemanggilan yang SALAH:**

```python
guru('olah raga', 'raihan')  # ini contoh yang salah
```

- `'olah raga'` masuk ke parameter `nama` → "guru ini bernama: olah raga"
- `'raihan'` masuk ke parameter `pelajaran` → "mengajar: raihan"
- **Logikanya salah!** Karena urutan posisi tidak sesuai keinginan.

---

#### 3. Default Arguments (Argumen Bawaan)

```python
def penjagaSekolah(nama, shift='siang', galak='tidak'):
    print('penjaga sekolah ini bernama:', nama)
    print('shiftnya:', shift)
    print('galak?:', galak)
```

- `shift='siang'` → nilai bawaan (default) adalah `'siang'`.
- `galak='tidak'` → nilai bawaan (default) adalah `'tidak'`.
- Jika tidak ditentukan, nilai default akan digunakan.

---

**Pemanggilan dengan hanya nama (sisanya default):**

```python
penjagaSekolah('Entis')
```

- Output:
  - `"penjaga sekolah ini bernama: Entis"`
  - `"shiftnya: siang"` (default)
  - `"galak?: tidak"` (default)

---

**Pemanggilan mengubah shift saja:**

```python
penjagaSekolah('Maman', shift='malam')
```

- Output:
  - `"penjaga sekolah ini bernama: Maman"`
  - `"shiftnya: malam"` (diubah)
  - `"galak?: tidak"` (default)

---

**Pemanggilan mengubah galak saja:**

```python
penjagaSekolah('Asep', galak='Sangat')
```

- Output:
  - `"penjaga sekolah ini bernama: Asep"`
  - `"shiftnya: siang"` (default)
  - `"galak?: Sangat"` (diubah)

---

**Pemanggilan yang MENYEBABKAN ERROR:**

```python
penjagaSekolah(shift='malam', galak='iya')
```

- **Error!** Parameter `nama` tidak memiliki nilai default, tapi tidak diberikan nilai.
- `nama` adalah parameter **wajib**.

---

## Ringkasan Tipe Argumen

| Tipe | Penjelasan | Contoh |
|------|------------|--------|
| **Positional** | Berdasarkan urutan | `siswa('mario')` |
| **Keyword** | Berdasarkan nama parameter | `guru(nama='popong', pelajaran='seni')` |
| **Default** | Punya nilai bawaan | `def f(x, y=10)` |

---

## Urutan Parameter yang Benar

```
def fungsi(param_wajib, param_default='nilai'):
                  │              │
                  │              └── Bisa dilewati (ada nilai default)
                  └── Harus diisi (tidak ada nilai default)
```

**Aturan:**
1. Parameter wajib (tanpa default) harus diisi.
2. Parameter default bisa dilewati.
3. Saat pakai keyword arguments, urutan tidak masalah.

---

## Analogi

Bayangkan kamu **mengisi formulir pendaftaran**:

- **Positional**: Isi kolom dari atas ke bawah, urutan sudah ditentukan.
- **Keyword**: Kamu tulis "Nama: Budi", "Alamat: Jl. Merdeka" — urutan tidak masalah karena sudah ada labelnya.
- **Default**: Jika kolom "Kota" dikosongkan, otomatis terisi "Bandung" (nilai bawaan).

**Error:** Kolom "Nama" wajib diisi. Jika kosong → formulir ditolak!

---

## Tips untuk Pemula

- Parameter **wajib** diletakkan di awal, parameter **default** di akhir.
- Gunakan **keyword arguments** untuk kode yang lebih mudah dibaca.
- Hati-hati: `guru('olah raga', 'raihan')` akan salah input karena posisi tidak sesuai.
- Default value sebaiknya menggunakan nilai yang **aman** (bukan `None` kecuali memang perlu).
