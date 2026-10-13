# BAB 7 - Versi Lama 19: Dictionary

## Apa yang Dipelajari

- Membuat dictionary dengan `{ }`
- Konsep **key-value** (pasangan kunci-nilai)
- Mengakses nilai dictionary dengan **key**
- Membuat **dictionary bersarang** (dictionary di dalam dictionary)
- Mengakses dictionary bersarang

---

## Penjelasan Kode

### File: `latihanDictionary.py`

#### 1. Membuat Dictionary

```python
member1 = {
    "ID": 101,
    "Nama": "Faqihza Mukhlish",
    "Pekerjaan": "Mahasiswa",
    "Status member": "Gold"
}

member2 = {
    "ID": 102,
    "Nama": "Ujang Pintu",
    "Pekerjaan": "reparasi pintu",
    "Status member": "Berlian"
}
```

| Elemen | Penjelasan |
|--------|-----------|
| `{ }` | Tanda untuk membuat dictionary |
| `"ID": 101` | **Key** = `"ID"`, **Value** = `101` (pasangan key-value) |
| **Key** | Harus berupa **string** (atau tipe immutable lain). Harus **unik**. |
| **Value** | Bisa berupa tipe data apa saja (string, angka, list, dll.) |

#### 2. Dictionary Bersarang (Nested Dictionary)

```python
memberlist = {101: member1, 102: member2}
```

Ini adalah dictionary yang **valuenya berupa dictionary lain**:

```
memberlist
├── 101 → member1 {"ID": 101, "Nama": "Faqihza Mukhlish", ...}
└── 102 → member2 {"ID": 102, "Nama": "Ujang Pintu", ...}
```

#### 3. Mengakses Dictionary Bersarang

```python
print(memberlist[101])
# Output: {'ID': 101, 'Nama': 'Faqihza Mukhlish', 'Pekerjaan': 'Mahasiswa', 'Status member': 'Gold'}
```

| Sintaks | Penjelasan |
|---------|-----------|
| `memberlist[101]` | Mengambil **value** dari key `101` → yaitu dictionary `member1` |
| `memberlist[101]["Nama"]` | Jika ingin mengambil nama → `"Faqihza Mukhlish"` |

---

## Operasi Dictionary Penting (Tambahan)

| Operasi | Sintaks | Penjelasan |
|---------|---------|-----------|
| Ambil value | `d["key"]` | Mengambil nilai berdasarkan key |
| Tambah/update | `d["key"] = value` | Menambah atau mengubah value |
| Hapus | `del d["key"]` | Menghapus pasangan key-value |
| Cek key | `"key" in d` | Mengecek apakah key ada di dictionary |
| Semua key | `d.keys()` | Mendapatkan semua key |
| Semua value | `d.values()` | Mendapatkan semua value |
| Semua pasangan | `d.items()` | Mendapatkan semua pasangan (key, value) |

---

## Analogi

### Dictionary = **Kamus / Buku Telepon**

Bayangkan **buku telepon**:
- **Key** = Nama kontak (misalnya "Budi")
- **Value** = Nomor telepon (misalnya "08123456789")

Kamu **mencari berdasarkan nama** (key) untuk mendapatkan **nomor telepon** (value). Kamu tidak perlu tahu urutan halaman, cukup sebut namanya.

### Dictionary Bersarang = **Lemari Arsip**

Bayangkan **lemari arsi** dengan laci bernomor:
- Laci `101` berisi **map asli** milik karyawan Faqihza (nama, pekerjaan, status).
- Laci `102` berisi **map asli** milik karyawan Ujang.

Ketika kamu membuka laci `101`, di dalamnya ada **berbagai informasi** tentang karyawan tersebut — seperti "dokumen di dalam dokumen" (dictionary di dalam dictionary).
