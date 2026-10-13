# BAB 8 - Latihan Program Perhitungan Sederhana

## Apa yang Dipelajari

- Membuat program konversi suhu (Celcius ke Reamur, Fahrenheit, Kelvin)
- Menggabungkan `input()`, casting `float()`, dan operasi aritmatika
- Membuat program yang interaktif (menerima input dari user)

## Penjelasan Kode

```python
# latihan konversi satuan temperature

# program konversi celcius ke satuan lain

print("\nPROGRAM KONVERSI TEMPERATUR\n")

celcius = float(input('Masukan suhu dalam celcius : '))
print("suhu adalah",celcius, "Celcius")

# reamur
reamur = (4/5) * celcius
print("suhu dalam reamur adalah ",reamur, "Reamur")

# fahrenheit
fahrenheit = ((9/5) * celcius) + 32
print("suhu dalam fahrenheit adalah ",fahrenheit, "Fahrenheit")

# Kelvin
kelvin = celcius + 273
print("suhu dalam kelvin adalah ",kelvin, "Kelvin")
```

### Penjelasan Baris per Baris

---

**Baris 5:**
```python
print("\nPROGRAM KONVERSI TEMPERATUR\n")
```
- `\n` adalah **escape character** untuk membuat **baris baru** (newline).
- Output akan ada baris kosong sebelum dan sesudah judul.

---

**Baris 7:**
```python
celcius = float(input('Masukan suhu dalam celcius : '))
```
- `input(...)` → menampilkan pesan dan menunggu user mengetik suhu.
- `float(...)` → mengubah input (string) menjadi angka desimal.
- Disimpan di variabel `celcius`.

---

**Baris 8:**
```python
print("suhu adalah",celcius, "Celcius")
```
- Menampilkan suhu yang baru dimasukkan user.

---

**Baris 10-11 (Konversi ke Reamur):**
```python
reamur = (4/5) * celcius
print("suhu dalam reamur adalah ",reamur, "Reamur")
```
- **Rumus Reamur:** `R = (4/5) × C`
- `4/5` dalam Python menghasilkan `0.8` (pembagian float).
- Jadi: `reamur = 0.8 × celcius`.

---

**Baris 13-14 (Konversi ke Fahrenheit):**
```python
fahrenheit = ((9/5) * celcius) + 32
print("suhu dalam fahrenheit adalah ",fahrenheit, "Fahrenheit")
```
- **Rumus Fahrenheit:** `F = (9/5 × C) + 32`
- `9/5 = 1.8`, jadi `fahrenheit = 1.8 × celcius + 32`.

---

**Baris 16-17 (Konversi ke Kelvin):**
```python
kelvin = celcius + 273
print("suhu dalam kelvin adalah ",kelvin, "Kelvin")
```
- **Rumus Kelvin:** `K = C + 273`
- Sederhana: tinggal tambah 273.

---

### Contoh Output

Jika user memasukkan `100`:

```
PROGRAM KONVERSI TEMPERATUR

Masukan suhu dalam celcius : 100
suhu adalah 100.0 Celcius
suhu dalam reamur adalah  80.0 Reamur
suhu dalam fahrenheit adalah  212.0 Fahrenheit
suhu dalam kelvin adalah  373.0 Kelvin
```

## Tabel Rumus Konversi Suhu

| Konversi | Rumus | Contoh (C = 100) |
|----------|-------|-------------------|
| Celcius → Reamur | R = (4/5) × C | (4/5) × 100 = 80 |
| Celcius → Fahrenheit | F = (9/5 × C) + 32 | (9/5 × 100) + 32 = 212 |
| Celcius → Kelvin | K = C + 273 | 100 + 273 = 373 |

## Analogi

Bayangkan ini seperti **mesin konversi otomatis di bandara**:
- Kamu memasukkan suhu dalam Celcius ke layar sentuh (`input()`).
- Mesin otomatis menghitung dan menampilkan suhu dalam berbagai satuan lainnya.
- Rumus konversi seperti **panduan buku saku** yang sudah di-program ke dalam mesin.
- Tinggal masukkan angka, hasilnya langsung keluar!

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, program konversi suhu Celcius |
