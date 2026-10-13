# BAB 9 - Operasi Komparasi

## Apa yang Dipelajari

- 6 operator perbandingan: `>`, `<`, `>=`, `<=`, `==`, `!=`
- Operator `is` dan `is not` untuk perbandingan identitas objek
- Semua hasil operasi komparasi adalah **boolean** (`True` atau `False`)
- Konsep `id()` dan `hex(id())` untuk melihat identitas objek di memori

## Penjelasan Kode

```python
# operasi komparasi

# setiap hasil dari operasi komparasi adalah boolean

# >,<,>=,<=,==,!=,is,is not

a = 4
b = 2
```

Dua variabel dibuat: `a = 4` dan `b = 2`. Semua operasi komparasi akan menggunakan dua nilai ini.

---

### 1. Lebih Besar Dari (`>`)

```python
print('========== lebih besar dari (>)')
hasil = a > 3
print(a,'>',3,'=',hasil)   # 4 > 3 = True
hasil = b > 3
print(b,'>',3,'=',hasil)   # 2 > 3 = False
hasil = b > 2
print(b,'>',2,'=',hasil)   # 2 > 2 = False
```
- `a > 3` → `4 > 3` → **True** (4 lebih besar dari 3)
- `b > 3` → `2 > 3` → **False** (2 tidak lebih besar dari 3)
- `b > 2` → `2 > 2` → **False** (2 sama dengan 2, bukan lebih besar)

---

### 2. Kurang Dari (`<`)

```python
print('========== kurang dari (<)')
hasil = a < 3
print(a,'<',3,'=',hasil)   # 4 < 3 = False
hasil = b < 3
print(b,'<',3,'=',hasil)   # 2 < 3 = True
hasil = b < 2
print(b,'<',2,'=',hasil)   # 2 < 2 = False
```
- `b < 3` → `2 < 3` → **True** (2 lebih kecil dari 3)
- `b < 2` → `2 < 2` → **False** (2 sama dengan 2, bukan lebih kecil)

---

### 3. Lebih Dari Sama Dengan (`>=`)

```python
print('========== lebih dari sama dengan(>=)')
hasil = a >= 3
print(a,'>=',3,'=',hasil)   # 4 >= 3 = True
hasil = b >= 3
print(b,'>=',3,'=',hasil)   # 2 >= 3 = False
hasil = b >= 2
print(b,'>=',2,'=',hasil)   # 2 >= 2 = True
```
- `b >= 2` → `2 >= 2` → **True** (2 sama dengan 2, jadi "lebih dari sama dengan" terpenuhi)

---

### 4. Kurang Dari Sama Dengan (`<=`)

```python
print('======== kurang dari sama dengan(<=)')
hasil = a <= 3
print(a,'<=',3,'=',hasil)   # 4 <= 3 = False
hasil = b <= 3
print(b,'<=',3,'=',hasil)   # 2 <= 3 = True
hasil = b <= 2
print(b,'<=',2,'=',hasil)   # 2 <= 2 = True
```

---

### 5. Sama Dengan (`==`)

```python
print('======== sama dengan(==)')
hasil = a == 4
print(a,'==',4,'=',hasil)   # 4 == 4 = True
hasil = b == 4
print(b,'==',4,'=',hasil)   # 2 == 4 = False
```
- `==` mengecek **apakah dua nilai sama**.
- Berbeda dari `=` yang adalah **assignment** (penugasan).

---

### 6. Tidak Sama Dengan (`!=`)

```python
print('======== sama dengan(!=)')
hasil = a != 4
print(a,'!=',4,'=',hasil)   # 4 != 4 = False
hasil = b != 4
print(b,'!=',4,'=',hasil)   # 2 != 4 = True
```
- `!=` mengecek **apakah dua nilai berbeda**.

---

### 7. Operator `is` (Object Identity)

```python
print('======== object identity(is)')
x = 5
y = 5
print('nilai x =',x,',id = ',hex(id(x)))
print('nilai y =',y,',id = ',hex(id(y)))
hasil = x is y
print('x is y =',hasil)     # True (Python meng-cache angka kecil)
```
- `is` mengecek **apakah dua variabel menunjuk objek yang SAMA di memori**.
- `id()` mengembalikan **alamat memori** objek.
- `hex(id(x))` menampilkan alamat memori dalam format hexadecimal.
- Untuk angka kecil (biasanya -5 sampai 256), Python **meng-cache** (menyimpan sekali), jadi `x is y` bisa `True`.

```python
x = 5
y = 6
print('nilai x =',x,',id = ',hex(id(x)))
print('nilai y =',y,',id = ',hex(id(y)))
hasil = x is y
print('x is y =',hasil)     # False (berbeda nilai, berbeda objek)
```

---

### 8. Operator `is not`

```python
print('======== object identity(is not)')
x = 5
y = 5
hasil = x is not y
print('x is y =',hasil)     # False (mereka IS same object)

x = 5
y = 6
hasil = x is not y
print('x is y =',hasil)     # True (mereka IS NOT same object)
```
- `is not` adalah **kebalikan dari `is`**.

## Tabel Ringkasan

| Operator | Nama | Contoh | Hasil | Penjelasan |
|----------|------|--------|-------|------------|
| `>` | Lebih besar dari | `4 > 3` | `True` | Apakah kiri lebih besar? |
| `<` | Kurang dari | `2 < 3` | `True` | Apakah kiri lebih kecil? |
| `>=` | Lebih dari sama dengan | `2 >= 2` | `True` | Lebih besar ATAU sama |
| `<=` | Kurang dari sama dengan | `2 <= 3` | `True` | Lebih kecil ATAU sama |
| `==` | Sama dengan | `4 == 4` | `True` | Apakah nilainya sama? |
| `!=` | Tidak sama dengan | `2 != 4` | `True` | Apakah nilainya beda? |
| `is` | Identitas objek | `x is y` | `True/False` | Apakah objek yang SAMA? |
| `is not` | Bukan identitas | `x is not y` | `True/False` | Apakah objek BERBEDA? |

## Analogi

Bayangkan kamu sedang **membandingkan benda**:
- `>` = Apakah buku A **lebih tebal** dari buku B?
- `<` = Apakah buku A **lebih tipis** dari buku B?
- `>=` = Apakah buku A **lebih tebal atau sama tebalnya** dengan buku B?
- `<=` = Apakah buku A **lebih tipis atau sama tipisnya** dengan buku B?
- `==` = Apakah buku A dan buku B **judulnya sama**?
- `!=` = Apakah buku A dan buku B **judulnya beda**?
- `is` = Apakah buku A dan buku B **adalah buku yang persis sama** (bukan hanya judulnya sama, tapi fisiknya buku yang sama)?
- `is not` = Apakah buku A dan buku B **bukan buku yang sama**?

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi operasi komparasi Python |
