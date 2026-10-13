# BAB 12 - Anonymous atau Lambda Function

## Apa yang Dipelajari

- **Lambda function**: fungsi anonymous (tanpa nama) dalam satu baris
- Syntax: `lambda argument: expression`
- Menggunakan lambda dengan **`sort()`** dan **`key`**
- Menggunakan lambda dengan **`filter()`** untuk menyaring data
- Konsep **currying**: membuat fungsi dari fungsi

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Fungsi Biasa vs Lambda

```python
# Fungsi biasa
def f_kuadrat(angka):
    return angka**2

print(f"hasil fungsi kuadrat = {f_kuadrat(3)}")
```

- Fungsi `f_kuadrat` ditulis dengan `def`, punya nama, punya badan fungsi.
- Output: `hasil fungsi kuadrat = 9`

```python
# Lambda
kuadrat = lambda angka : angka**2
print(f"hasil lambda kuadrat = {kuadrat(5)}")
```

- **`lambda angka : angka**2`** → fungsi anonymous yang menerima 1 parameter dan mengembalikan kuadrat.
- Lambda disimpan ke variabel `kuadrat` agar bisa dipanggil.
- Output: `hasil lambda kuadrat = 25`

#### 2. Lambda dengan Banyak Parameter

```python
pangkat = lambda num,pow : num**pow
print(f"hasil lambda pangkat = {pangkat(4,2)}")
```

- Lambda bisa menerima banyak parameter dipisah koma.
- `pangkat(4,2)` → `4**2 = 16`
- Output: `hasil lambda pangkat = 16`

#### 3. Lambda untuk Sorting

```python
# Sorting biasa (alfabetis)
data_list = ["Otong","Ucup","Dudung"]
data_list.sort()
print(f"sorted list = {data_list}")
```

- `sort()` tanpa `key` → mengurutkan **secara alfabetis**.
- Output: `sorted list = ['Dudung', 'Otong', 'Ucup']`

```python
# Sorting dengan fungsi biasa
def panjang_nama(nama):
    return len(nama)

data_list.sort(key=panjang_nama)
print(f"sorted list by panjang = {data_list}")
```

- Fungsi `panjang_nama` mengembalikan **panjang** string.
- `sort(key=panjang_nama)` → mengurutkan berdasarkan panjang nama.
- Output: `sorted list by panjang = ['Ucup', 'Otong', 'Dudung']` (5, 5, 6)

```python
# Sorting dengan lambda (lebih ringkas!)
data_list = ["Otong","Ucup","Dudung"]
data_list.sort(key=lambda nama:len(nama))
print(f"sorted list by lambda = {data_list}")
```

- Lambda menggantikan fungsi `panjang_nama` secara **inline**.
- `lambda nama:len(nama)` → fungsi singkat: terima `nama`, kembalikan `len(nama)`.
- Lebih efisien karena tidak perlu membuat fungsi terpisah.

#### 4. Filter dengan Lambda

```python
data_angka = [1,2,3,4,5,6,7,8,9,10,11,12]
```

**Filter bilangan kurang dari 7:**
```python
data_angka_baru = list(filter(lambda x:x<7,data_angka))
print(data_angka_baru)
```

- `filter(kondisi, iterable)` → menyaring data berdasarkan kondisi (True/False).
- `lambda x:x<7` → fungsi yang mengembalikan `True` jika `x < 7`.
- Output: `[1, 2, 3, 4, 5, 6]`

**Filter bilangan genap:**
```python
data_genap = list(filter(lambda x:(x%2==0),data_angka))
print(data_genap)
```

- `x%2==0` → sisa bagi 2 sama dengan 0 = genap.
- Output: `[2, 4, 6, 8, 10, 12]`

**Filter bilangan ganjil:**
```python
data_ganjil = list(filter(lambda x:(x%2!=0),data_angka))
print(data_ganjil)
```

- `x%2!=0` → sisa bagi 2 tidak sama dengan 0 = ganjil.
- Output: `[1, 3, 5, 7, 9, 11]`

**Filter kelipatan 3:**
```python
data_3 = list(filter(lambda x:(x%3==0),data_angka))
print(data_3)
```

- Output: `[3, 6, 9, 12]`

#### 5. Currying dengan Lambda

```python
# Fungsi biasa
def pangkat(angka,n):
    hasil = angka**n
    return hasil

data_hasil = pangkat(5,2)
print(f"fungsi biasa = {data_hasil}")
```

- Output: `fungsi biasa = 25`

```python
# Dengan currying
def pangkat(n):
    return lambda angka:angka**n

pangkat2 = pangkat(2)
print(f"pangkat2 = {pangkat2(5)}")

pangkat3 = pangkat(3)
print(f"pangkat3 = {pangkat3(3)}")

print(f"pangkat bebas = {pangkat(4)(5)}")
```

- **Currying** = memecah fungsi menjadi beberapa fungsi kecil yang saling memanggil.
- `pangkat(2)` mengembalikan `lambda angka:angka**2` (fungsi kuadrat).
- `pangkat2(5)` → `5**2 = 25`
- `pangkat3(3)` → `3**3 = 27`
- `pangkat(4)(5)` → memanggil `pangkat(4)` dulu (menghasilkan `lambda angka:angka**4`), lalu langsung dipanggil dengan `5` → `5**4 = 625`

---

## Ringkasan Lambda

| Fitur     | Lambda                           | Fungsi Biasa                    |
|-----------|----------------------------------|---------------------------------|
| Nama      | Anonymous (tanpa nama)           | Punya nama (`def`)              |
| Baris kode| 1 baris                          | Banyak baris                    |
| Return    | Otomatis (eksplisit)             | Perlu `return`                  |
| Kapan pakai| Operasi singkat, one-liner      | Operasi kompleks                |

---

## Analogi

Bayangkan lambda seperti **stiker tempel**:

- **Fungsi biasa** = Membuat **plakat besar** dengan nama fungsi, badan, dan return. Cocok untuk pekerjaan besar.
- **Lambda** = Membuat **stiker kecil** sekali pakai. Cocok untuk tugas singkat seperti mengurutkan atau menyaring.
- **Currying** = Membuat **template stiker** yang bisa kamu pakai berkali-kali dengan isi berbeda: `pangkat(2)`, `pangkat(3)`, dll.

---

## Kesalahan Umum Pemula

- **Lambda untuk kode panjang**: Lambda hanya untuk **satu ekspresi**. Jika butuh banyak baris, pakai `def`.
- **Lupa `list()` pada `filter()`**: `filter()` menghasilkan **iterator**, bukan list. Harus dibungkus `list()`.
- **Membingungkan currying**: `pangkat(4)(5)` ≠ `pangkat(4,5)`. Yang pertama dua panggilan fungsi, yang kedua dua argument.
