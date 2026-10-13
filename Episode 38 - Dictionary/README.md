# BAB 18 - Dictionary

## Apa yang Dipelajari

- Apa itu **dictionary** (kamus) dalam Python
- Membuat dictionary dengan pasangan **key-value**
- Mengakses value berdasarkan **key**
- Menyimpan berbagai tipe data dalam dictionary
- Perbedaan list dan dictionary

---

## Penjelasan Kode

### List sebagai Pembanding

```python
data_list = ['ucup','otong','dudung']
print(data_list[0])
```

List menggunakan **index numerik** (0, 1, 2, ...) untuk mengakses elemen.

---

### Membuat Dictionary

```python
data_dict = {
	'key':'value',
	'cp':'ucup',
	'tg':'otong',
	'dg':'dudung',
	'nmbr':100,
	'list':data_list,
}
```

| Komponen | Penjelasan |
|---|---|
| `{ }` | Tanda kurung kurawal untuk dictionary |
| `'cp':'ucup'` | **Pasangan key-value**: `'cp'` adalah key, `'ucup'` adalah value |
| `'nmbr':100` | Value bisa berupa **angka** |
| `'list':data_list` | Value bisa berupa **list** atau tipe data lain |

---

### Mengakses Value dengan Key

```python
print(data_dict['tg'])
print(data_dict['nmbr'])
print(data_dict['list'])
```

| Sintaks | Penjelasan |
|---|---|
| `data_dict['tg']` | Mengambil value dari key `'tg'` |
| `data_dict['nmbr']` | Mengambil value dari key `'nmbr'` |
| `data_dict['list']` | Mengambil value dari key `'list'` (berisi list) |

**Output:**
```
otong
100
['ucup', 'otong', 'dudung']
```

---

## Perbedaan List vs Dictionary

| Aspek | List | Dictionary |
|---|---|---|
| Akses dengan | **Index numerik** (0, 1, 2) | **Key** (teks/label) |
| Contoh | `data[0]` | `data['nama']` |
| Urutan | Terurut | **Tidak terurut** (sebelum Python 3.7) |
| Cocok untuk | Data berurutan | Data berlabel/bernama |

---

## Struktur Dictionary

```
data_dict = {
    'key1' : 'value1',
    'key2' : 'value2',
    'key3' : 'value3',
}

     ↓
   Key  →  Value
   'cp' →  'ucup'
   'tg' →  'otong'
   'dg' →  'dudung'
```

---

## Analogi

Bayangkan **kamus Bahasa Indonesia**:

- **Key** = kata yang dicari (misal: "apel")
- **Value** = arti dari kata tersebut (misal: "buah yang bulat dan merah")

Untuk mencari arti, kamu **tidak melihat halaman ke-1, ke-2**, dst. Kamu langsung mencari berdasarkan **nama kata** — seperti dictionary Python!

---

## Tips

1. Key harus berupa **tipe data yang tidak berubah** (string, angka, tuple). Tidak boleh list.
2. Value bisa berupa **tipe data apa saja** (string, angka, list, bahkan dictionary lain).
3. Dictionary sangat berguna untuk data yang punya **label/nama**, seperti data siswa `{ nama: "Budi", umur: 15 }`.
4. Jika key tidak ditemukan, akan menghasilkan **error** `KeyError`. Gunakan `.get()` untuk menghindarinya.
