# BAB 1 - Episode 61: NumPy - Studi Kasus PIP

## Apa yang Dipelajari

- Memasang library eksternal menggunakan **pip** (Python Package Installer)
- Mengimpor dan menggunakan library **NumPy** untuk komputasi numerik
- Membuat **array 1D** (vektor) dan **array 2D** (matriks) menggunakan `np.array()`
- Melakukan **operasi vektor/matriks**: pangkat, perkalian skalar, penjumlahan
- Membuat array **zeros** (nol semua) dan **ones** (satu semua)

---

## Penjelasan Kode

### File: `main_app.py`

```python
import numpy as np
```

- Baris ini mengimpor seluruh library NumPy dan memberi alias **`np`** agar penulisan lebih pendek.
- Library NumPy **tidak bawaan Python**, jadi harus diinstal dulu lewat terminal:
  ```
  pip install numpy
  ```
- Istilah **PIP** (Python Package Installer) adalah tools bawaan Python untuk memasang library dari repository [PyPI](https://pypi.org).

---

### Membuat Array 1D (Vektor)

```python
list_a = [1, 2, 3, 4]
vector_a = np.array([1, 2, 3, 4])
```

| Variabel      | Tipe         | Penjelasan                                        |
|---------------|--------------|----------------------------------------------------|
| `list_a`      | `list` biasa | List Python biasa, **tidak bisa** operasi matematika |
| `vector_a`    | `np.ndarray` | Array NumPy, **bisa** operasi matematika langsung   |

```python
print(f"list_a = {list_a}")
# print(list_a**2)  # INI AKAN GAGAL! List Python tidak mendukung operator **
print(f"vector_a = {vector_a}")
print(f"a pangkat 2 = {vector_a**2}")
print(f"a kali 5 = {vector_a*5}")
```

- `list_a ** 2` akan **error** karena Python tidak mengerti "pangkat 2" untuk list biasa.
- `vector_a ** 2` menghasilkan `[1, 4, 9, 16]` — setiap elemen dipangkatkan 2 **secara otomatis** (operasi elemen per elemen).
- `vector_a * 5` menghasilkan `[5, 10, 15, 20]` — setiap elemen dikali 5.

> **Inti:** NumPy memungkinkan operasi matematika pada seluruh array sekaligus tanpa perlu perulangan `for`.

---

### Membuat Array 2D (Matriks)

```python
matrix_b = np.array([(1, 2), (3, 4)])
print(f"matrix b = \n{matrix_b}")
print(f"matrix b^2 = \n{matrix_b**2}")
```

- `np.array([(1,2), (3,4)])` membuat matriks 2x2:
  ```
  [[1 2]
   [3 4]]
  ```
- `matrix_b ** 2` menghasilkan:
  ```
  [[ 1  4]
   [ 9 16]]
  ```

---

### Membuat Array dengan `zeros` dan `ones`

```python
zeros_c = np.zeros((2, 2))
print(f"zeros c = \n{zeros_c}")
```

- `np.zeros((2,2))` membuat matriks 2x2 yang **semua elemennya 0.0** (tipe float).

```python
ones_d = np.ones((2, 2))
print(f"ones c = \n{ones_d}")
```

- `np.ones((2,2))` membuat matriks 2x2 yang **semua elemennya 1.0** (tipe float).

---

### Operasi Campuran

```python
jumlah = matrix_b + matrix_b**2 + ones_d
print(f"jumlah = \n{jumlah}")
```

- Program menghitung: `matrix_b + matrix_b² + ones_d`
- Secara matematis:
  - Elemen (1,1): `1 + 1² + 1 = 3`
  - Elemen (1,2): `2 + 2² + 1 = 7`
  - Elemen (2,1): `3 + 3² + 1 = 13`
  - Elemen (2,2): `4 + 4² + 1 = 21`
- Hasil:
  ```
  [[ 3.  7.]
   [13. 21.]]
  ```

---

### Ringkasan Output Program

```
list_a = [1, 2, 3, 4]
vector_a = [1 2 3 4]
a pangkat 2 = [ 1  4  9 16]
a kali 5 = [ 5 10 15 20]
matrix b =
[[1 2]
 [3 4]]
matrix b^2 =
[[ 1  4]
 [ 9 16]]
zeros c =
[[0. 0.]
 [0. 0.]]
ones c =
[[1. 1.]
 [1. 1.]]
jumlah =
[[ 3.  7.]
 [13. 21.]]
```

---

## Analogi

Bayangkan kamu punya **kalkulator ajaib**.

- **List biasa** seperti kertas biasa — kamu harus tulis angka satu per satu dan hitung manual.
- **NumPy array** seperti kalkulator ajaib — kamu kasih semua angka sekaligus, lalu perintah "kuadratkan semua!" dan **langsung jadi** tanpa perlu menghitung satu per satu.

Matriks seperti tabel Excel mini: ada baris dan kolom, dan kamu bisa melakukan operasi pada seluruh tabel sekaligus — misalnya, "tambahkan semua nilai dengan kuadratnya sendiri!"

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Import library | `import numpy as np` | Mengimpor NumPy dengan alias `np` |
| Install library | `pip install numpy` | Memasang library dari PyPI |
| Array 1D | `np.array([1,2,3,4])` | Membuat vektor 1 dimensi |
| Array 2D | `np.array([(1,2),(3,4)])` | Membuat matriks 2 dimensi |
| Operasi pangkat | `arr ** 2` | Setiap elemen dipangkatkan 2 |
| Operasi kali | `arr * 5` | Setiap elemen dikali 5 |
| Matriks nol | `np.zeros((2,2))` | Matriks 2x2 berisi nol semua |
| Matriks satu | `np.ones((2,2))` | Matriks 2x2 berisi satu semua |
