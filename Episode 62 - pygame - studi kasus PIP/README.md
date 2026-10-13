# BAB 2 - Episode 62: Pygame - Studi Kasus PIP

## Apa yang Dipelajari

- Memasang library **Pygame** menggunakan `pip install pygame`
- Membuat **jendela (window)** game dengan `pygame.display.set_mode()`
- Memahami **game loop** (`while isRun`)
- **Event handling**: menangkap event keluar (tutup jendela)
- **Keyboard input**: mendeteksi tombol panah (arrow keys) untuk bergerak
- Menggambar **persegi panjang** (rectangle) di layar
- Konsep **posisi (x, y)**, **ukuran (lebar, panjang)**, dan **kecepatan (speed)**

---

## Penjelasan Kode

### File: `main_app.py`

### 1. Inisialisasi Pygame

```python
import pygame

pygame.init()
```

- Mengimpor library Pygame dan menjalankan `pygame.init()` untuk **menginisialisasi semua modul** Pygame (grafis, suara, input, dll).
- Tanpa `pygame.init()`, banyak fungsi Pygame tidak akan bekerja.

---

### 2. Variabel Game Loop

```python
isRun = True
```

- Variabel **flag** yang mengontrol apakah game masih berjalan.
- Selama `isRun == True`, game loop akan terus berputar.
- Saat user menekan tombol tutup jendela, `isRun` menjadi `False` → game berhenti.

---

### 3. Membuat Jendela (Window)

```python
window_lebar = 500
window_panjang = 500
window = pygame.display.set_mode((window_lebar, window_panjang))
```

| Variabel | Nilai | Penjelasan |
|---|---|---|
| `window_lebar` | 500 | Lebar jendela dalam piksel (px) |
| `window_panjang` | 500 | Tinggi jendela dalam piksel (px) |
| `window` | objek Surface | Permukaan gambar utama tempat semua elemen digambar |

- `pygame.display.set_mode()` membuat jendela berukuran **500x500 piksel**.

---

### 4. Properti Objek Game (Kotak yang Bisa Bergerak)

```python
x = 250          # Posisi awal sumbu X (horizontal)
y = 250          # Posisi awal sumbu Y (vertikal)

panjang = 20     # Tinggi kotak
lebar = 20       # Lebar kotak

speed = 10       # Kecepatan gerak per frame (piksel)
```

- Kotak dimulai dari **tengah jendela** (250, 250).
- Ukuran kotak: **20x20 piksel** (seperti piksel raksasa).
- Setiap kali tombol panah ditekan, kotak bergerak **10 piksel**.

---

### 5. Game Loop

```python
while isRun:
    pygame.time.delay(10)
```

- Game loop adalah **jantung** dari setiap game. Selama `isRun == True`, loop ini terus berputar.
- `pygame.time.delay(10)` memberi jeda **10 milidetik** per iterasi agar CPU tidak bekerja terlalu keras.

---

### 6. Event Handling — Tombol Tutup Jendela

```python
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            isRun = False
```

- `pygame.event.get()` mengambil **semua event** yang terjadi (klik mouse, tombol keyboard, tutup jendela, dll).
- Jika event yang terjadi adalah `pygame.QUIT` (user menekan tombol **X** di pojok jendela), maka `isRun = False` → loop berhenti → game selesai.

---

### 7. Keyboard Input — Tombol Panah

```python
    keys = pygame.key.get_pressed()

    if keys[pygame.K_LEFT] and x > 0:
        x -= speed

    if keys[pygame.K_RIGHT] and x < window_lebar - lebar:
        x += speed

    if keys[pygame.K_DOWN] and y < window_panjang - panjang:
        y += speed

    if keys[pygame.K_UP] and y > 0:
        y -= speed
```

| Tombol | Aksi | Kondisi Batas |
|---|---|---|
| `K_LEFT` (←) | `x -= 10` (geser kiri) | `x > 0` (tidak keluar layar kiri) |
| `K_RIGHT` (→) | `x += 10` (geser kanan) | `x < 480` (tidak keluar layar kanan) |
| `K_DOWN` (↓) | `y += 10` (geser bawah) | `y < 480` (tidak keluar layar bawah) |
| `K_UP` (↑) | `y -= 10` (geser atas) | `y > 0` (tidak keluar layar atas) |

> **Catatan:** `x > 0` dan `x < window_lebar - lebar` memastikan kotak **tidak keluar dari layar**.

---

### 8. Rendering (Menggambar ke Layar)

```python
    window.fill((255, 255, 255))
    pygame.draw.rect(window, (255, 120, 0), (x, y, lebar, panjang))
    pygame.display.update()
```

| Kode | Penjelasan |
|---|---|
| `window.fill((255,255,255))` | Mengisi seluruh layar dengan **warna putih** (RGB: 255,255,255) |
| `pygame.draw.rect(...)` | Menggambar **persegi panjang** berwarna **oranye** (RGB: 255,120,0) pada posisi (x,y) |
| `pygame.display.update()` | **Memperbarui tampilan** layar agar gambar baru terlihat |

> Penting: `window.fill()` harus dipanggil **setiap frame** untuk menghapus gambar frame sebelumnya. Kalau tidak, jejak kotak sebelumnya akan tertinggal.

---

### 9. Keluar dari Game

```python
pygame.quit()
```

- Dipanggil **setelah** game loop selesai untuk menutup semua modul Pygame dengan rapi.

---

### Alur Program Secara Keseluruhan

```
1. Inisialisasi Pygame
2. Buat jendela 500x500
3. Mulai game loop:
   a. Tunggu 10ms
   b. Cek event (tutup jendela?)
   c. Cek input keyboard (tombol panah)
   d. Update posisi kotak
   e. Bersihkan layar (warna putih)
   f. Gambar kotak di posisi baru
   g. Perbarui tampilan layar
4. Tutup Pygame
```

---

## Analogi

Bayangkan kamu sedang **menggambar animasi di buku sketsa**:

1. **`window.fill(putih)`** = Menghapus seluruh halaman buku sketsa dengan penghapus besar supaya bersih.
2. **`pygame.draw.rect()`** = Menggambar ulang kotak di posisi baru dengan spidol oranye.
3. **`pygame.display.update()`** = Membalik halaman buku supaya orang lain bisa melihat gambarnya.

Proses ini diulang **puluhan kali per detik** (sekitar 100 fps), sehingga mata kita melihatnya sebagai **animasi kotak bergerak** — sama seperti film kartun yang terdiri dari banyak gambar diam yang ditampilkan sangat cepat.

**Keyboard handling** seperti remote TV: kamu tekan tombol panah, dan kotak langsung bergerak ke arah yang kamu inginkan.

---

## Ringkasan Konsep Penting

| Konsep | Kode | Penjelasan |
|---|---|---|
| Install Pygame | `pip install pygame` | Memasang library dari PyPI |
| Inisialisasi | `pygame.init()` | Mengaktifkan semua modul Pygame |
| Membuat jendela | `pygame.display.set_mode((w,h))` | Membuat jendela game |
| Game loop | `while isRun:` | Loop utama yang menjalankan game |
| Delay | `pygame.time.delay(10)` | Jeda per frame (ms) |
| Event handling | `pygame.event.get()` | Menangkap semua event |
| Keyboard input | `pygame.key.get_pressed()` | Mendeteksi tombol yang ditekan |
| Gambar persegi | `pygame.draw.rect(surface, color, rect)` | Menggambar persegi panjang |
| Update layar | `pygame.display.update()` | Memperbarui tampilan |
| Warna RGB | `(255, 255, 255)` | (Merah, Hijau, Biru) — 0-255 |
