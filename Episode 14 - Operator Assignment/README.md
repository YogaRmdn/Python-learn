# BAB 13 - Operator Assignment

## Apa yang Dipelajari

- Operator assignment shorthand (penyingkatan): `+=`, `-=`, `*=`, `/=`, `%=`, `//=`, `**=`
- Operator assignment bitwise: `|=`, `&=`, `^=`, `>>=`, `<<=`
- Cara kerja penyingkatan assignment

## Penjelasan Kode

```python
# operasi yang dapat dilakukan dengan penyingkatan
# operasi ditambah dengan assignment

a = 5 # adalah assignment
print("nilai a =",a)

a += 1 # artinya adalah a = a + 1
print("nilai a += 1, nilai a menjadi",a)

a -= 2 # artinya adalah a = a - 2
print("nilai a -= 2, nilai a menjadi",a)

a *= 5 # artinya adalah a = a * 5
print("nilai a *= 5, nilai a menjadi",a)

a /= 2 # artinya adalah a = a / 2
print("nilai a /= 2, nilai a menjadi",a)
```

### Penjelasan Operator Aritmatika Assignment

| Operator | Sama Dengan | Penjelasan | Contoh |
|----------|-------------|------------|--------|
| `a += 1` | `a = a + 1` | Tambah 1 | `5 + 1 = 6` |
| `a -= 2` | `a = a - 2` | Kurang 2 | `6 - 2 = 4` |
| `a *= 5` | `a = a * 5` | Kali 5 | `4 × 5 = 20` |
| `a /= 2` | `a = a / 2` | Bagi 2 | `20 / 2 = 10.0` |

---

### Modulus dan Floor Division Assignment

```python
b = 10
print("\nnilai b =",b)

b %= 3
print("nilai b %= 3, nilai b menjadi",b)

b = 10
print("\nnilai b =",b)

b //= 3
print("nilai b //= 3, nilai b menjadi",b)
```

| Operator | Sama Dengan | Contoh |
|----------|-------------|--------|
| `b %= 3` | `b = b % 3` | `10 % 3 = 1` |
| `b //= 3` | `b = b // 3` | `10 // 3 = 3` |

---

### Eksponen Assignment

```python
a = 5
print("\nnilai a =",a)
a **= 3
print("nilai a **= 3, nilai a menjadi",a)
```

- `a **= 3` sama dengan `a = a ** 3` = `5³` = `125`.

---

### Operator Bitwise Assignment

```python
# OR
c = True
c |= False     # c = True | False = True

# AND
c = True
c &= False     # c = True & False = False

c = True
c &= True      # c = True & True = True

# XOR
c = True
c ^= False     # c = True ^ False = True

c = True
c ^= True      # c = True ^ True = False

# Shift
d = 0b0100     # 4
d >>= 2        # 4 >> 2 = 1
d <<= 1        # 1 << 1 = 2
```

## Tabel Ringkasan Lengkap

| Operator | Nama | Sama Dengan | Contoh |
|----------|------|-------------|--------|
| `+=` | Tambah sama dengan | `a = a + b` | `a += 3` |
| `-=` | Kurang sama dengan | `a = a - b` | `a -= 3` |
| `*=` | Kali sama dengan | `a = a * b` | `a *= 3` |
| `/=` | Bagi sama dengan | `a = a / b` | `a /= 3` |
| `%=` | Modulus sama dengan | `a = a % b` | `a %= 3` |
| `//=` | Floor div sama dengan | `a = a // b` | `a //= 3` |
| `**=` | Pangkat sama dengan | `a = a ** b` | `a **= 3` |
| `\|=` | OR assignment | `a = a \| b` | `a \|= 3` |
| `&=` | AND assignment | `a = a & b` | `a &= 3` |
| `^=` | XOR assignment | `a = a ^ b` | `a ^= 3` |
| `>>=` | Shift right | `a = a >> b` | `a >>= 3` |
| `<<=` | Shift left | `a = a << b` | `a <<= 3` |

## Analogi

Bayangkan kamu punya **tabungan di bank**:
- `a = 5` = Saldo awal Rp5.
- `a += 1` = Kamu **menabung** Rp1 → saldo jadi Rp6.
- `a -= 2` = Kamu **menarik uang** Rp2 → saldo jadi Rp4.
- `a *= 5` = Uang kamu **dipinjam** dan dikembalikan 5x lipat → Rp20.
- `a /= 2` = Saldo **dibagi 2** (misal pindah ke rekening lain) → Rp10.

**Intinya:** Operator assignment hanya **cara menulis yang lebih singkat**. Daripada menulis `a = a + 1`, cukup tulis `a += 1`. Hasilnya sama persis!

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi operator assignment |
