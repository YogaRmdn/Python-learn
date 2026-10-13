# BAB 9 - List

## Apa yang Dipelajari

- Apa itu **list** (kumpulan data berurutan)
- Membuat list dengan berbagai tipe data
- List campuran (berbagai tipe data dalam satu list)
- Membuat list dengan `list(range(...))`
- **List comprehension**: membuat list dengan for + if

---

## Penjelasan Kode

### 1. List Angka

```python
data_angka = [1,5,2,3]
print(data_angka)
```

| Komponen | Penjelasan |
|---|---|
| `[1,5,2,3]` | List berisi 4 angka, dibungkus tanda kurung siku `[]` |
| `data_angka` | Variabel yang menunjuk ke list tersebut |

**Output:** `[1, 5, 2, 3]`

---

### 2. List String

```python
data_string = ["ucup","otong","odah"]
print(data_string)
```

List bisa berisi **string** (teks). Setiap elemen dipisahkan koma.

---

### 3. List Boolean

```python
data_boolean = [True, False, True, True]
print(data_boolean)
```

List bisa berisi nilai **boolean** (`True` / `False`).

---

### 4. List Campuran

```python
data_campuran = [1,"bala-bala",2,"cireng","ucup",True,"otong",False]
print(data_campuran)
```

Python memungkinkan **berbagai tipe data** dalam satu list: angka, string, boolean, bahkan list lain!

---

### 5. Membuat List dengan `range()`

```python
data_range = range(0,10,2)
print(data_range)
data_list = list(data_range)
print(data_list)
```

| Komponen | Penjelasan |
|---|---|
| `range(0,10,2)` | Deret angka: 0, 2, 4, 6, 8 (mulai 0, sampai sebelum 10, loncat 2) |
| `list(data_range)` | Mengkonversi `range` menjadi list |

**Output:**
```
range(0, 10, 2)
[0, 2, 4, 6, 8]
```

---

### 6. List Comprehension (For + If)

```python
list_pake_for = [i**2 for i in range(0,10)]
print(list_pake_for)
```

**Artinya:** "Buat list berisi `i**2` untuk setiap `i` dari 0 sampai 9."

**Output:** `[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]`

---

```python
list_pake_for_if = [i for i in range(0,10) if i != 5]
print(list_pake_for_if)
```

**Artinya:** "Ambil semua angka dari 0-9, **kecuali** yang bernilai 5."

**Output:** `[0, 1, 2, 3, 4, 6, 7, 8, 9]`

---

```python
list_pake_for_if = [i for i in range(0,10) if i%2 == 0]
print(list_pake_for_if)
```

**Artinya:** "Ambil semua angka **genap** dari 0-9."

**Output:** `[0, 2, 4, 6, 8]`

---

```python
list_pake_for_if = [i**2 for i in range(0,10) if i%2 != 0]
print(list_pake_for_if)
```

**Artinya:** "Kuadratkan semua angka **ganjil** dari 0-9."

**Output:** `[1, 9, 25, 49, 81]`

---

## Ringkasan List Comprehension

| Sintaks | Arti |
|---|---|
| `[i for i in range(10)]` | List angka 0-9 |
| `[i**2 for i in range(10)]` | Kuadrat dari setiap angka |
| `[i for i in range(10) if i%2==0]` | Hanya angka genap |
| `[i**2 for i in range(10) if i%2!=0]` | Kuadrat dari angka ganjil |

---

## Analogi

Bayangkan **list** seperti **rak sepatu**:

- Rak bisa berisi sepatu jenis apa saja (olahraga, sandal, sepatu formal) → seperti list campuran
- Setiap kotak sepatu punya **posisi** (nomor urut) → seperti index
- Kamu bisa menambah, menghapus, atau mengganti sepatu di rak

---

## Tips

1. List comprehension lebih **ringkas** dan **cepat** dibanding for loop biasa untuk membuat list.
2. List bisa berisi **tipe data apa saja**, bahkan list lain (nested list).
3. Gunakan `len(list)` untuk mengetahui jumlah elemen dalam list.
