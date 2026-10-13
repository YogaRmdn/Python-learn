# BAB 4 - Versi Lama 16: Stacks dan Queues

## Apa yang Dipelajari

- Konsep **Stack** (Tumpukan) — prinsip **LIFO** (Last In, First Out)
- Konsep **Queue** (Antrian) — prinsip **FIFO** (First In, First Out)
- Implementasi Stack dengan **list** (`append()` dan `pop()`)
- Implementasi Queue dengan **`collections.deque`** (`append()` dan `popleft()`)

---

## Penjelasan Kode

### File 1: `Tumpukan.py` — Implementasi Stack (LIFO)

```python
tumpukan = [1, 2, 3, 4, 5, 6]
print('data sekarang:', tumpukan)
# Output: data sekarang: [1, 2, 3, 4, 5, 6]
```

**Stack** = tumpukan. Elemen yang **paling baru masuk** adalah yang **pertama keluar**.

#### Push (Menambah Data)

```python
tumpukan.append(7)
print('data masuk:', 7)
print('data sekarang:', tumpukan)
# Output: data sekarang: [1, 2, 3, 4, 5, 6, 7]

tumpukan.append(8)
print('data masuk:', 8)
print('data sekarang:', tumpukan)
# Output: data sekarang: [1, 2, 3, 4, 5, 6, 7, 8]
```

#### Pop (Mengambil Data)

```python
out = tumpukan.pop()
print('data keluar:', out)
# Output: data keluar: 8  ← yang terakhir masuk, pertama keluar!
print('data sekarang:', tumpukan)
# Output: data sekarang: [1, 2, 3, 4, 5, 6, 7]
```

---

### File 2: `antrian.py` — Implementasi Queue (FIFO)

```python
from collections import deque

antrian = deque([1, 2, 3, 4, 5])
print('data sekarang:', antrian)
```

**Queue** = antrian. Elemen yang **paling awal masuk** adalah yang **pertama keluar**.

#### Push (Menambah Data di Akhir)

```python
antrian.append(6)
print('data masuk:', 6)
print('data sekarang:', antrian)
# Output: data sekarang: deque([1, 2, 3, 4, 5, 6])

antrian.append(7)
print('data masuk:', 7)
print('data sekarang:', antrian)
# Output: data sekarang: deque([1, 2, 3, 4, 5, 6, 7])
```

#### Pop (Mengambil Data dari Depan)

```python
out = antrian.popleft()
print('data keluar:', out)
# Output: data keluar: 1  ← yang paling awal masuk, pertama keluar!
print('data sekarang:', antrian)
# Output: data sekarang: deque([2, 3, 4, 5, 6, 7])

out = antrian.popleft()
print('data keluar:', out)
# Output: data keluar: 2

out = antrian.popleft()
print('data keluar:', out)
# Output: data keluar: 3
```

#### Tambah Lagi di Akhir Antrian

```python
antrian.append(8)
print('data masuk:', 8)
print('data sekarang:', antrian)
# Output: data sekarang: deque([4, 5, 6, 7, 8])
```

---

## Perbandingan Stack vs Queue

| Aspek | Stack (Tumpukan) | Queue (Antrian) |
|-------|------------------|-----------------|
| **Prinsip** | LIFO (Last In, First Out) | FIFO (First In, First Out) |
| **Tambah** | `append()` (di akhir) | `append()` (di akhir) |
| **Ambil** | `pop()` (dari akhir) | `popleft()` (dari depan) |
| **Struktur** | List biasa | `collections.deque` |
| **Contoh** | Tumpukan piring | Antrian di bank |

> **Mengapa Queue pakai `deque`?**
> Karena `list.pop()` hanya bisa mengambil dari **akhir** (cepat). Untuk mengambil dari **depan** list butuh waktu lama (karena semua elemen bergeser). `deque` dirancang khusus agar operasi di **kedua ujung** sama-sama cepat.

---

## Analogi

### Stack (Tumpukan)
Bayangkan **tumpukan piring** di dapur:
1. Kamu meletakkan piring 1, lalu 2, lalu 3, ..., lalu 8 (dari bawah ke atas).
2. Saat mau ambil piring, kamu **pasti mengambil yang paling atas dulu** (piring 8).
3. Piring 1 (paling bawah) baru bisa diambil setelah semua piring di atasnya diambil.

> **"Yang terakhir masuk, yang pertama keluar."**

### Queue (Antrian)
Bayangkan **antrian di SPBU**:
1. Mobil 1 masuk antrian paling depan, mobil 2 di belakangnya, ..., mobil 7 di belakang.
2. Mobil 1 **pertama kali mengisi bensin** karena dia **paling depan**.
3. Mobil yang baru masuk (mobil 8) harus **antri di belakang**.

> **"Yang pertama masuk, yang pertama keluar."**
