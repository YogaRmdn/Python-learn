# BAB 7 - For Else, Range, Break

## Apa yang Dipelajari

- Fungsi `range()` untuk menghasilkan deret angka
- Statement `break` untuk menghentikan loop
- Clausa `else` pada `for` loop (else setelah loop)
- Kombinasi for + range + break + else

---

## Penjelasan Kode

### File: `for loop, else, break, range.py`

#### 1. Membuat Variabel Pencarian

```python
number = 50;
```

- `number` adalah angka yang ingin dicari.
- Tanda titik koma `;` di akhir baris **tidak diperlukan** di Python (tidak menimbulkan error, tapi bukan konvensi Python).

---

#### 2. For Loop dengan Range

```python
for i in range(0, 40):
    print(i)
```

- `range(0, 40)` menghasilkan deret angka dari `0` sampai `39` (40 **tidak termasuk**).
- Loop akan mencetak angka 0, 1, 2, 3, ..., 39.

---

#### 3. Break untuk Mencari Angka

```python
    if i is number:
        print('angka ditemukan', i)
        break
```

- Di dalam loop, kita mengecek: apakah `i` sama dengan `number` (50)?
- Karena `range(0, 40)` hanya sampai 39, angka 50 **tidak akan pernah ditemukan**.
- `break` akan **menghentikan loop** segera jika kondisi terpenuhi.
- Karena tidak pernah terpenuhi, loop berjalan sampai selesai.

---

#### 4. Else pada For Loop

```python
else:
    print('angka tidak ditemukan')
```

- `else` di akhir `for` loop akan dijalankan **jika loop selesai tanpa `break`**.
- Jika loop dihentikan dengan `break`, `else` **tidak dijalankan**.

**Logika:**
- Loop selesai (tidak ada break) → `else` jalan → "angka tidak ditemukan"
- Loop dihentikan dengan `break` → `else` tidak jalan

---

#### 5. Print di Luar Loop

```python
print("space di luar for")
```

- Baris ini dijalankan **setelah** seluruh blok for-else selesai.

---

## Ringkasan `range()`

| Kode | Hasil | Penjelasan |
|------|-------|------------|
| `range(5)` | `0, 1, 2, 3, 4` | Dari 0 sampai 4 |
| `range(0, 10)` | `0, 1, ..., 9` | Dari 0 sampai 9 |
| `range(1, 6)` | `1, 2, 3, 4, 5` | Dari 1 sampai 5 |
| `range(0, 20, 2)` | `0, 2, 4, ..., 18` | Dari 0, loncat 2 |

> **Catatan:** Parameter ketiga `range(start, stop, step)` adalah langkah (step).

---

## Alur Program

```
number = 50
       │
       ▼
for i in range(0, 40) ──→ i = 0, 1, 2, ..., 39
       │
       ├── i == 50? ──→ TIDAK (selalu)
       │
       ▼ (loop selesai tanpa break)
else:
  "angka tidak ditemukan"
       │
       ▼
"space di luar for"
```

---

## Analogi

Bayangkan kamu **mencari kunci** di laci nomor 0 sampai 39:
- Kamu buka satu per satu laci.
- Di laci manapun, kamu tidak menemukan kunci (karena kunci di laci 50, yang tidak ada).
- Setelah semua laci dibuka, kamu berkata: "Kunci tidak ditemukan." (ini peran `else`)
- Jika ternyata kunci ada di laci ke-25, kamu langsung berhenti dan bilang: "Ketemu!" (ini peran `break`)

---

## Tips untuk Pemula

- `range(a, b)` menghasilkan angka dari `a` sampai `b - 1`.
- `else` pada `for` berguna untuk menangani kasus "tidak ditemukan" tanpa flag tambahan.
- Gunakan `break` untuk menghentikan loop lebih awal ketika sudah menemukan yang dicari.
