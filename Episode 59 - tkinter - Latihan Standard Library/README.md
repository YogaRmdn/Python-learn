# BAB 19 - tkinter: Latihan Standard Library (GUI Dasar)

## Apa yang Dipelajari

- **tkinter**: module bawaan Python untuk membuat **GUI** (Graphical User Interface)
- Membuat **window** (jendela) utama
- Menggunakan komponen: **Label**, **Entry**, **Button**, **Frame**
- Mengelola tata letak dengan **`.pack()`**
- Menggunakan **`StringVariabel`** untuk mengikat data ke komponen
- Menampilkan **messagebox** (popup) saat tombol diklik
- Konsep **`mainloop()`**: menjalankan aplikasi GUI terus-menerus

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Import tkinter

```python
import tkinter as tk
from tkinter import ttk
from tkinter.messagebox import showinfo
```

- **`import tkinter as tk`** → import module tkinter dengan alias `tk`.
- **`from tkinter import ttk`** → import widget bertema (themed) yang lebih modern.
- **`from tkinter.messagebox import showinfo`** → import fungsi untuk menampilkan popup info.

#### 2. Membuat Window Utama

```python
window = tk.Tk()
window.configure(bg="white")
window.geometry("300x200")
window.resizable(False,False)
window.title("Sapa Dia!")
```

| Baris                     | Fungsi                                           |
|---------------------------|--------------------------------------------------|
| `window = tk.Tk()`       | Membuat **jendela utama** (root window)          |
| `window.configure(bg="white")` | Mengatur **warna latar belakang** jadi putih |
| `window.geometry("300x200")` | Mengatur **ukuran** jendela: 300px lebar, 200px tinggi |
| `window.resizable(False,False)` | **Tidak bisa diubah ukuran** (lebar & tinggi) |
| `window.title("Sapa Dia!")` | Mengatur **judul** jendela                      |

#### 3. Membuat Variabel tkinter

```python
NAMA_DEPAN = tk.StringVar()
NAMA_BELAKANG = tk.StringVar()
```

- **`tk.StringVar()`** → variabel khusus tkinter yang **otomatis terhubung** ke widget (Entry/Label).
- Ketika user mengetik di Entry, nilai `NAMA_DEPAN` otomatis berubah.
- Untuk mengambil nilai: `NAMA_DEPAN.get()`
- Untuk mengatur nilai: `NAMA_DEPAN.set(" nilai baru")`

#### 4. Fungsi Tombol

```python
def tombol_click():
    '''fungsi ini akan dipanggil oleh tombol'''
    pesan = f"Halo {NAMA_DEPAN.get()} {NAMA_BELAKANG.get()}, Ganteeeng!"
    showinfo(title="Whazzup!",message=pesan)
```

- Fungsi ini dijalankan saat user **mengklik tombol** "Sapa!".
- **`NAMA_DEPAN.get()`** → mengambil teks yang diketik user di entry nama depan.
- **`NAMA_BELAKANG.get()`** → mengambil teks dari entry nama belakang.
- **`showinfo(title, message)`** → menampilkan **popup** dengan judul dan pesan.

#### 5. Membuat Frame (Container)

```python
input_frame = ttk.Frame(window)
input_frame.pack(padx=10,pady=10,fill="x",expand=True)
```

- **`ttk.Frame(window)`** → membuat **frame** (kotak container) di dalam window.
- **`.pack(padx=10, pady=10)`** → menambahkan padding (jarak) 10px di kiri-kanan dan atas-bawah.
- **`fill="x"`** → frame mengisi **lebar penuh** window.
- **`expand=True`** → frame bisa **mengembang** jika window diubah ukurannya.

#### 6. Membuat Komponen-komponen GUI

**Label Nama Depan:**
```python
nama_depan_label = ttk.Label(input_frame, text="Nama Depan:")
nama_depan_label.pack(padx=10, fill="x", expand=True)
```

- **`ttk.Label(parent, text)`** → label teks yang menampilkan "Nama Depan:".
- **`.pack()`** → menempatkan komponen ke dalam frame.

**Entry Nama Depan:**
```python
nama_depan_entry = ttk.Entry(input_frame, textvariable=NAMA_DEPAN)
nama_depan_entry.pack(padx=10, fill="x", expand=True)
```

- **`ttk.Entry(parent, textvariable)`** → kolom input teks yang **terhubung** ke variabel `NAMA_DEPAN`.
- Ketika user mengetik, `NAMA_DEPAN.get()` akan mengembalikan teks yang diketik.

**Label Nama Belakang:**
```python
nama_belakang_label = ttk.Label(input_frame, text="Nama belakang:")
nama_belakang_label.pack(padx=10, fill="x", expand=True)
```

