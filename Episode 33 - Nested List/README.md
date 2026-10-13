# BAB 13 - Nested List

## Apa yang Dipelajari

- Apa itu **nested list** (list dalam list)
- Membuat list 2D (dua dimensi)
- Mengakses elemen dalam nested list
- Melooping nested list
- Bahaya reference pada nested list

---

## Penjelasan Kode

### Membuat Nested List

```python
data_0 = [1,2]
data_1 = [3,4,5]

data_list_biasa = [1,2,3,4]
print(f"list biasa = {data_list_biasa}")

list_2D = [data_0, data_1, 6, 7]
print(f"list 2D = {list_2D}")
```

| Komponen | Penjelasan |
|---|---|
| `data_0 = [1,2]` | List biasa berisi 2 angka |
| `data_1 = [3,4,5]` | List biasa berisi 3 angka |
| `list_2D = [data_0, data_1, 6, 7]` | List berisi **list lain** sebagai elemen + angka biasa |

**Output:**
```
list biasa = [1, 2, 3, 4]
list 2D = [[1, 2], [3, 4, 5], 6, 7]
```

---

### Membuat Nested List untuk Data Peserta

```python
peserta_0 = ["ucup",25,"Laki-laki"]
peserta_1 = ["otong",10,"Laki-laki"]
peserta_2 = ["dedeh",50,"Wanita"]

list_peserta = [peserta_0, peserta_1, peserta_2]
print(f"peserta = {list_peserta}")
```

Setiap peserta adalah **list** berisi `[nama, umur, gender]`.

**Output:**
```
peserta = [['ucup', 25, 'Laki-laki'], ['otong', 10, 'Laki-laki'], ['dedeh', 50, 'Wanita']]
```

---

### Melooping Nested List

```python
for peserta in list_peserta:
	print(f"nama\t: {peserta[0]}")
	print(f"umur\t: {peserta[1]}")
	print(f"gender\t: {peserta[2]}\n")
```

| Komponen | Penjelasan |
|---|---|
| `for peserta in list_peserta` | Setiap iterasi, `peserta` berisi satu sub-list |
| `peserta[0]` | Index 0 dari sub-list → **nama** |
| `peserta[1]` | Index 1 → **umur** |
| `peserta[2]` | Index 2 → **gender** |
| `\t` | Tab (spasi lebar) untuk formatting |
| `\n` | Baris kosong antar peserta |

**Output:**
```
nama    : ucup
umur    : 25
gender  : Laki-laki

nama    : otong
umur    : 10
gender  : Laki-laki

nama    : dedeh
umur    : 50
gender  : Wanita
```

---

### Bahaya Reference pada Nested List

```python
list_copy = list_peserta.copy()
print(f"peserta = {list_copy}")
peserta_0[0] = "michael"
print(f"peserta = {list_copy}")
print(f"peserta = {list_peserta}")
```

`copy()` hanya membuat **shallow copy** — sub-list di dalam masih tetap **reference** yang sama!

Saat `peserta_0[0] = "michael"` dijalankan, **kedua list** (`list_copy` dan `list_peserta`) ikut berubah karena `peserta_0` masih objek yang sama.

**Output:**
```
peserta = [['michael', 25, 'Laki-laki'], ...]
```

---

## Cara Mengakses Elemen 2D

```
list_2D = [[1,2], [3,4,5], 6, 7]

list_2D[0]      → [1, 2]      (sub-list pertama)
list_2D[0][0]   → 1           (elemen pertama dari sub-list pertama)
list_2D[1][2]   → 5           (elemen ketiga dari sub-list kedua)
list_2D[2]      → 6           (bukan sub-list, angka biasa)
```

---

## Analogi

Bayangkan **lemari buku** dengan beberapa **rak**:

- **Rak 1** berisi buku `[1, 2]`
- **Rak 2** berisi buku `[3, 4, 5]`
- **Rak 3** berisi buku tunggal `6`
- **Rak 4** berisi buku tunggal `7`

Untuk mengambil buku tertentu, kamu perlu tahu:
1. Di **rak** keberapa? (index luar)
2. Di **posisi** keberapa dalam rak tersebut? (index dalam)

---

## Tips

1. Nested list sangat berguna untuk merepresentasikan **data tabel** (baris dan kolom).
2. Gunakan **loop bersarang** (nested loop) untuk mengakses semua elemen.
3. Hati-hati dengan reference! Untuk nested list, gunakan `deepcopy()` (dibahas di episode berikutnya).
