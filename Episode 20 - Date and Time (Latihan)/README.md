# BAB 19 - Date and Time (Latihan)

## Apa yang Dipelajari

- Modul `datetime` dalam Python
- Membuat objek tanggal: `datetime.date()`
- Mendapatkan tanggal hari ini: `date.today()`
- Selisih tanggal menggunakan `timedelta`
- Format tanggal dengan `strftime()`

## Penjelasan Kode

```python
# Date and time (latihan)

import datetime as dt

print("Silahkan masukan tanggal, \nbulan dan tahun lahir anda \n")
tanggal = int(input("Tanggal \t: "))
bulan = int(input("Bulan \t\t: "))
tahun = int(input("Tahun \t\t: "))
```

- `import datetime as dt` → Mengimpor modul `datetime` dengan alias `dt`.
- Program meminta user memasukkan **tanggal, bulan, dan tahun lahir**.
- `int(input(...))` → Mengubah input string menjadi integer.

---

### Membuat Objek Tanggal

```python
tanggal_lahir = dt.date(tahun, bulan, tanggal)
print(f"Tanggal lahir anda adalah : {tanggal_lahir}")
```
- `dt.date(tahun, bulan, tanggal)` → Membuat objek tanggal.
- Parameter harus dalam urutan: **tahun, bulan, tanggal** (bukan tanggal, bulan, tahun).
- Contoh: `dt.date(2005, 6, 15)` → `2005-06-15`

---

### Mendapatkan Tanggal Hari Ini

```python
hari_ini = dt.date.today()
print(f"Hari ini tanggal: {hari_ini}")
```
- `dt.date.today()` → Mengembalikan **tanggal hari ini** dalam format `YYYY-MM-DD`.

---

### Menghitung Selisih Hari (Timedelta)

```python
umur_hari = hari_ini - tanggal_lahir
umur_tahun = umur_hari.days // 365
umur_bulan_sisa = (umur_hari.days % 365) // 30

print(f"Hari nya adalah : {tanggal_lahir:%A}")
print(f"Umur anda adalah: {umur_tahun} tahun, {umur_bulan_sisa} bulan")
```

**Penjelasan:**
- `hari_ini - tanggal_lahir` → Menghasilkan **objek timedelta** (selisih waktu).
- `umur_hari.days` → Jumlah **total hari** dari selisih.
- `umur_hari.days // 365` → Menghitung **umur dalam tahun** (dibulatkan ke bawah).
- `(umur_hari.days % 365) // 30` → Sisa hari setelah dikurangi tahun penuh, dibagi 30 untuk mendapatkan **sisa bulan**.
- `{tanggal_lahir:%A}` → Menampilkan **nama hari** (Senin, Selasa, dst.).

---

### Contoh Output

```
Silahkan masukan tanggal, 
bulan dan tahun lahir anda 

Tanggal 	: 15
Bulan 		: 6
Tahun 		: 2005
Tanggal lahir anda adalah : 2005-06-15
Hari ini tanggal: 2026-09-06
Hari nya adalah : Wednesday
Umur anda adalah: 21 tahun, 2 bulan
```

## Fungsi Penting `datetime`

| Fungsi | Keterangan | Contoh |
|--------|------------|--------|
| `dt.date(y, m, d)` | Membuat objek tanggal | `dt.date(2005, 6, 15)` |
| `dt.date.today()` | Tanggal hari ini | `dt.date.today()` |
| `hari_ini - tgl_lahir` | Selisih hari (timedelta) | `timedelta(days=7762)` |
| `.days` | Total hari dari timedelta | `7762` |
| `%A` | Nama hari lengkap | `"Wednesday"` |
| `%a` | Nama hari singkat | `"Wed"` |
| `%d` | Tanggal (01-31) | `"15"` |
| `%m` | Bulan (01-12) | `"06"` |
| `%Y` | Tahun 4 digit | `"2005"` |
| `%B` | Nama bulan lengkap | `"June"` |
| `%b` | Nama bulan singkat | `"Jun"` |

## Analogi

Bayangkan ini seperti **mesin waktu sederhana**:
1. **`dt.date(2005, 6, 15)`** = Kamu menyetel mesin waktu ke tanggal lahir kamu.
2. **`dt.date.today()`** = Mesin waktu menunjukkan tanggal **hari ini**.
3. **`hari_ini - tanggal_lahir`** = Mesin waktu **menghitung selisih** antara sekarang dan waktu lahir → berapa hari sudah berlalu.
4. **`umur_hari.days // 365`** = Mengubah jumlah hari menjadi **tahun** (365 hari = 1 tahun).
5. **`%A`** = Mesin waktu juga bisa memberitahu **nama hari** di tanggal lahir kamu.

## File dalam Folder Ini

| File | Keterangan |
|------|------------|
| `Main.py` | File utama, latihan date and time |
