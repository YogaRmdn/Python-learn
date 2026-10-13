# BAB 8 - Continue dan Pass

## Apa yang Dipelajari

- Statement `continue` untuk melompati iterasi
- Statement `pass` sebagai placeholder (pengisi tempat)
- Perbedaan `break`, `continue`, dan `pass`
- Else pada for loop

---

## Penjelasan Kode

### File: `continue&pass`

#### 1. Setup Loop

```python
for i in range(1, 10):
```

- Loop dari `1` sampai `9`.
- Variabel `i` mengambil nilai: 1, 2, 3, 4, 5, 6, 7, 8, 9.

---

#### 2. Kondisi `if` dengan `pass`

```python
    if i is 6:
        print("nilai i adalah", 6)
        # break : fungsinya untuk mengakhiri for (terminasi)
        # continue : fungsinya untuk melanjutkan ke step berikutnya
        pass
        print("cek bro 1")
```

- Ketika `i == 6`:
  1. `"nilai i adalah 6"` dicetak.
  2. `pass` dijalankan — **tidak melakukan apa-apa**.
  3. `print("cek bro 1")` tetap dicetak (karena `pass` tidak menghentikan eksekusi).

> **Catatan Penting:** Di sini `pass` hanya sebagai placeholder. Secara logika, baris-baris di atasnya menunjukkan perbandingan:
> - **`break`**: Menghentikan loop sepenuhnya.
> - **`continue`**: Melompat ke iterasi berikutnya (lewati sisa kode di loop).
> - **`pass`**: Tidak melakukan apa-apa, lanjut ke baris berikutnya.

---

#### 3. Cetak Nilai Saat Ini

```python
    print('nilai saat ini adalah', i)
```

- Dicetak untuk **setiap** iterasi, termasuk saat `i == 6`.

---

#### 4. Else pada For Loop

```python
else:
    print('akhir dari loop')
```

- Dicetak setelah loop selesai **tanpa `break`**.
- Karena tidak ada `break` di kode ini, `"akhir dari loop"` akan selalu dicetak.

---

#### 5. Print di Luar Loop

```python
print('print diluar loop')
```

- Dicetak setelah seluruh blok for-else selesai.

---

## Ringkasan: Break, Continue, Pass

| Statement | Fungsi | Efek |
|-----------|--------|------|
| `break` | Menghentikan loop | Loop berhenti total, lanjut ke kode setelah loop |
| `continue` | Melompati sisa iterasi | Langsung ke iterasi berikutnya |
| `pass` | Tidak melakukan apa-apa | Lanjut ke baris kode berikutnya |

---

## Alur Program

```
for i in range(1, 10):
│
├── i=1: print("nilai saat ini adalah 1")
├── i=2: print("nilai saat ini adalah 2")
├── i=3: print("nilai saat ini adalah 3")
├── i=4: print("nilai saat ini adalah 4")
├── i=5: print("nilai saat ini adalah 5")
├── i=6:
│     ├── print("nilai i adalah 6")
│     ├── pass (tidak terjadi apa-apa)
│     ├── print("cek bro 1")
│     └── print("nilai saat ini adalah 6")
├── i=7: print("nilai saat ini adalah 7")
├── i=8: print("nilai saat ini adalah 8")
└── i=9: print("nilai saat ini adalah 9")
        │
        ▼
else: print("akhir dari loop")
        │
        ▼
print("print diluar loop")
```

---

## Analogi

Bayangkan kamu sedang **membaca buku** halaman 1 sampai 9:
- **`break`**: Kamu berhenti membaca di halaman 6 dan melempar bukunya. Kamu tidak membaca sisa halaman.
- **`continue`**: Di halaman 6 kamu skip (tidak dibaca), tapi lanjut ke halaman 7, 8, 9.
- **`pass`**: Di halaman 6 kamu melihat-lihat sebentar (tidak melakukan apa-apa khusus), lalu lanjut ke baris berikutnya.

---

## Tips untuk Pemula

- `pass` sering digunakan sebagai **placeholder sementara** saat kode belum ditulis.
- `continue` berguna untuk **melewati** satu iterasi tertentu.
- `break` berguna untuk **menghentikan** loop lebih awal.
- Jangan gunakan `is` untuk membandingkan angka — gunakan `==`.
