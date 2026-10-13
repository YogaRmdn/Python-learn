# BAB 2 - Elif Statement

## Apa yang Dipelajari

- Perintah `elif` (else if) untuk menambah kondisi tambahan
- Cara membuat percabangan dengan lebih dari 2 opsi
- Urutan evaluasi kondisi dari atas ke bawah
- Blok `else` sebagai penangkap semua kondisi yang tidak terpenuhi

---

## Penjelasan Kode

### Membaca Input

```python
nama = input("Nama kamyu siapa? ")
```

Variabel `nama` menyimpan input dari pengguna.

---

### Percabangan If - Elif - Else

```python
if nama == "ucup":
	print("Hai ganteeeeng beuds!")
elif nama == "otong":
	print("Hai si kece bangeeeets!!")
elif nama == "mario":
	print("Hai humooooreeeesh!")
else:
	print("au ah gak kenal!!!")
```

| Baris | Penjelasan |
|---|---|
| `if nama == "ucup":` | Kondisi pertama: cek apakah nama adalah `"ucup"` |
| `elif nama == "otong":` | Kondisi kedua: cek apakah nama adalah `"otong"` |
| `elif nama == "mario":` | Ketiga: cek apakah nama adalah `"mario"` |
| `else:` | Jika tidak ada kondisi di atas yang terpenuhi, jalankan ini |

**Cara Kerja:**

1. Python mengecek kondisi dari **atas ke bawah**
2. Jika kondisi pertama `True`, aksi pertama dijalankan → sisanya **dilewati**
3. Jika kondisi pertama `False`, Python lanjut ke kondisi berikutnya
4. Jika semua kondisi `False`, blok `else` yang dijalankan

```
Input nama
    |
    v
nama == "ucup"? ----YES----> cetak "Hai ganteeeeng"
    | NO
    v
nama == "otong"? ---YES----> cetak "Hai si kece"
    | NO
    v
nama == "mario"? ---YES----> cetak "Hai humooresh"
    | NO
    v
else (tidak dikenal)
```

---

### Menjalankan Kode Setelah Percabangan

```python
print("ini adalah akhir dari program")
```

Baris ini **selalu dijalankan** karena berada di luar blok percabangan.

---

## Analogi

Bayangkan kamu memilih makanan di kantin:

- **If**: "Jika pesananmu **nasi goreng**, ambil di meja 1."
- **Elif**: "Kalau tidak, jika **mie ayam**, ambil di meja 2."
- **Elif**: "Kalau tidak, jika **bakso**, ambil di meja 3."
- **Else**: "Kalau tidak ada pilihan di atas, pilih sendiri dari etalase!"

Hanya **satu** aksi yang dijalankan, bukan semua.

---

## Tips

- Jumlah `elif` **tidak dibatasi** — bisa ditambah sebanyak yang kamu mau.
- `else` bersifat **opsional** (boleh tidak ada), tetapi disarankan untuk menangkap kondisi tak terduga.
- Urutan `elif` penting: Python berhenti di kondisi pertama yang bernilai `True`.
