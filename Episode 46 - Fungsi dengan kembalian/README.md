# BAB 6 - Fungsi dengan Return

## Apa yang Dipelajari

- Menggunakan keyword `return` untuk mengembalikan nilai dari fungsi
- Fungsi bisa mengembalikan **satu nilai** atau **banyak nilai** (tuple)
- Menggunakan hasil return dalam operasi lain
- Perbedaan `return` dan `print` di dalam fungsi

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Template Fungsi dengan Return

```python
# def nama_fungsi(argument):
#       badan fungsi
#       return output
```

- `return` adalah keyword untuk **mengembalikan nilai** dari fungsi ke pemanggilnya.
- Setelah `return` dijalankan, fungsi **berhenti** dan nilai dikirim ke luar.

#### 2. Fungsi Kuadrat

```python
def kuadrat(input_angka):
    '''Fungsi kuadrat'''
    output_kuadrat = input_angka**2
    return output_kuadrat

y = kuadrat(5)
print(y)
```

- **Alur kerja:**
  1. `kuadrat(5)` dipanggil → `input_angka` = `5`
  2. `output_kuadrat = 5**2` → `output_kuadrat` = `25`
  3. `return 25` → nilai `25` dikirim ke luar
  4. `y = 25` → variabel `y` menyimpan hasil return
- Output: `25`

```python
print(kuadrat(6))
```

- Fungsi `kuadrat(6)` dipanggil dan langsung dimasukkan ke `print()`.
- `6**2 = 36`
- Output: `36`

```python
z = 10 + kuadrat(7)
print(z)
```

- `kuadrat(7)` menghasilkan `49`.
- `z = 10 + 49 = 59`
- Output: `59`

#### 3. Fungsi Tambah dengan Return

```python
def fungsi_tambah(angka_1,angka_2):
    '''fungsi return dengan multi input'''
    return angka_1 + angka_2

a = fungsi_tambah(10,8)
print(a)
```

- Return langsung `angka_1 + angka_2` tanpa perlu variabel penampung.
- `fungsi_tambah(10,8)` → `10 + 8 = 18`
- Output: `18`

#### 4. Return Banyak Nilai (Tuple)

```python
def operasi_matematika(angka_1,angka_2):
    tambah = angka_1 + angka_2
    kurang = angka_1 - angka_2
    kali = angka_1 * angka_2
    bagi = angka_1 / angka_2

    return tambah,kurang,kali,bagi

k,l,m,n = operasi_matematika(9,5)

print(f"Hasil tambah = {k}")
print(f"Hasil kurang = {l}")
print(f"Hasil kali = {m}")
print(f"Hasil bagi = {n}")
```

- `return tambah,kurang,kali,bagi` mengembalikan **4 nilai sekaligus** sebagai **tuple**.
- `k,l,m,n = operasi_matematika(9,5)` → **tuple unpacking**: setiap nilai tuple dipecah ke variabel berbeda.
- Hasil:
  ```
  Hasil tambah = 14    (9+5)
  Hasil kurang = 4     (9-5)
  Hasil kali = 45      (9×5)
  Hasil bagi = 1.8     (9÷5)
  ```

---

## Perbedaan `return` vs `print`

| `print()` di dalam fungsi    | `return` di dalam fungsi          |
|------------------------------|-----------------------------------|
| Hanya **menampilkan** ke layar | **Mengembalikan** nilai ke pemanggil |
| Tidak bisa disimpan ke variabel | Bisa disimpan ke variabel        |
| Tidak bisa dipakai operasi   | Bisa dipakai dalam operasi matematika |

```python
# Dengan print (tidak bisa disimpan)
def tambah_print(a, b):
    print(a + b)

hasil = tambah_print(1, 2)  # hasil = None (tidak ada return)

# Dengan return (bisa disimpan)
def tambah_return(a, b):
    return a + b

hasil = tambah_return(1, 2)  # hasil = 3 (ada return!)
```

---

## Analogi

Bayangkan fungsi adalah **mesin ATM**:

- **Input** (argument) = kartu ATM dan PIN kamu.
- **Proses** = mesin memproses transaksi.
- **Return** = mesin **mengeluarkan uang** (nilai kembali ke tangan kamu).
- Kalau mesin cuma `print("uang kamu 100rb")` tapi tidak mengeluarkan uang, kamu tidak dapat apa-apa. **`return` = uangnya benar-benar keluar**.

---

## Kesalahan Umum Pemula

- **Lupa `return`**: Jika fungsi tidak punya `return`, hasilnya akan `None`.
- **Kode setelah `return`**: Semua kode yang ditulis **setelah** `return` tidak akan dijalankan.
- **Return banyak tanpa unpacking**: Jika tidak dipecah ke variabel, hasilnya berupa tuple.
