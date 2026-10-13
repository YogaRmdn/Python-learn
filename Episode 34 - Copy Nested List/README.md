# BAB 14 - Copy Nested List

## Apa yang Dipelajari

- Perbedaan **shallow copy** dan **deep copy**
- Menggunakan `copy()` (shallow copy) pada nested list
- Menggunakan `deepcopy()` dari modul `copy`
- Memahami kapan `copy()` aman dan kapan perlu `deepcopy()`

---

## Penjelasan Kode

### Data Awal

```python
data_0 = [1,2]
data_1 = [3,4]

data_2D = [data_0, data_1, 10]
data_2D_copy = data_2D.copy()

print(f"data = {data_2D}")
print(f"data copy = {data_2D_copy}")
```

**Output:**
```
data = [[1, 2], [3, 4], 10]
data copy = [[1, 2], [3, 4], 10]
```

---

### Mengakses Elemen Nested

```python
data = data_2D[1][0]
print(f"data = {data}")
```

| Komponen | Penjelasan |
|---|---|
| `data_2D[1]` | Ambil sub-list kedua: `[3, 4]` |
| `data_2D[1][0]` | Ambil elemen pertama dari sub-list kedua: `3` |

**Output:** `data = 3`

---

### Membandingkan Memory Address (Shallow Copy)

```python
print(f"address asli = {hex(id(data_2D))}")
print(f"address copy = {hex(id(data_2D_copy))}")

print("address dari member ke-1")
print(f"address asli = {hex(id(data_2D[0]))}")
print(f"address copy = {hex(id(data_2D_copy[0]))}")
```

**Output (contoh):**
```
address asli = 0x1a2b3c4d
address copy = 0x5e6f7a8b          ← Berbeda (list luar baru)

address dari member ke-1
address asli = 0x9a8b7c6d
address copy = 0x9a8b7c6d          ← SAMA! (sub-list masih reference)
```

> **Ini masalah!** Meskipun list luarnya sudah copy, **sub-list di dalamnya masih menunjuk ke objek yang sama**.

---

### Shallow Copy Gagal Mengubah Sub-List

```python
data_2D[1][0] = 5
data_2D[2] = 9

print(f"data = {data_2D}")
print(f"data copy = {data_2D_copy}")
```

**Output:**
```
data = [[1, 2], [5, 4], 9]
data copy = [[1, 2], [5, 4], 10]
```

Perhatikan:
- `data_2D[2] = 9` → Hanya mengubah list asli (karena elemen integer **di-replace**)
- `data_2D[1][0] = 5` → **Juga mengubah copy!** Karena sub-list `[3, 4]` adalah objek yang sama

---

### Deep Copy — Solusinya

```python
from copy import deepcopy

data_2D = [data_0, data_1, 10]
data_2D_deepcopy = deepcopy(data_2D)
```

| Komponen | Penjelasan |
|---|---|
| `from copy import deepcopy` | Mengimpor fungsi `deepcopy` dari modul `copy` |
| `deepcopy(data_2D)` | Membuat salinan **total** — termasuk semua sub-list |

---

### Membandingkan Address (Deep Copy)

```python
print(f"address asli = {hex(id(data_2D))}")
print(f"address deep = {hex(id(data_2D_deepcopy))}")

print("address dari member ke-1")
print(f"address asli = {hex(id(data_2D[0]))}")
print(f"address copy = {hex(id(data_2D_deepcopy[0]))}")
```

**Output (contoh):**
```
address asli = 0x1a2b3c4d
address deep = 0xabcdef12          ← Berbeda

address dari member ke-1
address asli = 0x9a8b7c6d
address copy = 0x12345678          ← JUGA BERBEDA!
```

---

### Deep Copy Independen

```python
data_2D[1][0] = 30
print(f"data = {data_2D}")
print(f"data copy = {data_2D_copy}")
print(f"data deep = {data_2D_deepcopy}")
```

**Output:**
```
data = [[1, 2], [30, 4], 10]
data copy = [[1, 2], [5, 4], 10]
data deep = [[1, 2], [3, 4], 10]    ← TIDAK BERUBAH!
```

---

## Ringkasan: Shallow vs Deep Copy

| Aspek | Shallow Copy (`.copy()`) | Deep Copy (`deepcopy()`) |
|---|---|---|
| List luar | Salinan baru | Salinan baru |
| Sub-list | **Masih reference** | **Juga salinan baru** |
| Mengubah sub-list asli | **Memengaruhi copy** | **Tidak memengaruhi** |
| Kecepatan | Lebih cepat | Lebih lambat |
| Kapan digunakan | List tanpa nested | **Nested list** |

---

## Analogi

Bayangkan kamu memfotokopi **buku catatan**:

- **Shallow copy**: Kamu memfotokopi **sampul dan daftar isi** saja. Isi catatan di dalam masih **buku yang sama** — jika orang lain menulis di buku asli, catatanmu juga ikut berubah.
- **Deep copy**: Kamu memfotokopi **seluruh halaman** termasuk semua catatan di dalamnya. Ini benar-benar buku baru yang **independen**.

---

## Tips

1. Gunakan `.copy()` untuk list **sederhana** (tanpa nested list).
2. Gunakan `deepcopy()` untuk **nested list** agar benar-benar independen.
3. `deepcopy()` lebih lambat, jadi hanya gunakan saat benar-benar diperlukan.
