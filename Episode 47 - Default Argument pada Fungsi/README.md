# BAB 7 - Default Argument pada Fungsi

## Apa yang Dipelajari

- Memberikan **nilai default** pada parameter fungsi
- Parameter dengan default value bersifat **opsional** saat dipanggil
- Menggabungkan parameter biasa dan default argument
- Keyword argument untuk **melewati parameter tertentu**

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Template Default Argument

```python
# def fungsi(argument):
# def fungsi(argument = nilai defaultnya):
```

- **Tanpa default**: argument wajib diisi saat pemanggilan.
- **Dengan default**: argument boleh tidak diisi, akan pakai nilai default.

#### 2. Contoh 1: Default Argument Sederhana

```python
def say_hello(nama = "Ganteng"):
    '''fungsi dengan default argument'''
    print(f"Hallo {nama}")

say_hello("Ucup")
say_hello()
```

- Parameter `nama` punya default value `"Ganteng"`.
- `say_hello("Ucup")` → parameter diisi `"Ucup"`, output: `Hallo Ucup`
- `say_hello()` → parameter **tidak diisi**, otomatis pakai default `"Ganteng"`, output: `Hallo Ganteng`

#### 3. Contoh 2: Gabungan Parameter Biasa + Default

```python
def sapa_dia(nama, pesan = "Apa kabar?"):
    '''fungsi dengan satu input biasa, dan satu default argument'''
    print(f"hai {nama}, {pesan}")

sapa_dia("Dudung","Hai Ganteeeng")
sapa_dia("Otong")
```

- `nama` = parameter **wajib** (tidak ada default).
- `pesan` = parameter **opsional** (ada default `"Apa kabar?"`).
- `sapa_dia("Dudung","Hai Ganteeeng")` → `hai Dudung, Hai Ganteeeng`
- `sapa_dia("Otong")` → `hai Otong, Apa kabar?`

#### 4. Contoh 3: Default Argument dengan Return

```python
def hitung_pangkat(angka, pangkat=2):
    hasil = angka**pangkat
    return hasil

print(hitung_pangkat(2,4))

hasil = hitung_pangkat(pangkat=3, angka=5)
print(hasil)
```

- `pangkat` punya default `2`.
- `hitung_pangkat(2,4)` → `2**4 = 16` (pangkat di-override jadi 4).
- `hitung_pangkat(pangkat=3, angka=5)` → pakai **keyword argument**, urutan bebas. `5**3 = 125`.

#### 5. Contoh 4: Semua Parameter Default

```python
def fungsi(input1=1,input2=2,input3=3,input4=4):
    hasil = input1 + input2 + input3 + input4
    return hasil

print(fungsi())                    # 1+2+3+4 = 10
print(fungsi(input3=10))           # 1+2+10+4 = 17
```

- `fungsi()` → semua pakai default: `1+2+3+4 = 10`
- `fungsi(input3=10)` → hanya `input3` yang di-override: `1+2+10+4 = 17`

---

## Ringkasan Default Argument

| Pemanggilan              | input1 | input2 | input3 | input4 | Hasil |
|--------------------------|--------|--------|--------|--------|-------|
| `fungsi()`               | 1      | 2      | 3      | 4      | 10    |
| `fungsi(input3=10)`      | 1      | 2      | 10     | 4      | 17    |
| `fungsi(10,20)`          | 10     | 20     | 3      | 4      | 37    |

---

## Analogi

Bayangkan fungsi adalah **mesin kopi**:

- **Parameter wajib** = Kamu **harus** pilih ukuran kopi (S/M/L).
- **Default argument** = Kamu boleh tidak pilih gula, nanti otomatis pakai **"gula standar"** (default).
- Jika mau gula ekstra, tinggal pilih: `kopi(ukuran="M", gula="ekstra")`.

---

## Aturan Default Argument

1. **Parameter default HARUS di belakang** parameter biasa:
   ```python
   # BENAR
   def fungsi(a, b=10): ...

   # SALAH - error!
   def fungsi(a=10, b): ...
   ```

2. **Default value hanya dihitung sekali** saat fungsi didefinisikan, bukan saat dipanggil (hati-hati dengan mutable default).
3. **Override satu default** tanpa mengubah yang lain pakai **keyword argument**.
