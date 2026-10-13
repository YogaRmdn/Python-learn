# BAB 3 - Latihan Percabangan

## Apa yang Dipelajari

- Membuat program kalkulator sederhana menggunakan `if-elif-else`
- Mengonversi input angka ke tipe `float`
- Menggunakan operator logika `or` dalam kondisi
- Membuat pembatas visual dengan karakter berulang

---

## Penjelasan Kode

### Membuat Header Kalkulator

```python
print(20*"=")
print("Kalkulator Sederhana")
print(20*"=" + "\n")
```

| Baris | Penjelasan |
|---|---|
| `20*"="` | Mengulang karakter `=` sebanyak 20 kali → `====================` |
| `print(20*"=")` | Mencetak garis pembatas |
| `"\n"` | Karakter newline (baris baru) |

Hasilnya:
```
====================
Kalkulator Sederhana
====================

```

---

### Membaca Input

```python
angka_1 = float(input("masukan angka 1 = "))
operator = input("operator (+,-,x,/) : ")
angka_2 = float(input("masukan angka 2 = "))
```

| Variabel | Penjelasan |
|---|---|
| `angka_1` | Angka pertama, dikonversi ke `float` (pecahan) agar bisa menampung angka desimal |
| `operator` | Operator matematika yang dimasukkan pengguna (+, -, x, /) |
| `angka_2` | Angka kedua, juga dikonversi ke `float` |

> **Mengapa `float()`?** Karena `input()` selalu mengembalikan string. Tanpa `float()`, operasi matematika akan error.

---

### Percabangan Operator

```python
if operator == "+":
	hasil = angka_1 + angka_2
	print(f"hasilnya adalah {hasil}")
elif operator == "-":
	hasil = angka_1 - angka_2
	print(f"hasilnya adalah {hasil}")
elif operator == "x" or operator == "*":
	hasil = angka_1 * angka_2
	print(f"hasilnya adalah {hasil}")
elif operator == "/":
	hasil = angka_1 / angka_2
	print(f"hasilnya adalah {hasil}")
else:
	print("masukan yang bener dong!, aku pusying")
```

| Kondisi | Aksi |
|---|---|
| `operator == "+"` | Menjumlahkan kedua angka |
| `operator == "-"` | Mengurangkan angka_2 dari angka_1 |
| `operator == "x" or operator == "*"` | Mengalikan kedua angka (menerima `x` atau `*`) |
| `operator == "/"` | Membagi angka_1 dengan angka_2 |
| `else` | Jika operator tidak dikenali, tampilkan pesan error |

**Penggunaan `or`:**

```python
elif operator == "x" or operator == "*":
```

Artinya: jalankan blok ini jika input adalah `"x"` **ATAU** `"*"`. Ini memudahkan pengguna yang mungkin mengetik salah satu dari keduanya.

---

### Akhir Program

```python
print("Akhir dari program, terima gajih!")
```

Dijalankan setelah proses kalkulasi selesai.

---

## Analogi

Bayangkan kamu sedang di kasir minimitori:

- Kamu mengetik dua angka dan pilih operator (+, -, x, /)
- Kasir (program) akan melihat pilihanmu dan menjalankan operasi yang sesuai
- Jika kamu pilih yang tidak ada di daftar, kasir bilang: "Maaf, saya tidak mengerti!"

---

## Contoh Jalankan

```
====================
Kalkulator Sederhana
====================

masukan angka 1 = 10
operator (+,-,x,/) : +
masukan angka 2 = 5
hasilnya adalah 15.0
Akhir dari program, terima gajih!
```

---

## Tips

1. Selalu gunakan `float()` atau `int()` saat membaca angka dari `input()`.
2. Gunakan `or` untuk menangani beberapa kemungkinan input sekaligus.
3. Selalu sediakan blok `else` di akhir untuk menangani input yang tidak valid.
