# BAB 12 - Copy Pada List

## Apa yang Dipelajari

- Konsep **pass by reference** dalam Python
- Mengapa menyalin list dengan `b = a` tidak membuat salinan baru
- Menggunakan `copy()` untuk membuat salinan independen
- Memahami **memory address** dengan `id()` dan `hex()`

---

## Penjelasan Kode

### Membuat List Awal

```python
a = ["Ucup","Otong","Dudung"]
print(f"a = {a}")
```

List `a` dibuat dengan 3 elemen.

---

### Pass by Reference

```python
b = a  # pass by reference
print(f"b = {b}")
```

| Komponen | Penjelasan |
|---|---|
| `b = a` | **Bukan** membuat salinan baru! `b` menunjuk ke **list yang sama** dengan `a` |
| `pass by reference` | Kedua variabel (`a` dan `b`) merujuk ke **alamat memori yang sama** |

> **Penting:** Dalam Python, `b = a` tidak membuat salinan list. `b` hanya **alias** (nama lain) dari `a`.

---

### Mengubah Salah Satu Memengaruhi Keduanya

```python
a[1] = "Michael"
b.sort()
print(f"a = {a}")
print(f"b = {b}")
```

**Output:**
```
a = ['Ucup', 'Michael', 'Dudung']
b = ['Dudung', 'Michael', 'Ucup']
```

Karena `a` dan `b` menunjuk ke **list yang sama**, perubahan pada salah satu **memengaruhi keduanya**.

- `a[1] = "Michael"` → mengubah list asli
- `b.sort()` → mengurutkan list yang sama

---

### Melihat Memory Address

```python
print(f"address a = {hex(id(a))}")
print(f"address b = {hex(id(b))}")
```

| Fungsi | Penjelasan |
|---|---|
| `id(a)` | Mengembalikan **alamat memori** dari `a` |
| `hex()` | Mengkonversi angka ke format heksadesimal |

**Output (contoh):**
```
address a = 0x1a2b3c4d
address b = 0x1a2b3c4d
```

**Alamat sama** → membuktikan bahwa `a` dan `b` adalah **list yang sama**.

---

### Menggunakan copy() — Salinan Baru

```python
c = a.copy()  # full duplikat / data baru
```

| Komponen | Penjelasan |
|---|---|
| `a.copy()` | Membuat **salinan baru** dari list `a` |
| `c` | List baru yang **independen** dari `a` |

---

### Membandingkan Alamat

```python
print(f"address a = {hex(id(a))}")
print(f"address b = {hex(id(b))}")
print(f"address c = {hex(id(c))}")
```

**Output (contoh):**
```
address a = 0x1a2b3c4d
address b = 0x1a2b3c4d
address c = 0x5e6f7a8b
```

`a` dan `b` punya alamat **sama**, tapi `c` punya alamat **berbeda** → `c` benar-benar salinan baru.

---

### Mengubah Salinan Independen

```python
c[0] = "Dadang"
print(f"a = {a}")
print(f"b = {b}")
print(f"c = {c}")
```

**Output:**
```
a = ['Ucup', 'Michael', 'Dudung']
b = ['Dudung', 'Michael', 'Ucup']
c = ['Dadang', 'Michael', 'Ucup']
```

Hanya `c` yang berubah! `a` dan `b` tetap sama karena `c` adalah salinan independen.

---

## Ringkasan

| Sintaks | Hasil | Independen? |
|---|---|---|
| `b = a` | `b` menunjuk ke list yang sama | **Tidak** (reference) |
| `c = a.copy()` | `c` adalah salinan baru | **Ya** (copy) |

---

## Analogi

Bayangkan sebuah **dokumen Google**:

- **`b = a`**: Kamu dan temanmu membuka **dokumen yang sama**. Jika salah satu mengedit, yang lain juga berubah (karena kalian melihat dokumen yang sama)
- **`c = a.copy()`**: Kamu **mendownload** dokumen itu dan mengedit salinannya. Dokumen asli tidak berubah.

---

## Tips

1. **Selalu gunakan `copy()`** saat kamu ingin membuat salinan list yang tidak terpengaruh perubahan asli.
2. Gunakan `hex(id(variabel))` untuk mengecek apakah dua variabel menunjuk ke objek yang sama.
3. `copy()` hanya membuat **shallow copy** (untuk nested list, gunakan `deepcopy()` — dibahas di episode selanjutnya).
