# BAB 17 - Tuples dan Sets

## Apa yang Dipelajari

- **Tuple**: kumpulan data yang **tidak bisa diubah** (immutable)
- **Set**: kumpulan data yang **unik** dan **tidak terurut**
- Perbedaan list, tuple, dan set
- Kapan harus menggunakan tuple vs list vs set

---

## Penjelasan Kode

### 1. List (Sebagai Pembanding)

```python
data_list = [10,2,4,3,2]
print(data_list)
```

**Output:** `[10, 2, 4, 3, 2]`

List menggunakan **tanda kurung siku `[]`** dan:
- Bisa diubah (mutable)
- Bisa memiliki elemen duplikat
- Terurut (ordered)

---

### 2. Tuple

```python
data_tuples = (7,8,9,10)
print(data_tuples)
print(data_tuples[1])
```

| Komponen | Penjelasan |
|---|---|
| `(7,8,9,10)` | Tuple dibungkus **tanda kurung biasa `()`** |
| `data_tuples[1]` | Mengakses elemen dengan index (sama seperti list) |

**Output:**
```
(7, 8, 9, 10)
8
```

---

### Yang TIDAK Bisa Dilakukan pada Tuple

```python
# data_tuples[1] = "ucup"    # ERROR! Tidak bisa mengubah elemen
# data_tuples.append(1)       # ERROR! Tidak bisa menambah elemen
```

| Keterbatasan | Penjelasan |
|---|---|
| `data_tuples[1] = "x"` | **Error** — tuple tidak bisa diubah setelah dibuat |
| `data_tuples.append(1)` | **Error** — tuple tidak punya method `append` |

> **Ingat:** Tuple = **immutable** (tidak berubah). Setelah dibuat, isinya selamanya.

---

### 3. Set (Himpunan)

```python
data_sets = {10,4,3,2,4,7,6,5}
print(data_sets)
```

| Komponen | Penjelasan |
|---|---|
| `{10,4,3,2,4,7,6,5}` | Set dibungkus **tanda kurung kurawal `{}`** |
| `4` muncul dua kali | Tapi di output hanya muncul **satu kali** |

**Output:** `{2, 3, 4, 5, 6, 7, 10}`

Perhatikan:
- **Duplikat dihapus** otomatis (angka 4 yang duplikat hilang)
- **Tidak terurut** — urutan di output mungkin berbeda dari urutan input
- **Tidak bisa diakses dengan index**: `data_sets[0]` akan **ERROR**

---

## Perbandingan List, Tuple, dan Set

| Aspek | List `[]` | Tuple `()` | Set `{}` |
|---|---|---|---|
| Tanda kurung | `[ ]` | `( )` | `{ }` |
| Bisa diubah (mutable) | Ya | **Tidak** | Ya (tapi tidak di-index) |
| Duplikat | Diizinkan | Diizinkan | **Tidak diizinkan** |
| Terurut (ordered) | Ya | Ya | **Tidak** |
| Bisa di-index | Ya | Ya | **Tidak** |
| Method tersedia | append, remove, dll | Hanya count, index | add, remove, dll |

---

## Kapan Menggunakan Apa?

| Tipe | Kapan Digunakan | Contoh |
|---|---|---|
| **List** | Kumpulan data yang **berubah** | Daftar belanja, daftar tugas |
| **Tuple** | Kumpulan data yang **tetap** | Koordinat (x,y), warna RGB |
| **Set** | Kumpulan data **unik** tanpa duplikat | Daftar email unik, tag unik |

---

## Analogi

Bayangkan tiga jenis wadah:

- **List** 📝 → **Daftar belanja**: Bisa ditambah, dihapus, diubah kapan saja
- **Tuple** 📦 → **Paket yang sudah di-segel**: Setelah dikemas, isinya tidak bisa diubah
- **Set** 🎯 → **Kumpulan stiker unik**: Hanya satu stiker dari setiap jenis, tidak ada duplikat, dan urutannya tidak penting

---

## Tips

1. Gunakan **tuple** untuk data yang tidak boleh berubah (misal koordinat GPS, konfigurasi).
2. Gunakan **set** untuk **menghapus duplikat** dari sebuah list: `set(my_list)`.
3. Set sangat cepat untuk mengecek **keberadaan** elemen: `if x in my_set` jauh lebih cepat dari `if x in my_list`.
