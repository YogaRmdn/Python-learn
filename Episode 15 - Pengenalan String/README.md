# BAB 14 - Pengenalan String

## Apa yang Dipelajari

- Cara membuat string: single quote (`'...'`), double quote (`"..."`)
- Escape characters: `\'`, `\"`, `\\`, `\t`, `\b`, `\n`, `\r`
- Raw string (`r'...'`) untuk mengabaikan escape character
- Multiline string menggunakan triple quotes (`"""..."""`)
- Perbedaan `\n` (LF), `\r` (CR), dan `\r\n` (CRLF)


## Penjelasan Kode

```python
data = "ini adalah string"
print(data)
print(type(data))
```
- String dibuat dengan **tanda kutip** (single `'` atau double `"`).
- `type(data)` → `<class 'str'>`.

---

### 1. Cara Membuat String

```python
data = 'Menggunakan single quote'
print(data)

data = "Menggunakan double quote"
print(data)
```
- Bisa menggunakan **single quote** atau **double quote**, hasilnya sama.

```python
print('"Halo, apa kabar?"')
print("'Halo, apa kabar?'")
print("ini adalah hari jum'at")
```
- Jika string pakai double quote (`"`), kamu bisa pakai single quote (`'`) di dalamnya tanpa escape, dan sebaliknya.

---

### 2. Escape Characters

```python
# membuat tanda ' menjadi string
print('mari shalat jum\'at')
print('g\'day, isn\'t it?')
```
- `\'` → menampilkan **tanda kutip tunggal** di dalam string single quote.

```python
# backslash
print("C:\\user\\Ucup")
```
- `\\` → menampilkan **satu backslash** `\`. Karena `\` sendiri adalah escape character, perlu ditulis dua kali.

```python
# tab
print("ucup\t\t\totong, semakin jauhan")
```
- `\t` → **tab horizontal** (spasi lebar). Digunakan tiga kali.

```python
# backspace
print("ucup \botong, jadi deketan")
```
- `\b` → **backspace** (hapus karakter sebelumnya).

```python
# newline
print("baris pertama.\nbaris kedua.")     # LF → unix, macos, linux
print("baris pertama.\rbaris kedua.")     # CR → commodore, acorn, lisp
print("baris pertama.\r\nbaris kedua.")   # CRLF → windows
```
- `\n` → **Line Feed** (pindah baris baru). Dipakai di Unix/Mac/Linux.
- `\r` → **Carriage Return** (kembali ke awal baris). Dipakai di sistem lama.
- `\r\n` → **CRLF** (kombinasi). Dipakai di **Windows**.

---

### 3. Raw String

```python
# hati-hati
print('C:\new folder')   # akan salah pathnya (\n jadi newline!)

# menggunakan raw string
print(r'C:\new folder')  # benar, \new ditampilkan apa adanya
```
- Tanpa `r`, Python menganggap `\n` sebagai **newline**.
- Dengan `r`, Python menganggap `\n` sebagai **teks literal** `\n`.

---

### 4. Multiline String

```python
print("""
Nama : Ucup
Kelas : 3 SD   
""")
```
- Triple double quotes (`"""..."""`) untuk string yang **memakan beberapa baris**.

```python
print(r"""
Nama : Ucup
Kelas : 3 SD\new normal 
Website : www.ucup.com/newID
""")
```
- Multiline + raw string: tidak ada escape character yang diproses.

## Tabel Escape Characters

| Escape | Keterangan | Contoh Output |
|--------|------------|---------------|
| `\'` | Tanda kutip tunggal | `'` |
| `\"` | Tanda kutip ganda | `"` |
| `\\` | Backslash | `\` |
| `\t` | Tab horizontal | (spasi lebar) |
| `\b` | Backspace | (hapus karakter sebelum) |
| `\n` | Newline (baris baru) | (pindah baris) |
| `\r` | Carriage return | (kembali ke awal baris) |

## Analogi

Bayangkan string seperti **papan tulis**:
- **Single/Double quote** = Kamu bisa menulis di papan tulis dengan **spidol hitam** atau **spidol biru**, hasilnya sama (terbaca).
- **Escape characters** (`\`) = seperti **kode rahasia**: `\n` artinya "pindah baris", `\t` artinya "kasih spasi lebar".
- **Raw string** (`r'...'`) = "Jangan terjemahkan kode rahasia, tulis saja apa adanya".
- **Multiline string** (`"""..."""`) = Papan tulis yang **sangat panjang**, bisa menulis di banyak baris sekaligus.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, pengenalan string Python |
