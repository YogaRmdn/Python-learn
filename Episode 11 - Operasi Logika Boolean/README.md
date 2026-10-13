# BAB 10 - Operasi Logika Boolean

## Apa yang Dipelajari

- Operator logika: `NOT`, `OR`, `AND`, `XOR`
- Tabel kebenaran (truth table) untuk masing-masing operator
- Cara kerja operator logika dengan nilai `True` dan `False`

## Penjelasan Kode

```python
# operasi logika atau boolean

# not, or, and, xor

# NOT
print('====NOT====')
a = False
c = not a
print('data a =',a)
print('-------------- NOT')
print('data c =',c)

# OR (jika salah satu true, maka hasilnya adalah true)
print('====OR====')
a = False
b = False
c = a or b
print(a,'OR',b,'=',c)
a = False
b = True
c = a or b
print(a,'OR',b,' =',c)
a = True
b = False
c = a or b
print(a,' OR',b,'=',c)
a = True
b = True
c = a or b
print(a,' OR',b,' =',c)

# AND (jika dua buah nilai true, maka hasil true)
print('====AND====')
a = False
b = False
c = a and b
print(a,'AND',b,'=',c)
a = False
b = True
c = a and b
print(a,'AND',b,' =',c)
a = True
b = False
c = a and b
print(a,' AND',b,'=',c)
a = True
b = True
c = a and b
print(a,' AND',b,' =',c)

# XOR (akan true jika salah satu true, sisanya false)
print('====XOR====')
a = False
b = False
c = a ^ b
print(a,'XOR',b,'=',c)
a = False
b = True
c = a ^ b
print(a,'XOR',b,' =',c)
a = True
b = False
c = a ^ b
print(a,' XOR',b,'=',c)
a = True
b = True
c = a ^ b
print(a,' XOR',b,' =',c)
```

### Penjelasan per Operator

---

#### 1. NOT (Kebalikan)

```python
a = False
c = not a
print('data c =',c)  # True
```
- `not` membalik nilai boolean: `True` jadi `False`, `False` jadi `True`.
- Seperti ** mematikan saklar lampu**: jika lampu menyala (`True`), maka matikan (`False`), dan sebaliknya.

**Tabel Kebaran NOT:**
| Input | Output |
|-------|--------|
| `True` | `False` |
| `False` | `True` |

---

#### 2. OR (Atau)

```python
# Jika SALAH SATU saja True, hasilnya True
```

| a | b | a OR b |
|---|---|--------|
| False | False | **False** |
| False | True | **True** |
| True | False | **True** |
| True | True | **True** |

- `OR` hanya butuh **salah satu** nilai `True` untuk menghasilkan `True`.
- Semua harus `False` barulah hasilnya `False`.

---

#### 3. AND (Dan)

```python
# Jika DUA-DUANYA True, baru hasilnya True
```

| a | b | a AND b |
|---|---|--------|
| False | False | **False** |
| False | True | **False** |
| True | False | **False** |
| True | True | **True** |

- `AND` membutuhkan **kedua nilai** `True` untuk menghasilkan `True`.
- Jika salah satu saja `False`, hasilnya `False`.

---

#### 4. XOR (Exclusive OR / Atau Eksklusif)

```python
c = a ^ b  # XOR menggunakan operator ^
```

| a | b | a XOR b |
|---|---|--------|
| False | False | **False** |
| False | True | **True** |
| True | False | **True** |
| True | True | **False** |

- `XOR` menghasilkan `True` jika **hanya salah satu** yang `True`.
- Jika **keduanya sama** (`True` atau `False`), hasilnya `False`.
- Seperti **lampu lalu lintas**: hanya satu jalur yang boleh hijau pada satu waktu.

## Tabel Perbandingan Semua Operator

| a | b | NOT a | OR | AND | XOR |
|---|---|-------|----|-----|-----|
| F | F | T | **F** | **F** | **F** |
| F | T | T | **T** | **F** | **T** |
| T | F | F | **T** | **F** | **T** |
| T | T | F | **T** | **T** | **F** |

## Analogi

Bayangkan kamu sedang **memutuskan mau pergi ke mall**:

- **AND** = Kamu punya uang **DAN** ada waktu → baru pergi ke mall. Kalau salah satu tidak ada, tidak jadi.
- **OR** | Kamu punya uang **ATAU** ada teman mengajak → langsung pergi ke mall. Cukup salah satu saja.
- **NOT** = Jika seharusnya pergi (`True`), maka `not` membuatmu **tidak** pergi (`False`).
- **XOR** = Kamu pergi ke mall **ATAU** ke bioskop (tapi **tidak keduanya**). Kalau keduanya, bingung sendiri → `False`.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi operasi logika boolean |
