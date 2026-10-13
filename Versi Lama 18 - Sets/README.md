# BAB 6 - Versi Lama 18: Sets (Himpunan)

## Apa yang Dipelajari

- Membuat set dengan `set()` dan `{ }`
- Menambah elemen dengan `add()`
- Memahami sifat **tidak ada duplikat** dan **tidak berurutan**
- Operasi himpunan: **union** (∪) dan **intersection** (∩)

---

## Penjelasan Kode

### File: `latihanSets.py`

#### 1. Membuat Set Kosong dan Menambah Elemen

```python
superhero = set()

superhero.add("wiro sableng")
superhero.add("gundala")
superhero.add("saras 008")
superhero.add(212)

print(superhero)
# Output: {'wiro sableng', 'gundala', 'saras 008', 212}
```

| Elemen | Penjelasan |
|--------|-----------|
| `set()` | Membuat **set kosong** (tidak bisa pakai `{}` karena itu untuk dictionary kosong) |
| `.add(x)` | Menambah elemen `x` ke dalam set |
| `212` | Set bisa menyimpan **tipe data campuran** (string + angka) |

> **Catatan:** Urutan elemen saat dicetak **tidak tentu** karena set tidak memiliki indeks.

#### 2. Membuat Set dengan Elemen Langsung

```python
ganjil = {1, 3, 5, 7, 9}
genap = {2, 4, 6, 8, 10}
prima = {2, 3, 5, 7}
```

#### 3. Union (∪) — Gabungan Dua Himpunan

```python
print(ganjil.union(genap))
# Output: {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
```

**Union** = menggabungkan **semua elemen** dari dua set (tanpa duplikat).

```
ganjil  = {1, 3, 5, 7, 9}
genap   = {2, 4, 6, 8, 10}
─────────────────────────────
union   = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
```

#### 4. Intersection (∩) — Elemen yang Sama

```python
print(ganjil.intersection(prima))
# Output: {3, 5, 7}
```

**Intersection** = hanya elemen yang **ada di kedua** set.

```
ganjil = {1, 3, 5, 7, 9}
prima  = {2, 3, 5, 7}
─────────────────────────
inter  = {3, 5, 7}     ← angka yang ada di KEDUA set
```

---

## Sifat Set

| Sifat | Penjelasan |
|-------|-----------|
| **Tidak berurutan** | Elemen tidak punya indeks, urutan saat cetak bisa berubah |
| **Tidak ada duplikat** | Jika menambah elemen yang sudah ada, Python mengabaikannya |
| **Tipe campuran** | Bisa menyimpan string, angka, boolean dalam satu set |
| **Mutable** | Bisa ditambah (`add`) dan dihapus elemennya |

---

## Operasi Set Lainnya (Tambahan)

| Operasi | Sintaks | Penjelasan |
|---------|---------|-----------|
| Union | `A.union(B)` atau `A \| B` | Semua elemen dari A dan B |
| Intersection | `A.intersection(B)` atau `A & B` | Elemen yang ada di A **dan** B |
| Difference | `A.difference(B)` atau `A - B` | Elemen di A yang **tidak ada** di B |
| Symmetric Diff | `A.symmetric_difference(B)` atau `A ^ B` | Elemen yang ada di A atau B, tapi **tidak di keduanya** |

---

## Analogi

Bayangkan kamu punya **dua kotak mainan**:

- **Kotak A (ganjil)**: ` action figure`, `mobil-mobilan`, `lego`, `puzzle`, `ular tangga`
- **Kotak B (prima)**: `mobil-mobilan`, `lego`, `puzzle`, `mainan air`

### Union (∪)
Kamu **menggabungkan semua** mainan dari kedua kotak ke dalam **satu kotak raksasa**. Duplikat dihilangkan (cukup satu mobil-mobilan).

### Intersection (∩)
Kamu hanya mengambil mainan yang **ada di kedua kotak**: `mobil-mobilan`, `lego`, `puzzle`.

### Difference (-)
Mainan yang ada di Kotak A tapi **tidak ada** di Kotak B: `action figure`, `ular tangga`.
