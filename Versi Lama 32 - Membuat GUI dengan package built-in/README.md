# BAB 8 - Membuat GUI dengan Package Built-in

## Apa yang Dipelajari

- **GUI (Graphical User Interface)** : Interface berbasis grafis (jendela, tombol, label) alih-alih teks
- **`tkinter`** : Package GUI bawaan Python (built-in), tidak perlu install
- **Widget** : Elemen-elemen GUI seperti Label, Button, Entry, dll.
- **`mainloop()`** : Event loop yang menjalankan GUI dan menunggu interaksi pengguna
- **Event handling** : Menangani aksi pengguna (seperti menekan tombol)

## Penjelasan Kode

Berikut adalah kode lengkap dari program ini:

```python
import tkinter

main_window = tkinter.Tk()

def event_tekan():
    label2 = tkinter.Label(main_window, text="aku ditekan ^_^")
    label2.pack()


label = tkinter.Label(main_window, text="halo, saya adalah \n GUI sederhana dengan \n menggunakan python")
tombol = tkinter.Button(main_window, text="tekan akuh", command = event_tekan)

label.pack()
tombol.pack()
main_window.mainloop()
```

### Blok 1: Import dan Membuat Window Utama

```python
import tkinter
main_window = tkinter.Tk()
```

- `import tkinter` - Mengimport package `tkinter` yang sudah **built-in** (bawaan Python). Tidak perlu `pip install`.
- `tkinter.Tk()` - Membuat **jendela utama** (top-level window) dari aplikasi GUI. Ini adalah "kanvas" di mana semua widget akan ditempatkan.
- `main_window` - Variabel yang menyimpan referensi ke jendela utama.

### Blok 2: Fungsi Event Handler

```python
def event_tekan():
    label2 = tkinter.Label(main_window, text="aku ditekan ^_^")
    label2.pack()
```

- `def event_tekan():` - Mendefinisikan fungsi yang akan **dijalankan saat tombol ditekan**.
- `tkinter.Label(main_window, text="aku ditekan ^_^")` - Membuat widget **Label** (teks) baru dengan teks `"aku ditekan ^_^"`. Label ini ditempatkan di `main_window`.
- `label2.pack()` - Menggunakan metode `pack()` untuk **menempatkan** label ke jendela. Tanpa `pack()`, widget tidak akan terlihat di layar.

### Blok 3: Membuat Widget

```python
label = tkinter.Label(main_window, text="halo, saya adalah \n GUI sederhana dengan \n menggunakan python")
tombol = tkinter.Button(main_window, text="tekan akuh", command = event_tekan)
```

- **Label:**
  - `tkinter.Label(main_window, ...)` - Membuat widget label (teks statis).
  - `text="halo, saya adalah \n GUI sederhana dengan \n menggunakan python"` - Teks yang ditampilkan. `\n` adalah **newline** (pindah baris).
- **Button:**
  - `tkinter.Button(main_window, ...)` - Membuat widget tombol.
  - `text="tekan akuh"` - Teks yang ditampilkan di tombol.
  - `command = event_tekan` - **Event handler**: fungsi `event_tekan` akan dipanggil **otomatis** saat tombol diklik. Perhatikan tidak ada `()` - hanya nama fungsi, bukan pemanggilan fungsi.

### Blok 4: Menempatkan Widget dan Menjalankan GUI

```python
label.pack()
tombol.pack()
main_window.mainloop()
```

- `label.pack()` - Menempatkan label ke jendela.
- `tombol.pack()` - Menempatkan tombol ke jendela (di bawah label).
- `main_window.mainloop()` - **Event loop** yang membuat jendela muncul di layar dan **menunggu** interaksi pengguna (klik, ketik, dll.). Program akan terus berjalan sampai jendela ditutup. **Semua kode setelah `mainloop()` tidak akan dijalankan sampai GUI ditutup.**

### Diagram Widget

```
main_window (jendela utama)
│
├── label  → "halo, saya adalah \n GUI sederhana dengan \n menggunakan python"
│
├── tombol → "tekan akuh"
│
└── [setelah tombol diklik]
    └── label2 → "aku ditekan ^_^"
```

## Analogi

Bayangkan **membuat formulir pendaftaran online**:

- **`tkinter.Tk()`** = Membuat **halaman kosong** di website.
- **Label** = **Judul/formulir teks** yang memberi tahu pengguna apa yang harus dilakukan. Teks ini tidak bisa diklik atau diubah.
- **Button** = **Tombol "Kirim"** yang bisa diklik. Saat diklik, sesuatu terjadi (misalnya muncul pesan sukses).
- **`command=event_tekan`** = **Program di balik tombol**. Saat tombol "Kirim" diklik, program ini berjalan (muncul pesan "aku ditekan").
- **`pack()`** = **Menata letak** elemen-elemen di halaman (atas, bawah, kiri, kanan).
- **`mainloop()`** = **Menjaga halaman tetap aktif**. Tanpa ini, halaman langsung tertutup sebelum pengguna sempat melihat atau mengklik apa pun.

> **Note:** `tkinter` adalah package **built-in** (sudah ada di Python). Tidak perlu install apapun - cukup `import tkinter` dan langsung bisa membuat GUI!
