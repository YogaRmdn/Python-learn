# BAB 12 - Return Value (Nilai Kembalian)

## Apa yang Dipelajari

- Menggunakan `return` untuk mengembalikan nilai dari fungsi
- Menyimpan hasil return ke variabel
- Fungsi dengan multiple arguments dan return
- Menggabungkan (nesting) pemanggilan fungsi dengan return

---

## Penjelasan Kode

### File: `part 12- return value.py`

#### 1. Fungsi dengan Return Value

```python
def kuadrat(argumen):
    total = argumen ** 2
    print('nilai kuadrat dari', argumen, 'adalah:', total)
    return total
```

**Cara kerja:**
1. `argumen ** 2` → mengkuadratkan input (misal: `4² = 16`).
2. `print(...)` → menampilkan hasil ke layar.
3. `return total` → **mengembalikan** nilai `total` ke pemanggil fungsi.

> **Perbedaan `print` vs `return`:**
> - `print` hanya **menampilkan** ke layar, tidak bisa disimpan.
> - `return` **mengembalikan** nilai yang bisa disimpan di variabel.

---

**Memanggil fungsi dan menyimpan hasilnya:**

```python
a = kuadrat(4)
print(a)
```

1. `kuadrat(4)` dipanggil:
   - `total = 4 ** 2 = 16`
   - `"nilai kuadrat dari 4 adalah: 16"` dicetak
   - `return 16` → nilai 16 dikembalikan
2. `a = 16` → hasil return disimpan ke variabel `a`.
3. `print(a)` → mencetak `16`.

---

#### 2. Pemisah Visual

```python
print('+' * 100)
```

- Mencetak 100 tanda `+` sebagai garis pemisah.

---

#### 3. Fungsi Tambah dengan Multiple Arguments

```python
def tambah(argumen1, argumen2):
    total = argumen1 + argumen2
    print(argumen1, '+', argumen2, '=', total)
    return total
```

- Menerima **dua input**, menjumlahkan, menampilkan, dan mengembalikan hasil.

---

#### 4. Fungsi Kali

```python
def kali(argumen1, argumen2):
    total = argumen1 * argumen2
    print(argumen1, 'x', argumen2, '=', total)
    return total
```

- Menerima **dua input**, mengalikan, menampilkan, dan mengembalikan hasil.

---

#### 5. Nesting Pemanggilan Fungsi (Gabungan Return)

```python
b = kali(3, tambah(3, 4))
print(b)
```

**Cara kerja (dari dalam ke luar):**

```
b = kali(3, tambah(3, 4))
              │
              ├── 1. tambah(3, 4) dijalankan DULU
              │     ├── total = 3 + 4 = 7
              │     ├── "3 + 4 = 7" dicetak
              │     └── return 7
              │
              ├── 2. Maka menjadi: kali(3, 7)
              │     ├── total = 3 * 7 = 21
              │     ├── "3 x 7 = 21" dicetak
              │     └── return 21
              │
              └── 3. b = 21
```

| Langkah | Fungsi | Input | Output Layar | Return |
|---------|--------|-------|--------------|--------|
| 1 | `tambah(3, 4)` | 3, 4 | `3 + 4 = 7` | `7` |
| 2 | `kali(3, 7)` | 3, 7 | `3 x 7 = 21` | `21` |
| 3 | `print(b)` | - | `21` | - |

---

## Ringkasan

| Konsep | Penjelasan |
|--------|------------|
| `return` | Mengembalikan nilai dari fungsi |
| `print` vs `return` | `print` menampilkan, `return` mengembalikan data |
| Multiple arguments | Fungsi bisa menerima lebih dari satu input |
| Nesting | Hasil return bisa langsung dijadikan input fungsi lain |

---

## Analogi

Bayangkan fungsi adalah **mesin**:

```
┌──────────────┐
│  Mesin Tambah │──→ Input: 3, 4 ──→ Output: 7
└──────────────┘

┌──────────────┐
│  Mesin Kali   │──→ Input: 3, 7 ──→ Output: 21
└──────────────┘
```

- **Return** seperti **tinta printer**: hasil cetakan bisa kamu ambil dan pakai.
- **Print** seperti **tayangan di TV**: kamu bisa melihat, tapi tidak bisa menyimpan hasilnya.
- **Nesting**: Kamu masukkan hasil dari Mesin Tambah ke Mesin Kali, lalu hasil akhirnya kamu simpan.

---

## Tips untuk Pemula

- Selalu gunakan `return` jika kamu ingin **menggunakan hasil** fungsi nanti.
- Jangan lupa `return` — jika tidak ada, fungsi secara default mengembalikan `None`.
- Fungsi bisa mengembalikan **apa saja**: angka, teks, list, bahkan fungsi lain.
- Saat nesting, Python mengevaluasi dari **dalam ke luar** (seperti matematika: kurung dulu).
