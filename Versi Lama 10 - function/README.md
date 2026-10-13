# BAB 10 - Function (Fungsi)

## Apa yang Dipelajari

- Membuat fungsi dengan `def`
- Memanggil fungsi
- Fungsi dengan parameter (input)
- Memanggil fungsi di dalam fungsi lain
- Return value (nilai kembalian)

---

## Penjelasan Kode

### File: `function.py`

#### 1. Fungsi Sederhana Tanpa Parameter

```python
def suaraayam():
    print('kukuruyuk!!!!')
```

- `def` → mendefinisikan (membuat) fungsi baru.
- `suaraayam` → nama fungsi.
- `()` → tanda kurung kosong berarti fungsi ini **tidak menerima input**.
- `print('kukuruyuk!!!!')` → kode yang dijalankan saat fungsi dipanggil.

> **Panggil fungsi:** `suaraayam()` → mencetak `"kukuruyuk!!!!"`

---

#### 2. Fungsi yang Memanggil Fungsi Lain

```python
def hargaayam():
    suaraayam()
    print('harga ayam per 1 kg adalah Rp. 20.000')
```

- `suaraayam()` dipanggil di dalam `hargaayam()`.
- Saat `hargaayam()` dipanggil:
  1. Pertama, `"kukuruyuk!!!!"` dicetak (dari `suaraayam()`).
  2. Lalu `"harga ayam per 1 kg adalah Rp. 20.000"` dicetak.

> **Panggil:** `hargaayam()` → `"kukuruyuk!!!!"` lalu `"harga ayam per 1 kg adalah Rp. 20.000"`

---

#### 3. Fungsi dengan Parameter (Input)

```python
def hargatotalayam(kg):
    suaraayam()
    harga = 20000
    hargaTotal = kg * harga
    print('harga', kg, 'kg ayam adalah', hargaTotal)
```

- Parameter `kg` → nilai yang **dimasukkan** saat memanggil fungsi.
- `harga = 20000` → harga per kg (variabel lokal di dalam fungsi).
- `hargaTotal = kg * harga` → menghitung total harga.

---

#### 4. Memanggil Fungsi dengan Nilai Berbeda

```python
hargaayam()
hargatotalayam(2)
hargatotalayam(0.5)
hargatotalayam(1)
hargatotalayam(9)
```

| Pemanggilan | `kg` | `hargaTotal` | Output |
|-------------|------|--------------|--------|
| `hargatotalayam(2)` | 2 | 40000 | "harga 2 kg ayam adalah 40000" |
| `hargatotalayam(0.5)` | 0.5 | 10000 | "harga 0.5 kg ayam adalah 10000" |
| `hargatotalayam(1)` | 1 | 20000 | "harga 1 kg ayam adalah 20000" |
| `hargatotalayam(9)` | 9 | 180000 | "harga 9 kg ayam adalah 180000" |

---

## Komponen Fungsi

```
def nama_fungsi(parameter):
    │       │         │
    │       │         └── Input yang diterima fungsi
    │       └── Nama fungsi
    └── Kata kunci untuk mendefinisikan fungsi

    # isi fungsi (body)
    return nilai_kembalian  # opsional
```

---

## Alur Program

```
1. Program mendefinisikan fungsi-fungsi (tidak langsung dijalankan)
2. hargaayam() dipanggil
   └── suaraayam() dipanggil → "kukuruyuk!!!!"
   └── "harga ayam per 1 kg adalah Rp. 20.000"
3. hargatotalayam(2) dipanggil
   └── suaraayam() → "kukuruyuk!!!!"
   └── harga = 20000
   └── hargaTotal = 2 * 20000 = 40000
   └── "harga 2 kg ayam adalah 40000"
4. ...dst untuk pemanggilan lainnya
```

---

## Analogi

Bayangkan fungsi adalah **mesin vending**:

```
         ┌─────────────────────────┐
  Input →│  Mesin Vending (Fungsi) │→ Output
  (kg)   │  - Terima berat ayam    │  (harga total)
         │  - Kalikan dengan harga │
         │  - Tampilkan hasil      │
         └─────────────────────────┘
```

- `suaraayam()` = mesin berbunyi "kukuruyuk" setiap kali dinyalakan.
- `hargatotalayam(kg)` = kamu masukkan berat ayam → mesin menghitung total harga.

---

## Tips untuk Pemula

- Fungsi membuat kode **lebih rapi dan tidak berulang** (DRY: Don't Repeat Yourself).
- Fungsi bisa **dipanggil berkali-kali** dengan input berbeda.
- Fungsi bisa **memanggil fungsi lain**.
->Nama fungsi sebaiknya deskriptif: `hitung_harga()` lebih jelas dari `f()`.
- Gunakan **snake_case** untuk nama fungsi: `hitung_total()`, bukan `hitungTotal()`.
