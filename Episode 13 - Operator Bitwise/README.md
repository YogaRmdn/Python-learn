# BAB 12 - Operator Bitwise

## Apa yang Dipelajari

- Operator bitwise: OR (`|`), AND (`&`), XOR (`^`), NOT (`~`)
- Shift operator: Shift Right (`>>`), Shift Left (`<<`)
- Konversi angka ke biner menggunakan `format(value, '08b')`
- Cara kerja operasi bitwise pada level bit

## Penjelasan Kode

```python
# episode operator bitwise, operasi biner, binary

a = 9
b = 5
```

Dua variabel: `a = 9` (biner: `00001001`) dan `b = 5` (biner: `00000101`).

---

### 1. Bitwise OR (`|`)

```python
c = a | b
print('\n=========OR=========')
print('nilai :',a,' , binary :',format(a,'08b'))
print('nilai :',b,' , binary :',format(b,'08b'))
print('----------------------------- (|)')
print('nilai :',c,' , binary :',format(c,'08b'))
```

**Cara kerja:**
```
  00001001  (9)
| 00000101  (5)
----------
  00001101  (13)
```
- OR: Jika **salah satu atau kedua** bit bernilai `1`, hasilnya `1`.
- `9 | 5 = 13`

---

### 2. Bitwise AND (`&`)

```python
c = a & b
print('\n=========AND========')
print('nilai :',a,' , binary :',format(a,'08b'))
print('nilai :',b,' , binary :',format(b,'08b'))
print('----------------------------- (&)')
print('nilai :',c,' , binary :',format(c,'08b'))
```

**Cara kerja:**
```
  00001001  (9)
& 00000101  (5)
----------
  00000001  (1)
```
- AND: Hanya `1` jika **kedua** bit bernilai `1`.
- `9 & 5 = 1`

---

### 3. Bitwise XOR (`^`)

```python
c = a ^ b
print('\n=========XOR========')
print('nilai :',a,' , binary :',format(a,'08b'))
print('nilai :',b,' , binary :',format(b,'08b'))
print('----------------------------- (^)')
print('nilai :',c,' , binary :',format(c,'08b'))
```

**Cara kerja:**
```
  00001001  (9)
^ 00000101  (5)
----------
  00001100  (12)
```
- XOR: `1` hanya jika **salah satu** bit bernilai `1` (bukan keduanya).
- `9 ^ 5 = 12`

---

### 4. Bitwise NOT (`~`)

```python
c = ~a
print('\n=========NOT========')
print('nilai :',a,' , binary :',format(a,'08b'))
print('----------------------------- (~)')
print('nilai :',c,' , binary :',format(c,'08b'))
```

**Cara kerja:**
- NOT membalik semua bit: `1` jadi `0`, `0` jadi `1`.
- `~9 = -10` (menggunakan rumus: `~x = -(x+1)`)

```python
d = 0b0000010001
e = 0b1111111111
print('nilai :',e^d,' , binary :',format(e^d,'08b'))
```
- Menampilkan XOR dari dua bilangan biner.

---

### 5. Shift Right (`>>`)

```python
c = a >> 2
print('\n=========>>=========')
print('nilai :',a,' , binary :',format(a,'08b'))
print('----------------------------- (>>)')
print('nilai :',c,' , binary :',format(c,'08b'))
```

**Cara kerja:**
```
  00001001  (9) → geser 2 bit ke kanan
→ 00000010  (2)
```
- Setiap shift ke kanan = **membagi 2** (dibulatkan ke bawah).
- `9 >> 2` = `9 // (2²)` = `9 // 4` = `2`

---

### 6. Shift Left (`<<`)

```python
c = a << 2
print('\n=========<<=========')
print('nilai :',a,' , binary :',format(a,'08b'))
print('----------------------------- (<<)')
print('nilai :',c,' , binary :',format(c,'08b'))
```

**Cara kerja:**
```
  00001001  (9) → geser 2 bit ke kiri
→ 00100100  (36)
```
- Setiap shift ke kiri = **mengalikan 2**.
- `9 << 2` = `9 × (2²)` = `9 × 4` = `36`

## Tabel Ringkasan

| Operator | Nama | Contoh | Hasil | Biner |
|----------|------|--------|-------|-------|
| `\|` | OR | `9 \| 5` | `13` | `00001101` |
| `&` | AND | `9 & 5` | `1` | `00000001` |
| `^` | XOR | `9 ^ 5` | `12` | `00001100` |
| `~` | NOT | `~9` | `-10` | — |
| `>>` | Shift Right | `9 >> 2` | `2` | `00000010` |
| `<<` | Shift Left | `9 << 2` | `36` | `00100100` |

## Analogi

Bayangkan kamu punya **panel lampu neon** dengan 8 lampu (8 bit):

- **OR (`|`)** = "Nyalakan lampu yang menyala di **panel A** ATAU **panel B**". Jika salah satu menyala, nyalakan.
- **AND (`&`)** = "Nyalakan lampu yang menyala di **panel A** DAN **panel B**". Harus menyala di keduanya.
- **XOR (`^`)** = "Nyalakan lampu yang menyala di **satu panel saja**". Kalau keduanya menyala atau keduanya mati, jangan nyalakan.
- **NOT (`~`)** = "Balik semua kondisi lampu: yang menyala jadi mati, yang mati jadi menyala".
- **Shift Right (`>>`)** = "Geser semua lampu ke **kanan**". Lampu yang keluar panel hilang.
- **Shift Left (`<<`)** = "Geser semua lampu ke **kiri**". Lampu yang keluar panel hilang.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi operator bitwise |
