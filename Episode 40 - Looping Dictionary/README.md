# BAB 20 - Looping Dictionary

## Apa yang Dipelajari

- Melooping dictionary dengan `for` (mendapatkan key)
- Menggunakan `keys()` untuk mendapatkan semua key
- Menggunakan `values()` untuk mendapatkan semua value
- Menggunakan `items()` untuk mendapatkan pasangan key-value
- Unpacking key dan value dalam loop

---

## Penjelasan Kode

### Data Awal

```python
teman_teman = {
	"cup":"ucup surucup",
	"tong":"otong surotong",
	"dung":"dudung surudung",
	"sep":"asep si kasyep",
	"cuy":"ucuy surucuy"
}
```

---

### 1. Looping Biasa (Mendapatkan Key)

```python
for teman in teman_teman:
	print(teman)
```

Ketika kamu melooping dictionary **tanpa metode apapun**, yang keluar adalah **key**-nya saja.

**Output:**
```
cup
tong
dung
sep
cuy
```

---

### 2. Menggunakan `keys()`

```python
keys = teman_teman.keys()
print(keys)

for key in teman_teman.keys():
	print(teman_teman.get(key))
```

| Komponen | Penjelasan |
|---|---|
| `keys()` | Mengembalikan **semua key** dalam dictionary |
| `teman_teman.get(key)` | Mengambil value berdasarkan key |

**Output keys():** `dict_keys(['cup', 'tong', 'dung', 'sep', 'cuy'])`

---

### 3. Menggunakan `values()`

```python
values = teman_teman.values()
print(values)

for value in teman_teman.values():
	print(value)
```

| Komponen | Penjelasan |
|---|---|
| `values()` | Mengembalikan **semua value** dalam dictionary |

**Output values():** `dict_values(['ucup surucup', 'otong surotong', ...])`

---

### 4. Menggunakan `items()`

```python
items = teman_teman.items()
print(items)

for item in teman_teman.items():
	print(item)
```

| Komponen | Penjelasan |
|---|---|
| `items()` | Mengembalikan **pasangan (key, value)** sebagai tuple |

**Output items():** `dict_items([('cup', 'ucup surucup'), ('tong', 'otong surotong'), ...])`

Setiap item dicetak sebagai **tuple**: `('cup', 'ucup surucup')`

---

### 5. Unpacking Key dan Value

```python
for key, value in teman_teman.items():
	print(f"key = {key}, value = {value}")
```

| Komponen | Penjelasan |
|---|---|
| `for key, value in ...items()` | **Unpacking**: key dan value dipisahkan ke variabel terpisah |

**Output:**
```
key = cup, value = ucup surucup
key = tong, value = otong surotong
key = dung, value = dudung surudung
key = sep, value = asep si kasyep
key = cuy, value = ucuy surucuy
```

---

## Ringkasan Metode Looping

| Metode | Yang Di-loop | Cocok untuk |
|---|---|---|
| `for x in dict` | **Key** saja | Saat hanya butuh key |
| `for x in dict.keys()` | **Key** saja | Lebih eksplisit |
| `for x in dict.values()` | **Value** saja | Saat hanya butuh value |
| `for x in dict.items()` | **(key, value)** | Saat butuh keduanya |
| `for k, v in dict.items()` | **key + value** (di-unpack) | Cara paling umum & rapi |

---

## Analogi

Bayangkan **daftar rapot siswa**:

- **`keys()`**: Daftar **nama siswa** saja: Budi, Andi, Siti...
- **`values()`**: Daftar **nilai** saja: 85, 90, 78...
- **`items()`**: Daftar **pasangan**: (Budi, 85), (Andi, 90), (Siti, 78)...
- **`for k, v in items()`**: Kamu bisa langsung baca: "Budi nilainya 85, Andi nilainya 90..."

---

## Tips

1. **`items()` + unpacking** (`for k, v in dict.items()`) adalah cara paling **populer dan Pythonic** untuk melooping dictionary.
2. `keys()` dan `values()` mengembalikan **view objects** (bukan list), tapi bisa di-loop seperti list.
3. Gunakan `list(dict.keys())` jika kamu benar-benar membutuhkan list dari key.
