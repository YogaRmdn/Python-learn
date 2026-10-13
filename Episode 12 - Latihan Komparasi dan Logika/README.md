# BAB 11 - Latihan Komparasi dan Logika

## Apa yang Dipelajari

- Menggabungkan operator komparasi dengan operator logika (`or` dan `and`)
- Membuat program pengecekan rentang angka
- Konsep **irisan** (intersection) dan **gabungan** (union) pada rentang angka

## Penjelasan Kode

```python
# episode latihan logika dan komparasi

# membuat gabungan area rentang dari angka

# ++++++3--------10+++++++

inputUser = float(input("masukan angka yang bernilai\nkurang dari 3 \natau \nlebih besar dari 10\n:"))
```

### Kasus 1: Angka di Luar Rentang (OR)

Program meminta user memasukkan angka, lalu mengecek apakah angka tersebut **di luar rentang 3-10** (kurang dari 3 ATAU lebih dari 10).

```python
# ++++++3-----------------
# Memeriksa angka kurang dari 3
isKurangDari = (inputUser < 3)
print("Kurang dari 3 =", isKurangDari)

# ---------------10++++++++
# Memeriksa angka lebih dari 10
isLebihDari = (inputUser > 10)
print("Lebih dari 10 =", isLebihDari)

# ++++++3--------10+++++++

isCorrect = isKurangDari or isLebihDari
print("angka yang anda masukan: ", isCorrect)
```

**Penjelasan:**
- `isKurangDari = (inputUser < 3)` → Menyimpan hasil pengecekan: apakah input kurang dari 3?
- `isLebihDari = (inputUser > 10)` → Menyimpan hasil pengecekan: apakah input lebih dari 10?
- `isCorrect = isKurangDari or isLebihDari` → Menggunakan `OR`: jika **salah satu** kondisi benar, maka `isCorrect = True`.

**Visualisasi Garis Bilang:**
```
++++++3--------10+++++++
  ↑ True    ↑ False   ↑ True
```
- Di bawah 3 → True
- Di antara 3-10 → False
- Di atas 10 → True

**Contoh:**
- Input `1` → `1 < 3` = True, `1 > 10` = False → `True or False` = **True** ✅
- Input `5` → `5 < 3` = False, `5 > 10` = False → `False or False` = **False** ❌
- Input `15` → `15 < 3` = False, `15 > 10` = True → `False or True` = **True** ✅

---

### Kasus 2: Angka di Dalam Rentang (AND)

```python
# -----3++++++++10--------
# kasus irisan
print("\n",10*"=","\n")
inputUser = float(input("masukan angka yang bernilai\nlebih dari 3 \ndan \nkurang dari 10\n:"))

# -----3++++++++++++++++++
# lebih dari 3
isLebihDari = inputUser > 3
print("Lebih dari 3 = ",isLebihDari)

# +++++++++++++++10-------
# kurang dari 10
isKurangDari = inputUser < 10
print("Kurang dari 10 = ",isKurangDari)

# -----3++++++++10--------
isCorrect = isKurangDari and isLebihDari
print("angka yang anda masukan: ", isCorrect)
```

**Penjelasan:**
- `isLebihDari = inputUser > 3` → Cek apakah input lebih dari 3.
- `isKurangDari = inputUser < 10` → Cek apakah input kurang dari 10.
- `isCorrect = isKurangDari and isLebihDari` → Menggunakan `AND`: **kedua** kondisi harus benar.

**Visualisasi Garis Bilang:**
```
-----3++++++++10--------
       ↑ True (overlap)
```
- Di bawah 3 → False
- Di antara 3-10 → **True** (irisan)
- Di atas 10 → False

**Contoh:**
- Input `5` → `5 > 3` = True, `5 < 10` = True → `True and True` = **True** ✅
- Input `1` → `1 > 3` = False, `1 < 10` = True → `False and True` = **False** ❌
- Input `15` → `15 > 3` = True, `15 < 10` = False → `True and False` = **False** ❌

## Tabel Ringkasan

| Kasus | Operator | Kondisi | Input 1 | Input 5 | Input 15 |
|-------|----------|---------|---------|---------|----------|
| Luar rentang | `OR` | `< 3 OR > 10` | True ✅ | False ❌ | True ✅ |
| Dalam rentang | `AND` | `> 3 AND < 10` | False ❌ | True ✅ | False ❌ |

## Analogi

Bayangkan kamu sedang **memilih jalur di taman hiburan**:
- **Kasus OR (OR = ATAU)**: Kamu boleh masuk jika tinggimu **kurang dari 150cm** ATAU **lebih dari 180cm**. Cukup salah satu syarat saja.
- **Kasus AND (AND = DAN)**: Kamu boleh masuk jika tinggimu **lebih dari 150cm** DAN **kurang dari 180cm**. Harus memenuhi kedua syarat.

Atau seperti **filter pencarian**:
- OR = "cari produk yang **murah** atau **bagus**" → dapat semua yang memenuhi salah satu.
- AND = "cari produk yang **murah** dan **bagus**" → hanya dapat yang memenuhi keduanya.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, latihan komparasi dan logika |
