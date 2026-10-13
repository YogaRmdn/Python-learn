# BAB 13 - Global dan Local Scope

## Apa yang Dipelajari

- **Global scope**: variabel yang didefinisikan di luar fungsi, bisa diakses di mana saja
- **Local scope**: variabel yang didefinisikan di dalam fungsi, hanya bisa diakses di dalam fungsi
- Keyword **`global`**: mengubah variabel global dari dalam fungsi
- Perilaku scope di dalam **loop** dan **percabangan** (`if`)

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Variabel Global

```python
nama_global = "otong" # <- ini variabel global
```

- Variabel yang didefinisikan di **luar fungsi** → berada di **global scope**.
- Bisa diakses dari **mana saja** dalam file.

#### 2. Mengakses Variabel Global di Dalam Fungsi

```python
def fungsi1():
    print(f"fungsi menampilkan {nama_global}")

fungsi1()
```

- Fungsi `fungsi1()` **membaca** variabel global `nama_global`.
- Output: `fungsi menampilkan otong`
- **Penting**: Fungsi bisa **membaca** variabel global tanpa keyword `global`.

#### 3. Mengakses Variabel Global di Dalam Loop

```python
for i in range(0,5):
    print(f"loop {i} - {nama_global}")
```

- Loop juga bisa mengakses variabel global.
- Output:
  ```
  loop 0 - otong
  loop 1 - otong
  loop 2 - otong
  loop 3 - otong
  loop 4 - otong
  ```

#### 4. Mengakses Variabel Global di Dalam Percabangan

```python
if True:
    print(f"if menampilkan {nama_global}")
```

- Percabangan `if` juga bisa mengakses variabel global.
- Output: `if menampilkan otong`

#### 5. Variabel Local Scope

```python
def fungsi2():
    nama_local = "Ucup" # <- variabel lokal scope

fungsi2()
# print(nama_local) # tidak bisa dilakukan bos
```

- `nama_local` didefinisikan di **dalam** fungsi → berada di **local scope**.
- Setelah fungsi selesai dijalankan, variabel lokal **hilang dari memori**.
- `print(nama_local)` di luar fungsi akan menyebabkan **`NameError`**: variabel tidak dikenali.

#### 6. Mengakses Variabel yang Didefinisikan Setelah Fungsi

```python
def say_otong():
    print(f"Hello {nama}")

nama = "Otong"
say_otong()
```

- **Menarik!** Fungsi `say_otong()` menggunakan variabel `nama` yang didefinisikan **setelah** fungsi.
- Tapi tetap jalan karena Python membaca kode **saat fungsi dipanggil**, bukan saat didefinisikan.
- Output: `Hello Otong`

#### 7. Mengubah Variabel Global dari Dalam Fungsi

```python
angka = 0
name = "Ucup"

def ubah(nilai_baru, nama_baru):
    global angka
    global name
    angka = nilai_baru
    name = nama_baru

print(f"Sebelum {angka,name}")
ubah(10,"Otong")
print(f"Sesudah {angka,name}")
```

- Tanpa keyword `global`, `angka = nilai_baru` akan membuat **variabel baru lokal** (bukan mengubah yang global).
- Dengan `global angka`, Python tahu bahwa kita ingin **mengubah variabel global** `angka`.
- Output:
  ```
  Sebelum (0, 'Ucup')
  Sesudah (10, 'Otong')
  ```

#### 8. Scope di Loop dan If

```python
angka = 0

for i in range(0,5):
    angka += i
    angka_dummy = 0

print(angka)        # 0+1+2+3+4 = 10
print(angka_dummy)  # 0 (terakhir di-loop)

if True:
    angka = 5
    angka_dummy = 10

print(angka)        # 5
print(angka_dummy)  # 10
```

- Di Python, **loop dan `if` tidak membuat scope baru** (berbeda dengan bahasa lain seperti JavaScript/Java).
- Variabel yang dibuat di dalam loop/if **tetap ada** di scope yang sama (global atau lokal tergantung konteks).

---

## Ringkasan Scope

| Variabel         | Didefinisikan di     | Scope     | Bisa Diakses dari             |
|------------------|----------------------|-----------|-------------------------------|
| `nama_global`    | Luar fungsi          | Global    | Mana saja                     |
| `nama_local`     | Dalam fungsi         | Local     | Hanya di dalam fungsi         |
| `angka` (dengan `global`) | Dalam fungsi | Global    | Mana saja (setelah `global`)  |

---

## Analogi

Bayangkan **rumah** (global scope) dan **kamar tidur** (local scope):

- **Variabel global** = **TV di ruang tamu**. Siapa saja di rumah bisa nonton TV.
- **Variabel lokal** = **Buku di kamar tidur**. Hanya orang di kamar itu yang bisa baca buku. Kalau kamu keluar kamar, bukunya "hilang".
- **Keyword `global`** = Kamu membawa **TV dari ruang tamu ke kamar tidur**, dan kamu mengganti channel-nya. Perubahan itu terjadi di **TV asli di ruang tamu**.

---

## Kesalahan Umum Pemula

- **Mengakses variabel lokal dari luar fungsi**: Error! Variabel lokal hanya hidup di dalam fungsi.
- **Lupa keyword `global`**: Jika mau mengubah variabel global dari dalam fungsi, harus pakai `global`. Tanpa `global`, Python membuat variabel **baru lokal**.
- **Scope loop**: Di Python, variabel di dalam loop tetap hidup di scope induknya (tidak seperti di bahasa lain).
