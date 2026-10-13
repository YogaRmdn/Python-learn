# BAB 17 - Format String

## Apa yang Dipelajari

- F-string (Python 3.6+) sebagai cara modern format string
- Format angka: desimal (`.3f`), ribuan (`,`), leading zero (`010`), tanda `+/-`
- Format persen (`%`)
- Operasi aritmatika di dalam placeholder f-string
- Konversi ke binary (`bin`), octal (`oct`), hexadecimal (`hex`)

## Penjelasan Kode

```python
# format string

# contoh generic
# string
nama = "ucup"
format_str = f"hello {nama}"
print(format_str)
```
- `f"hello {nama}"` adalah **f-string** (formatted string literal).
- Tanda `f` sebelum kutip menandakan ini f-string.
- `{nama}` akan digantikan dengan **nilai** dari variabel `nama`.
- Output: `hello ucup`

---

### Format Berbagai Tipe Data

```python
# boolean
boolean = False
format_str = f"boolean = {boolean}"
print(format_str)           # boolean = False

# angka
angka = 2005.5
format_str = f"angka = {angka}"
print(format_str)           # angka = 2005.5
```

---

### Format Angka Integer

```python
angka = 15
format_str = f"bilangan bulat = {angka:d}"
print(format_str)           # bilangan bulat = 15
```
- `:d` menandakan format **integer (desimal)**.

---

### Format Angka dengan Pemisah Ribuan

```python
angka = 2000000
format_str = f"jutaan = {angka:,}"
print(format_str)           # jutaan = 2,000,000
```
- `:,` menambahkan **koma sebagai pemisah ribuan**.

---

### Format Angka Desimal

```python
angka = 2005.54321
format_str = f"desimal = {angka:.3f}"
print(format_str)           # desimal = 2005.543
```
- `:.3f` menampilkan **3 angka setelah desimal** (dibulatkan).

---

### Leading Zero

```python
angka = 2005.54321
format_str = f"desimal = {angka:010.3f}"
print(format_str)           # desimal = 002005.543
```
- `010.3f` = total lebar **10 karakter**, diisi **nol di depan**, **3 desimal**.

---

### Tanda Plus/Minus

```python
angka_minus = -10
angka_plus = +10.1234
format_minus = f"minus = {angka_minus:+d}"
format_plus = f"plus = {angka_plus:+.2f}"

print(format_minus)         # minus = -10
print(format_plus)          # plus = +10.12
```
- `+d` → menampilkan **tanda `+` untuk positif**, `-` untuk negatif.
- `+.2f` → tanda plus + 2 desimal.

---

### Format Persen

```python
persentase = 0.045
format_persen = f"persen = {persentase:.2%}"
print(format_persen)        # persen = 4.50%
```
- `:.2%` mengalikan nilai dengan 100 dan menambahkan `%`.

---

### Operasi di Dalam Placeholder

```python
harga = 10000
jumlah = 5
format_string = f"harga total = Rp. {harga*jumlah:,}"
print(format_string)        # harga total = Rp. 50,000
```
- `{harga*jumlah:,}` → operasi perkalian **langsung di dalam** placeholder.

---

### Binary, Octal, Hexadecimal

```python
angka = 255
format_binary = f"binary = {bin(angka)}"
format_octal = f"octal = {oct(angka)}"
format_hex = f"hex = {hex(angka)}"

print(format_binary)        # binary = 0b11111111
print(format_octal)         # octal = 0o377
print(format_hex)           # hex = 0xff
```

## Tabel Format Codes

| Code | Keterangan | Contoh | Hasil |
|------|------------|--------|-------|
| `{x}` | Default | `f"{10}"` | `10` |
| `{x:d}` | Integer | `f"{15:d}"` | `15` |
| `{x:,}` | Pemisah ribuan | `f"{2000000:,}"` | `2,000,000` |
| `{x:.nf}` | n desimal | `f"{3.14:.1f}"` | `3.1` |
| `{x:0n}` | Leading zero | `f"{5:04}"` | `0005` |
| `{x:+d}` | Tanda +/- | `f"{-5:+d}"` | `-5` |
| `{x:.n%}` | Persen | `f"{0.05:.1%}"` | `5.0%` |

## Analogi

Bayangkan f-string seperti **surat Label pengiriman**:
- `{nama}` = Bagian yang kamu **isi dengan nama penerima**.
- `:,` = Menambahkan **koma ribuan** agar mudah dibaca (Rp. 1,000,000).
- `.2f` = Mengatur **ketelitian angka** (sama seperti menulis uang: Rp. 10.50, bukan Rp. 10.50000000).
- `+d` = Menambahkan **tanda plus/minus** seperti termometer: +10° atau -5°.
- `:.2%` = Konversi otomatis ke persen: `0.05` → `5.00%`.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi format string |
