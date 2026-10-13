# BAB 11 - Fungsi dengan **kwargs

## Apa yang Dipelajari

- **`**kwargs`**: menerima banyak argument **keyword** dalam bentuk dictionary
- Perbedaan `*args` (tuple) vs `**kwargs` (dictionary)
- Mengakses nilai `kwargs` dengan key
- Menggabungkan `*args` dan `**kwargs` dalam satu fungsi
- Studi kasus: kalkulator dengan pilihan operasi

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Fungsi Biasa

```python
def fungsi(nama,tinggi,berat):
    '''fungsi biasa'''
    print(f"{nama} punya tinggi {tinggi} dan berat {berat}")

fungsi("ucup",183,79)
```

- Fungsi biasa dengan 3 parameter positional.
- Argument harus dikirim berurutan: nama, tinggi, berat.

#### 2. Fungsi dengan `**kwargs`

```python
def fungsi(**kwargs):
    '''fungsi kwargs'''
    nama = kwargs["nama"]
    tinggi = kwargs["tinggi"]
    berat = kwargs["berat"]
    print(f"{nama} punya tinggi {tinggi} dan berat {berat}")

fungsi(nama="ucup",tinggi=183,berat=79)
```

- **`**kwargs`** → tanda `**` di depan parameter membuat Python mengumpulkan semua argument **keyword** ke dalam **dictionary** bernama `kwargs`.
- `fungsi(nama="ucup",tinggi=183,berat=79)` → kwargs = `{"nama": "ucup", "tinggi": 183, "berat": 79}`
- Nilai diakses dengan **key**: `kwargs["nama"]`, bukan indeks.

#### 3. Studi Kasus: Kalkulator dengan *args dan **kwargs

```python
def math(*args,**kwargs):
    output = 0
    if kwargs["option"] == "tambah":
        for angka in args:
            output +=angka
    elif kwargs["option"] == "kali":
        output = 1
        for angka in args:
            output *= angka
    else:
        print("tidak ada operasi")

    return output

hasil = math(1,2,3,4,option="tambah")
print(f"hasil jumlah {hasil}")

hasil = math(1,2,3,4,option="kali")
print(f"hasil kali {hasil}")
```

- **`*args`** menampung angka-angka: `(1,2,3,4)`
- **`**kwargs`** menampung keyword argument: `{"option": "tambah"}`
- **Jika option = "tambah"**: semua angka dijumlahkan → `1+2+3+4 = 10`
- **Jika option = "kali"**: semua angka dikalikan → `1×2×3×4 = 24`

---

## Perbedaan *args vs **kwargs

| Aspek           | `*args`                        | `**kwargs`                        |
|-----------------|--------------------------------|-----------------------------------|
| **Tipe data**   | Tuple                          | Dictionary                        |
| **Cara kirim**  | Posisional: `fungsi(1,2,3)`   | Keyword: `fungsi(a=1,b=2,c=3)`  |
| **Akses**       | Indeks: `args[0]`              | Key: `kwargs["nama"]`             |
| **Urutan**      | Penting                        | Tidak penting                     |

---

## Cara Kerja **kwargs

```
fungsi(nama="ucup", tinggi=183, berat=79)
   │          │            │          │
   ▼          ▼            ▼          ▼
kwargs = {
    "nama": "ucup",
    "tinggi": 183,
    "berat": 79
}
```

---

## Menggabungkan *args dan **kwargs

```python
def contoh(*args, **kwargs):
    print(f"args: {args}")       # Tuple
    print(f"kwargs: {kwargs}")   # Dictionary

contoh(1, 2, 3, nama="Ucup", kota="Bandung")
```

Output:
```
args: (1, 2, 3)
kwargs: {'nama': 'Ucup', 'kota': 'Bandung'}
```

---

## Analogi

Bayangkan kamu **order makanan di restoran**:

- **`*args`** = Kamu pesan **banyak makanan** tanpa nama: "Nasi, Ayam, Sambal, Kerupuk". Pelayan mencatat **berurutan**.
- **`**kwargs`** = Kamu pesan dengan **nama spesifik**: "Menu: Nasi Goreng, Ukuran: Besar, Minum: Es Teh". Pelayan mencatat berdasarkan **label/nama pesanan**.

---

## Aturan Penggunaan

1. **Urutan yang benar**: `(parameter_biasa, *args, **kwargs)`
2. **`**kwargs` harus di posisi terakhir** setelah `*args`.
3. **Nama `kwargs` tidak wajib**: Bisa `**data`, `**options`, dll.
4. **Hati-hati dengan key**: Jika key tidak ada di kwargs, akan terjadi `KeyError`.
