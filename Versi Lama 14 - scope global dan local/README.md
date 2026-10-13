# BAB 2 - Versi Lama 14: Scope Variable (Global dan Local)

## Apa yang Dipelajari

- Perbedaan **variabel global** dan **variabel local**
- Bagaimana Python menentukan **scope** (jangkauan) sebuah variabel
- Menggunakan kata kunci **`global`** untuk mengubah variabel global dari dalam fungsi

---

## Penjelasan Kode

### File: `scope.py`

#### 1. Deklarasi Variabel Global

```python
namaKucing = 'cassandra'
makananKucing = 'royal canin'
```

Variabel ini didefinisikan **di luar fungsi**, sehingga merupakan **variabel global**. Artinya, variabel ini bisa diakses dari **mana saja** dalam file — baik di luar maupun di dalam fungsi.

#### 2. Fungsi `rubahNamaKucing` — Penggunaan `global`

```python
def rubahNamaKucing(namaBaru):
    global namaKucing          # ← Mengambil variabel global
    namaKucing = namaBaru      # ← Mengubah variabel global
    nama = namaBaru            # ← Ini variabel LOCAL (hanya ada di dalam fungsi)
    print('saya rubah nama kucing menjadi', namaKucing)
```

| Elemen | Penjelasan |
|--------|------------|
| `global namaKucing` | Memberitahu Python: "variabel `namaKucing` ini adalah yang **global**, bukan yang baru" |
| `namaKucing = namaBaru` | Mengubah nilai variabel global `namaKucing` |
| `nama = namaBaru` | Membuat variabel **lokal baru** bernama `nama`. Variabel ini **tidak bisa diakses** di luar fungsi |

#### 3. Fungsi `kasihMakanKucing` — Mengubah Dua Variabel Global

```python
def kasihMakanKucing(makanan, nama):
    global namaKucing, makananKucing
    namaKucing = nama
    makananKucing = makanan
```

Fungsi ini mengubah **dua variabel global** sekaligus: `namaKucing` dan `makananKucing`.

#### 4. Pemanggilan Fungsi

```python
rubahNamaKucing('ketie')
# Output: saya rubah nama kucing menjadi ketie

kasihMakanKucing('universal', 'alex')
# Output: nama kucing saya menjadi alex dan makan universal
```

Setelah pemanggilan terakhir, `namaKucing` berubah menjadi `'alex'` dan `makananKucing` berubah menjadi `'universal'`.

---

## Ringkasan Scope

| Jenis Scope | Didefinisikan di | Bisa diakses dari |
|-------------|-----------------|-------------------|
| **Global** | Di luar semua fungsi | Di mana saja (termasuk dalam fungsi) |
| **Local** | Di dalam fungsi | **Hanya** di dalam fungsi itu sendiri |

### Aturan Penting

```
┌─────────────────────────────────────────────┐
│            GLOBAL SCOPE                     │
│  namaKucing = 'cassandra'                   │
│  makananKucing = 'royal canin'              │
│                                             │
│  ┌─────────────────────────────────────┐    │
│  │        LOCAL SCOPE                  │    │
│  │  (di dalam fungsi)                  │    │
│  │                                     │    │
│  │  tanpa 'global' → baca global, tapi │    │
│  │  menulis = membuat baru (local)     │    │
│  │                                     │    │
│  │  dengan 'global' → bisa menulis     │    │
│  │  dan mengubah variabel global       │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
```

---

## Analogi

Bayangkan sebuah **rumah besar**:

- **Variabel Global** = **Nama keluarga** yang tertulis di pintu depan rumah. Semua orang (di dalam dan luar rumah) bisa melihatnya. Siapa pun bisa menggantinya kalau tahu cara menggantinya (pakai `global`).

- **Variabel Local** = **Nama panggilan** yang kamu berikan ke temanmu saat kalian berdua di kamar. Nama itu hanya kalian berdua yang tahu. Orang di ruang tamu tidak tahu nama panggilan itu.

- **Kata kunci `global`** = Seperti kamu **mengambil spidol raksasa** dan menuliskan nama baru di pintu depan rumah, sehingga semua orang di rumah melihat nama baru itu. Tanpa spidol itu, kamu hanya bisa mengubah nama di dalam kamar sendiri (lokal).
