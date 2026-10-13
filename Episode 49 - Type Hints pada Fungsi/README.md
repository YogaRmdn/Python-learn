# BAB 9 - Type Hints pada Fungsi

## Apa yang Dipelajari

- **Type hints** (anotasi tipe): cara memberi petunjuk tipe data pada fungsi
- Anotasi **parameter**: `argument: int`
- Anotasi **return type**: `-> int`
- Kenapa type hints penting untuk kode yang rapi
- Type hints **tidak memaksa** Python, hanya petunjuk

---

## Penjelasan Kode

### File: `main_app.py`

#### 1. Masalah Tanpa Type Hints

```python
# studi kasus
def fungsi(parameter):
    hasil = parameter**2
    print(hasil)

fungsi(1)      # parameter = 1 (int) → OK
fungsi("Ucup") # parameter = "Ucup" (string) → apa yang terjadi?
fungsi(True)   # parameter = True (bool) → apa yang terjadi?
```

- Tanpa type hints, fungsi bisa menerima **tipe data apapun**.
- Python **tidak melarang** fungsi dipanggil dengan tipe data yang salah.
- Ini bisa menyebabkan **bug** yang sulit ditemukan.

#### 2. Type Hints pada Parameter

```python
def sepuluh_pangkat(argument:int) -> int:
    '''FUNGSI DENGAN HINTS'''
    output = 10**argument
    return output

HASIL = sepuluh_pangkat(4)
print(HASIL)
```

- **`argument:int`** → menunjukkan bahwa parameter `argument` diharapkan bertipe **integer**.
- **`-> int`** → menunjukkan bahwa fungsi ini mengembalikan nilai bertipe **integer**.
- `sepuluh_pangkat(4)` → `10**4 = 10000`
- Output: `10000`

> **Catatan penting**: Type hints **tidak memaksa** Python. Jika kamu tetap memanggil `sepuluh_pangkat("hello")`, Python tetap akan menjalankan (dan kemungkinan error di运行时).

#### 3. Type Hints dengan string (module)

```python
import string

def display(argument:string):
    print(argument)

display("Ucup")
```

- **Catatan**: Sebenarnya tipe yang benar untuk string di type hints adalah `str`, bukan `string`.
- `string` adalah module Python, tapi dalam kode ini digunakan sebagai type hint (tidak standar tapi bisa jalan karena type hints tidak dipaksa oleh Python).
- Cara yang lebih benar: `def display(argument: str):`

---

## Jenis-jenis Type Hints

| Tipe Data      | Type Hint | Contoh                |
|----------------|-----------|------------------------|
| Integer        | `int`     | `argument: int`        |
| Float          | `float`   | `argument: float`      |
| String         | `str`     | `argument: str`        |
| Boolean        | `bool`    | `argument: bool`       |
| List           | `list`    | `argument: list`       |
| Dictionary     | `dict`    | `argument: dict`       |
| None (tidak return) | `None` | `-> None`           |

---

## Analogi

Bayangkan type hints seperti **label pada wadah**:

- **Tanpa label**: Kamu tidak tahu wadah ini berisi air atau minyak. Bisa tumpah kalau salah buka.
- **Dengan label**: Wadah bertulis "Air Minum" → kamu tahu isinya air, bisa minum dengan aman.
- **Type hints** = label yang membantu programmer (dan tool seperti IDE) memahami data apa yang masuk dan keluar fungsi.

---

## Kenapa Type Hints Penting?

1. **Membaca kode lebih mudah**: Programmer lain langsung tahu parameter harus tipe apa.
2. **IDE mendeteksi error**: IDE seperti VS Code bisa memberi **peringatan** jika tipe data salah.
3. **Dokumentasi hidup**: Type hints berfungsi sebagai dokumentasi yang selalu up-to-date.
4. **Debugger lebih cepat**: Error lebih cepat ditemukan karena tipe data jelas.

---

## Kesalahan Umum Pemula

- **Type hints bukan aturan**: Python tidak akan error jika kamu mengabaikan type hints.
- **Membingungkan `string` module dengan tipe `str`**: Type hint yang benar untuk string adalah `str`.
- **Tidak konsisten**: Menulis type hints di beberapa fungsi tapi tidak di fungsi lain.