**Entry Nama Belakang:**
```python
nama_belakang_entry = ttk.Entry(input_frame, textvariable=NAMA_BELAKANG)
nama_belakang_entry.pack(padx=10, fill="x", expand=True)
```

**Tombol Sapa:**
```python
tombol_sapa = ttk.Button(input_frame, text="Sapa!", command=tombol_click)
tombol_sapa.pack(fill='x', expand=True, padx=10, pady=10)
```

- **`ttk.Button(parent, text, command)`** → tombol dengan teks "Sapa!" yang menjalankan fungsi `tombol_click` saat diklik.
- **`command=tombol_click`** → memberitahu tombol: "Jika diklik, jalankan fungsi ini".

#### 7. Main Loop

```python
window.mainloop()
```

- **`mainloop()`** → menjalankan aplikasi GUI **terus-menerus** (event loop).
- Jendela akan tetap terbuka sampai user menutupnya.
- **Tanpa `mainloop()`**, jendela langsung muncul dan langsung hilang.

---

## Alur Aplikasi

```
┌─────────────────────────────────┐
│          Sapa Dia!              │
│                                 │
│  Nama Depan:                    │
│  ┌─────────────────────────┐    │
│  │ [user ketik nama]       │    │
│  └─────────────────────────┘    │
│                                 │
│  Nama Belakang:                 │
│  ┌─────────────────────────┐    │
│  │ [user ketik nama]       │    │
│  └─────────────────────────┘    │
│                                 │
│  ┌─────────────────────────┐    │
│  │        Sapa!            │    │ ← Klik tombol ini
│  └─────────────────────────┘    │
└─────────────────────────────────┘
              │
              ▼ (klik tombol)
┌─────────────────────────────────┐
│  ┌───────────────────────┐      │
│  │     Whazzup!          │      │
│  │                       │      │
│  │ Halo Ucup Surucup,    │      │
│  │ Ganteeeng!            │      │
│  │                       │      │
│  │           [ OK ]      │      │
│  └───────────────────────┘      │
└─────────────────────────────────┘
```

---

## Komponen tkinter

| Komponen       | Fungsi                                    | Contoh                               |
|----------------|-------------------------------------------|---------------------------------------|
| `Tk()`         | Jendela utama                             | `window = tk.Tk()`                   |
| `Frame`        | Kotak container untuk menampung widget    | `ttk.Frame(window)`                  |
| `Label`        | Teks label (tidak bisa diedit)             | `ttk.Label(frame, text="Nama:")`     |
| `Entry`        | Kolom input teks (bisa diedit)             | `ttk.Entry(frame, textvariable=var)` |
| `Button`       | Tombol klik                               | `ttk.Button(frame, text="OK", command=func)` |
| `StringVar`    | Variabel yang terhubung ke widget          | `tk.StringVar()`                     |
| `showinfo`     | Popup messagebox                          | `showinfo(title, message)`           |

---

## Manajemen Tata Letak (Layout Manager)

| Metode   | Fungsi                                                      |
|----------|--------------------------------------------------------------|
| `.pack()` | Menyusun widget secara **vertikal/horizontal** (otomatis)  |
| `.grid()` | Menyusun widget dalam **grid/tabel** (baris & kolom)       |
| `.place()` | Menempatkan widget dengan **koordinat absolut** (x, y)     |

Dalam kode ini, hanya `.pack()` yang digunakan.

---

## Analogi

Bayangkan kamu **membuat formulir pendaftaran online**:

1. **`tk.Tk()`** = Membuat **halaman kosong** di browser.
2. **`Frame`** = Membuat **section/bagian** di halaman (bagian input data).
3. **`Label`** = **Judul kolom**: "Nama Depan:", "Nama Belakang:".
4. **`Entry`** = **Kolom input** yang bisa diketik user.
5. **`Button`** = Tombol **"Submit"** atau **"Kirim"**.
6. **`StringVar`** = **Variabel tersembunyi** yang menyimpan apa yang diketik user.
7. **`showinfo`** = **Pop-up konfirmasi**: "Data kamu sudah terkirim!"
8. **`mainloop()`** = Halaman **tetap terbuka** sampai kamu tutup tab browser.

---

## Tips untuk Pemula

1. **Jalankan kode di IDE** (VS Code, PyCharm) agar jendela GUI muncul.
2. **Jangan jalankan di terminal** karena tkinter butuh tampilan grafis.
3. **`mainloop()` harus di baris terakhir** kode GUI.
4. Untuk menghentikan program, tutup jendela GUI atau tekan Ctrl+C di terminal.
5. **`ttk` lebih modern** dari `tk` biasa, gunakan `ttk` untuk tampilan lebih bagus.
