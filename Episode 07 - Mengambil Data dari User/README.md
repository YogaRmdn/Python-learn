# BAB 6 - Mengambil Data dari User

## Apa yang Dipelajari

- Fungsi `input()` untuk mengambil data dari user
- Output `input()` selalu berupa **string**
- Konversi input ke tipe data lain: `float()`, `int()`, `bool()`
- Menggabungkan `input()` dengan casting

## Penjelasan Kode

```python
# Episode input user

# data yang dimasukan pasti string
data = input("Masukan data: ")

print("data = ",data,",type =",type(data))

# jika kita ingin mengambil int, maka
angka = float(input("masukan angka: "))
angka = int(input("masukan angka: "))

print("data = ",angka,",type =",type(angka))

bagaimana dengan boolean
biner = bool(int(input("masukan nilai boolean: ")))

print("data = ",biner,",type =",type(biner))
```

### Penjelasan Baris per Baris

---

#### 1. Input Dasar (String)

```python
data = input("Masukan data: ")
print("data = ",data,",type =",type(data))
```
- `input("Masukan data: ")` menampilkan **pesan/promp** `"Masukan data: "` ke layar.
- Program akan **berhenti sejenak** menunggu user mengetik sesuatu dan menekan Enter.
- Apa pun yang diketik user akan disimpan sebagai **string** di variabel `data`.
- Contoh: jika user mengetik `123`, maka `data` bernilai `"123"` (string, bukan angka).

---

#### 2. Konversi Input ke Float dan Integer

```python
angka = float(input("masukan angka: "))
angka = int(input("masukan angka: "))
```
- **Baris pertama:** `input()` mengambil input dari user, lalu `float()` mengubahnya menjadi angka desimal.
  - Contoh input `10.5` → `angka = 10.5` (tipe `float`)
- **Baris kedua:** `input()` mengambil input lagi, lalu `int()` mengubahnya menjadi bilangan bulat.
  - Contoh input `10` → `angka = 10` (tipe `int`)
  - Perhatikan: nilai `angka` di-overwrite (ditimpa) oleh baris kedua.

```python
print("data = ",angka,",type =",type(angka))
```
- Mencetak nilai dan tipe data dari `angka`.

---

#### 3. Konversi Input ke Boolean

```python
biner = bool(int(input("masukan nilai boolean: ")))
```
- Ini adalah **chaining** (penggabungan beberapa fungsi dalam satu baris):
  1. `input("masukan nilai boolean: ")` → mengambil input dari user (string).
  2. `int(...)` → mengubah string ke integer.
  3. `bool(...)` → mengubah integer ke boolean.
- Contoh:
  - User input `1` → `int("1")` = `1` → `bool(1)` = `True`
  - User input `0` → `int("0")` = `0` → `bool(0)` = `False`

```python
print("data = ",biner,",type =",type(biner))
```
- Mencetak hasil konversi ke boolean.

## Alur Proses Input

```
User mengetik "hello" + Enter
         ↓
input() mengembalikan → "hello" (string)
         ↓
float("hello") → ❌ ERROR (bisa jadi crash!)
int("hello")   → ❌ ERROR
```

```
User mengetik "42" + Enter
         ↓
input() mengembalikan → "42" (string)
         ↓
int("42") → 42 (integer) ✅
```

## Analogi

Bayangkan `input()` seperti **kotak surat di depan rumah**:
- Kamu menulis pertanyaan di kertas dan taruh di kotak surat (`input("pesan: ")`).
- Tetangga (user) mengirim jawaban lewat kotak itu.
- **Apa pun yang masuk ke kotak surat, bentuknya selalu kertas** (string).
- Jika kamu mau angka, kamu harus **membaca dan mengubah** kertas itu ke angka (`int()` atau `float()`).
- Jika kamu mau tahu apakah jawabannya "ya" atau "tidak", kamu harus **mengonversi** dulu ke boolean (`bool()`).

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, demonstrasi pengambilan input dari user |
