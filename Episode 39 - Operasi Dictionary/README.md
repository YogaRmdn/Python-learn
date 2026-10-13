# BAB 19 - Operasi Dictionary

## Apa yang Dipelajari

- Mengecek panjang dictionary dengan `len()`
- Mengecek keberadaan key dengan `in`
- Mengakses value dengan `get()`
- Mengupdate value dan menambah key baru
- Menghapus key-value dengan `del`
- Menggunakan `update()` untuk update massal

---

## Penjelasan Kode

### Data Awal

```python
data_dict = {
	"cup":"ucup surucup",
	"tong":"otong surotong",
	"dung":"dudung surudung"
}
```

---

### 1. Mengetahui Panjang Dictionary

```python
LENDICT = len(data_dict)
print(f"panjang dictionary: {LENDICT}")
```

`len()` mengembalikan **jumlah pasangan key-value**.

**Output:** `panjang dictionary: 3`

---

### 2. Mengecek Keberadaan Key

```python
KEY = "cup"
CHECKKEY = KEY in data_dict
print(f"apakah {KEY} ada di data_dict: {CHECKKEY}")
```

| Komponen | Penjelasan |
|---|---|
| `"cup" in data_dict` | Mengecek apakah key `"cup"` **ada** di dictionary |
| Mengembalikan | `True` jika ada, `False` jika tidak |

**Output:** `apakah cup ada di data_dict: True`

---

### 3. Mengakses Value dengan `get()`

```python
print(data_dict["cup"])
print(data_dict.get("cup"))
print(data_dict.get("kis","key tidak ditemukan"))
```

| Sintaks | Penjelasan |
|---|---|
| `data_dict["cup"]` | Akses langsung — **error** jika key tidak ada |
| `data_dict.get("cup")` | Akses dengan get — **None** jika key tidak ada |
| `data_dict.get("kis", "pesan")` | Get dengan **pesan default** jika key tidak ada |

**Output:**
```
ucup surucup
ucup surucup
key tidak ditemukan
```

> **Gunakan `get()`** untuk menghindari error `KeyError` saat key mungkin tidak ada.

---

### 4. Mengupdate Value

```python
data_dict["cup"] = "ucup si ganteng"
print(data_dict)
```

Jika key sudah ada, value-nya **diupdate** (diganti).

---

### 5. Menambah Key Baru

```python
data_dict["sep"] = "asep si kasyep"
print(data_dict)
```

Jika key **belum ada**, Python akan **membuat key baru** dengan value yang diberikan.

---

### 6. Mengupdate dengan `update()`

```python
data_dict.update({"cup":"ucup surucup"})
print(data_dict)
```

`update()` memperbarui value untuk key yang sudah ada.

---

### 7. Menambah Beberapa Key Sekaligus dengan `update()`

```python
data_dict.update({"faqih":"faqihza si kweren"})
print(data_dict)
```

Jika key belum ada, `update()` akan **menambahkannya**.

---

### 8. Menghapus Data dengan `del`

```python
del data_dict["faqih"]
print(data_dict)
```

`del` menghapus **key-value** berdasarkan key.

---

## Ringkasan Operasi Dictionary

| Operasi | Sintaks | Keterangan |
|---|---|---|
| Panjang | `len(dict)` | Jumlah pasangan key-value |
| Cek key ada | `key in dict` | Mengembalikan True/False |
| Baca value | `dict["key"]` | Error jika key tidak ada |
| Baca aman | `dict.get("key", default)` | Default jika key tidak ada |
| Update value | `dict["key"] = value` | Update atau tambah key |
| Update massal | `dict.update({...})` | Update beberapa key sekaligus |
| Hapus | `del dict["key"]` | Hapus key-value |

---

## Analogi

Bayangkan **buku alamat**:

- **`len()`**: "Berapa kontak yang saya punya?"
- **`"Budi" in`**: "Apakah Budi ada di buku alamat?"
- **`get("Budi", "Tidak ditemukan`)**: "Cari nomor Budi. Jika tidak ada, bilang 'tidak ditemukan'"
- **`dict["Budi"] = "08123"`**: "Simpan nomor Budi"
- **`update()`**: "Update beberapa kontak sekaligus"
- **`del dict["Budi"]`**: "Hapus kontak Budi dari daftar"

---

## Tips

1. **Gunakan `get()`** alih-alih `dict["key"]` untuk menghindari error.
2. `in` operator sangat berguna untuk **validasi input** sebelum mengakses value.
3. `update()` sangat efisien untuk **update massal** beberapa key-value sekaligus.
