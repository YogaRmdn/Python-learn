# BAB 1 - Copy Dictionary

## Apa yang Dipelajari

- Cara menyalin (copy) dictionary menggunakan metode `.copy()`
- Perbedaan antara copy dan referensi langsung
- Menghapus elemen dictionary dengan `.pop()` (berdasarkan key)
- Menghapus elemen terakhir dictionary dengan `.popitem()`

---

## Penjelasan Kode

### File: `Main.py`

#### 1. Membuat Dictionary Asal

```python
teman_teman = {
    "cup":"ucup surucup",
    "tong":"otong surotong",
    "dung":"dudung surudung",
    "sep":"asep si kasyep",
    "cuy":"ucuy surucuy"
}
```

- Dictionary `teman_teman` dibuat dengan **key** berupa singkatan nama (cup, tong, dung, sep, cuy) dan **value** berupa nama lengkap.
- Struktur: `{key : value}`

#### 2. Menyalin Dictionary dengan `.copy()`

```python
friends = teman_teman.copy()
```

- `.copy()` membuat **salinan baru** dari dictionary, bukan sekadar membuat variabel baru yang menunjuk ke dictionary yang sama.
- Setelah di-copy, `friends` memiliki isi yang sama dengan `teman_teman`, tapi keduanya adalah dictionary **terpisah** di memori.

#### 3. Menampilkan Isi Kedua Dictionary

```python
print(f"teman-teman: {teman_teman}\n")
print(f"friends: {friends}\n")
```

- Kedua dictionary ditampilkan dan terlihat **identik** saat pertama kali dicetak.

#### 4. Mengubah Isi Dictionary Asal

```python
teman_teman["cup"] = "ucup si kweren"
print(f"teman-teman: {teman_teman}\n")
print(f"friends: {friends}\n")
```

- Nilai key `"cup"` di dictionary `teman_teman` diubah dari `"ucup surucup"` menjadi `"ucup si kweren"`.
- **Hasil penting**: Perubahan pada `teman_teman` **tidak mempengaruhi** `friends`. Ini membuktikan bahwa `.copy()` benar-benar membuat salinan terpisah.
- Jika tanpa `.copy()` (misal `friends = teman_teman`), maka keduanya menunjuk ke dictionary yang sama, dan perubahan satu akan mempengaruhi yang lain.

#### 5. Menghapus Elemen dengan `.pop()`

```python
dataAsep = friends.pop("sep")
print(f"data asep = {dataAsep}\n")
print(f"friends = {friends}\n")
```

- `.pop("sep")` menghapus elemen dengan key `"sep"` dari dictionary `friends`.
- **Nilai yang dihapus** (yaitu `"asep si kasyep"`) dikembalikan dan disimpan ke variabel `dataAsep`.
- Setelah `.pop()`, dictionary `friends` tinggal 4 elemen (tidak ada lagi key `"sep"`).

#### 6. Menghapus Elemen Terakhir dengan `.popitem()`

```python
dataTerakhir = friends.popitem()
print(f"data terakhir = {dataTerakhir}\n")
print(f"friends = {friends}\n")
```

- `.popitem()` menghapus **pasangan key-value terakhir** yang masuk ke dictionary.
- Yang dikembalikan berupa **tuple** `(key, value)`, contohnya: `('cuy', 'ucuy surucuy')`.
- Berguna jika ingin mengambil elemen secara acak dari akhir dictionary.

---

## Ringkasan Metode Dictionary

| Metode      | Fungsi                                    | Return Value              |
|-------------|-------------------------------------------|---------------------------|
| `.copy()`   | Menyalin dictionary ke dictionary baru    | Dictionary baru           |
| `.pop(key)` | Menghapus elemen berdasarkan key          | Nilai dari key yang dihapus |
| `.popitem()`| Menghapus elemen terakhir                 | Tuple (key, value)        |

---

## Analogi

Bayangkan kamu punya **daftar belanja** di kertas:

1. **`.copy()`** = kamu **fotocopy** kertas daftar belanja itu. Sekarang kamu punya 2 kertas. Kalau kamu menulis coretan di kertas asli, kertas fotocopy tetap bersih.
2. **`.pop("apel")`** = kamu **mencoret** item "apel" dari daftar, dan kamu ingat bahwa kamu mencoret "apel".
3. **`.popitem()`** = kamu menghapus **item paling bawah** dari daftar belanja.

---

## Kesalahan Umum Pemula

- **Tanpa `.copy()`**: Jika `friends = teman_teman`, maka `friends` dan `teman_teman` adalah **referensi yang sama**. Mengubah satu akan mengubah yang lain.
- **`.pop()` tanpa key**: Akan menyebabkan error karena Python tidak tahu elemen mana yang mau dihapus.
- **`.popitem()`**: Di Python 3.7+, menghapus elemen yang **paling akhir dimasukkan**. Di versi lebih lama, nilainya tidak bisa diprediksi.
