# BAB 3 - Strings (Teks)

## Apa yang Dipelajari

- Membuat string (teks) dengan tanda kutip tunggal `'` dan ganda `"`
- Escape character: tanda kutip di dalam string
- Multi-line string dengan `"""`
- Raw string dengan `r''`
- Pengulangan string dengan `*`
- Concatenation (penggabungan string)
- String indexing dan slicing (memotong teks)
- Operasi dasar pada string

---

## Penjelasan Kode

### File: `strings.py`

#### 1. String dengan Tanda Kutip Tunggal

```python
text1 = 'jalan - jalan di hari minggu'
```

- String bisa dibuat dengan **tanda kutip tunggal** `'...'`.
- Isi string bisa berupa teks apa saja.

---

#### 2. Escape Character dengan Backslash `\`

```python
text2 = 'jalan - jalan di hari jum\'at'
```

- Jika ingin menggunakan tanda kutip **di dalam** string yang pakai kutip tunggal, gunakan backslash `\` sebelum kutipnya.
- `\'` berarti "tampilkan kutip tunggal ini sebagai teks biasa".

---

#### 3. String dengan Tanda Kutip Ganda

```python
text3 = "jalan - jalan di hari jum'at"
```

- Gunakan **tanda kutip ganda** `"..."` jika teks mengandung kutip tunggal. Tidak perlu escape.

---

#### 4. Tanda Kutip Ganda di Dalam Kutip Tunggal

```python
text4 = 'mahmuy berkata, "kemaren kemana bro?"'
```

- Kutip ganda `"..."` bisa langsung ditulis di dalam string kutip tunggal tanpa escape.

---

#### 5. Escape dengan Kutip Ganda

```python
text5 = "hobloh menjawab, \"jalan - jalan bro\" "
```

- Begitu juga sebaliknya: `\"` untuk menampilkan kutip ganda di dalam string kutip ganda.

---

#### 6. Newline dengan `\n`

```python
text6 = 'mahmuy: "kemaren kemana bro?" \nhobloh: "jalan - jalan bro"'
```

- `\n` adalah **newline** (ganti baris). Teks setelah `\n` akan muncul di baris baru.

---

#### 7. Multi-line String dengan `"""`

```python
text7 = """
mahmuy: "kemaren kemana bro?"
hobloh: "jalan - jalan bro"
mahmuy: "jalan - jalan kemana bro?"
hobloh: "ke Mang Uing bro!!!!"
"""
```

- Tiga tanda kutip `"""..."""` memungkinkan menulis teks **lintas beberapa baris** tanpa perlu `\n`.

---

#### 8. Raw String dengan `r''`

```python
text8 = r'C:\nyoto'
```

- Awalan `r` sebelum kutip membuat string menjadi **raw string** (teks mentah).
- Tanpa `r`, `\n` akan dianggap sebagai newline. Dengan `r`, `\n` ditulis apa adanya sebagai karakter `\` dan `n`.

---

#### 9. Operasi pada String

```python
print(text8)
print(5*"wk")
print('kue' 'pukis')
print(text1 + text2)
```

| Operasi | Kode | Hasil | Penjelasan |
|---------|------|-------|------------|
| Tampilkan | `print(text8)` | `C:\nyoto` | Menampilkan isi variabel |
| Pengulangan | `5*"wk"` | `wk wk wk wk wk` | Teks diulang 5 kali |
| Concat tanpa `+` | `'kue' 'pukis'` | `kuepukis` | Dua string berdampingan otomatis digabung |
| Concat dengan `+` | `text1 + text2` | `jalan - jalan di hari minggujalan - jalan di hari jum'at` | Digabung dengan operator `+` |

---

### File: `strings2.py`

#### Visualisasi Index String

```python
# |p|i|s|a|n|g| |g|o| r | e | n | g |
# | | | | | | | | | |   |   |   |   |
# 0 1 2 3 4 5 6 7 8 9  10   11  12  13
```

Setiap karakter dalam string memiliki **nomor indeks** mulai dari `0`.

---

#### Slicing (Memotong String)

```python
text = "pisang goreng"
a = text[2:]
```

- `text[2:]` artinya ambil karakter dari indeks **2 sampai akhir**.
- `text[2]` = `s`, `text[3]` = `a`, dst. → hasilnya: `"sang goreng"`

```python
print('e'+a+' bau')
```

- `'e' + a + ' bau'` = `'e' + 'sang goreng' + ' bau'` = `"esang goreng bau"`

---

## Ringkasan Slicing

| Kode | Arti | Hasil |
|------|------|-------|
| `text[0]` | Karakter pertama | `p` |
| `text[2]` | Karakter indeks ke-2 | `s` |
| `text[-1]` | Karakter terakhir | `g` |
| `text[2:]` | Dari indeks 2 sampai akhir | `sang goreng` |
| `text[:5]` | Dari awal sampai indeks 4 | `pisang` |
| `text[2:5]` | Dari indeks 2 sampai 4 | `san` |

---

## Analogi

Bayangkan string adalah **deretan kereta**:

```
| P | I | S | A | N | G |
| 0 | 1 | 2 | 3 | 4 | 5 |
```

- **Indexing**: Kamu mau duduk di gerbong ke-2? Itu `text[2]` = `S`.
- **Slicing**: Kamu mau ambil gerbong dari nomor 2 sampai akhir? Itu `text[2:]` = `SANG`.
- **Concatenation**: Kamu menyambung dua rangkaian kereta jadi satu.
- **Raw string** (`r''`): Seperti menulis catatan apa adanya, tanpa interpretasi khusus.

---

## Tips untuk Pemula

- Jika teks mengandung banyak tanda kutip, gunakan **triple quotes** `"""..."""`.
- Ingat: index di Python **mulai dari 0**, bukan 1!
- Negative index: `text[-1]` adalah karakter terakhir, `text[-2]` adalah karakter kedua dari belakang.
