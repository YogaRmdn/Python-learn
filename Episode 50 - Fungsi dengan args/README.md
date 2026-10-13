# BAB 10 - Fungsi dengan *args

## Apa yang Dipelajari

- **`*args`**: menerima **banyak argument** tanpa harus mendefinisikan satu per satu
- Perbedaan fungsi biasa vs fungsi dengan `*args`
- `args` bertipe **tuple** (immutable, bisa diiterasi)
- Studi kasus: fungsi penjumlahan fleksibel

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Fungsi Biasa (Tanpa *args)

```python
def fungsi(nama,tinggi,berat):
    print(f"{nama} punya tinggi {tinggi} dan berat {berat}")

fungsi("ucup",170,40)
```

- Fungsi ini **wajib** menerima tepat **3 argument**: nama, tinggi, berat.
- Jika argument lebih sedikit atau lebih banyak → **error**.

#### 2. Fungsi dengan List

```python
def fungsi(data_list):
    data = data_list.copy()
    nama = data[0]
    tinggi = data[1]
    berat = data[2]
    print(f"{nama} punya tinggi {tinggi} dan berat {berat}")

fungsi(["otong",100,120])
```

- Semua data dikemas dalam **satu list**.
- Akses data pakai indeks: `data[0]`, `data[1]`, `data[2]`.
- Kelemahan: harus pakai list, tidak fleksibel.

#### 3. Mengenal `*args`

```python
def fungsi(*args):
    nama = args[0]
    tinggi = args[1]
    berat = args[2]
    print(f"{nama} punya tinggi {tinggi} dan berat {berat}")

fungsi("dudung",120,120)
```

- **`*args`** → tanda `*` di depan parameter membuat Python mengumpulkan **semua argument** yang dikirim ke dalam **tuple** bernama `args`.
- `fungsi("dudung",120,120)` → `args = ("dudung", 120, 120)`
- Akses pakai indeks seperti biasa: `args[0]` = `"dudung"`, `args[1]` = `120`.

#### 4. Studi Kasus: Fungsi Penjumlahan Fleksibel

```python
def tambah(*data):
    # data tipenya adalah tuple, dia bisa diiterasi
    output = 0
    for angka in data:
        output += angka
    return output

hasil = tambah(1,2,3,4,5,6,7,8,9)
print(f"hasil = {hasil}")

hasil = tambah(10,5,15)
print(f"hasil = {hasil}")
```

- **`*data`** menampung berapa pun jumlah angka.
- Loop `for` menjumlahkan semua angka di dalam tuple `data`.
- `tambah(1,2,3,4,5,6,7,8,9)` → `1+2+3+4+5+6+7+8+9 = 45`
- `tambah(10,5,15)` → `10+5+15 = 30`

---

## Cara Kerja *args

```
fungsi("dudung", 120, 120)
        │        │     │
        ▼        ▼     ▼
    args = ("dudung", 120, 120)  ← Tuple
              │        │     │
           args[0]  args[1] args[2]
```

---

## Perbandingan Pendekatan

| Pendekatan                | Cara Kerja                                | Fleksibel? |
|---------------------------|-------------------------------------------|------------|
| 3 parameter biasa         | `fungsi(nama, tinggi, berat)`             | Tidak      |
| 1 parameter list          | `fungsi(["ucup", 170, 40])`              | Cukup      |
| `*args`                   | `fungsi("ucup", 170, 40)`               | Sangat     |

---

## Analogi

Bayangkan `*args` seperti **keranjang belanja**:

- **Fungsi biasa**: Kamu bawa **3 kantong khusus**: kantong buah, kantong sayur, kantong daging. Harus isi semua.
- **Fungsi `*args`**: Kamu bawa **1 keranjang besar**. Isi berapa pun yang kamu mau: 3 item, 5 item, 10 item.
- Python akan **mengumpulkan** semua item ke dalam tuple.

---

## Aturan *args

1. **`*` sebelum nama parameter** → mengubah semua argument menjadi tuple.
2. **Nama `args` tidak wajib**: Bisa `*angka`, `*data`, `*semua`, dll.
3. **Bisa digabung** dengan parameter biasa:
   ```python
   def fungsi(nama, *data):
       # nama = argument pertama (string)
       # data = tuple sisa argument
   ```
4. **`*args` harus di belakang** parameter biasa:
   ```python
   # BENAR
   def fungsi(nama, *args): ...
   # SALAH
   def fungsi(*args, nama): ...  # Error!
   ```
