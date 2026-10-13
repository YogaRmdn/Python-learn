# BAB 5 - Versi Lama 17: Tuples

## Apa yang Dipelajari

- Membuat tuple dan membandingkannya dengan list
- Memahami sifat **immutable** (tidak bisa diubah)
- **Efisiensi memori**: tuple lebih hemat memori dari list
- **Kecepatan**: tuple lebih cepat diproses daripada list

---

## Penjelasan Kode

### File 1: `tuples.py` — Perbedaan List vs Tuple

```python
# List
Ganjil = [1, 3, 5, 7, 9]

# Tuple
Genap = (2, 4, 6, 6, 8, 10)

print(type(Ganjil))
# Output: <class 'list'>

print(type(Genap))
# Output: <class 'tuple'>

print(Genap)
# Output: (2, 4, 6, 6, 8, 10)
```

| Aspek | List | Tuple |
|-------|------|-------|
| **Tanda** | `[ ]` (kurung siku) | `( )` (kurung bulat) |
| **Type** | `<class 'list'>` | `<class 'tuple'>` |
| **Bisa diubah?** | Ya (mutable) | **Tidak** (immutable) |
| **Contoh** | `[1, 3, 5]` | `(2, 4, 6)` |

> **Immutable** = Setelah dibuat, kamu **tidak bisa** menambah, menghapus, atau mengubah isi tuple.

---

### File 2: `testTuple.py` — Perbandingan Ukuran Memori

```python
import sys

data_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, "pisang goreng", "syahrini", "via vallen", False, 3.14]
data_tuple = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, "pisang goreng", "syahrini", "via vallen", False, 3.14)

besar_datalist = sys.getsizeof(data_list)
besar_datatuple = sys.getsizeof(data_tuple)

print("besar data list:", besar_datalist)
print("besar data tuple:", besar_datatuple)
```

| Elemen | Penjelasan |
|--------|-----------|
| `import sys` | Mengimpor modul `sys` untuk mengakses informasi sistem |
| `sys.getsizeof()` | Mengembalikan **ukuran memori** (dalam byte) dari suatu objek |

**Hasil**: Tuple menggunakan **lebih sedikit memori** daripada list karena:
- List membutuhkan **ruang ekstra** untuk alokasi kapasitas (agar bisa tumbuh dinamis).
- Tuple bersifat tetap, sehingga Python tidak perlu ruang ekstra.

---

### File 3: `testTuple2.py` — Perbandingan Kecepatan Eksekusi

```python
import timeit

data_list = timeit.timeit(stmt="[1,2,3,4,5,6,7,8,9]", number=1000000)
data_tuple = timeit.timeit(stmt="(1,2,3,4,5,6,7,8,9)", number=1000000)

print("waktu untuk memproses list:", data_list)
print("waktu untuk memproses tuple:", data_tuple)
```

| Elemen | Penjelasan |
|--------|-----------|
| `import timeit` | Modul untuk mengukur waktu eksekusi kode |
| `timeit.timeit()` | Menjalankan `stmt` sebanyak `number` kali, mengembalikan waktu total (detik) |
| `number=1000000` | Menjalankan 1.000.000 kali untuk hasil yang signifikan |

**Hasil**: Tuple **lebih cepat** dibuat daripada list. Python bisa mengonstruksi tuple secara statis saat kompilasi, sementara list harus dialokasikan dinamis.

---

## Ringkasan: List vs Tuple

| Aspek | List | Tuple |
|-------|------|-------|
| **Sintaks** | `[1, 2, 3]` | `(1, 2, 3)` |
| **Mutable?** | Ya | **Tidak** |
| **Memori** | Lebih besar | **Lebih kecil** |
| **Kecepatan** | Lebih lambat | **Lebih cepat** |
| **Keyakinan** | Bisa berubah kapan saja | Pasti aman isinya tidak berubah |
| **Penggunaan** | Data yang sering berubah | Data yang konstan (koordinat, warna RGB, dll.) |

---

## Analogi

### List = **Papan Tulis**
Kamu bisa **menghapus, menulis ulang, dan menambah** tulisan di papan tulis kapan saja. Tapi karena sering diubah, informasi di papan tulis **bisa berubah** dan **tidak terjamin keasliannya**.

### Tuple = **Batu Nisan / Piagam**
Begitu ditulis, isinya **tidak bisa diubah lagi**. Kalau kamu ingin mengubahnya, kamu harus membuat batu nisan/piagam yang **baru sepenuhnya**. Karena isinya permanen, orang bisa **mempercayai** bahwa data di dalamnya **tidak akan berubah**.

> **Kapan pakai tuple?** Gunakan tuple untuk data yang seharusnya **tidak berubah**, seperti koordinat GPS `(latitude, longitude)`, warna RGB `(255, 0, 0)`, atau versi software `(3, 8, 5)`.
