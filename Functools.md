# PYTHON FUNCTOOLS 

## **1. Pendahuluan**  
Modul `functools` adalah modul bawaan Python yang menyediakan fungsi-fungsi untuk memanipulasi fungsi lain. Modul ini sering digunakan dalam pemrograman fungsional untuk optimasi, memoization (caching), pengurangan parameter fungsi, dan dekorator.  

---

## **2. Cara Menggunakan Library `functools`**  
Untuk menggunakan `functools`, kita harus mengimpornya terlebih dahulu:  
```python
import functools
```

---

# **3. Fungsi-Fungsi dalam `functools`**

## **3.1. `functools.reduce()` – Mengurangi Data Secara Iteratif**  
Fungsi ini digunakan untuk menerapkan fungsi ke elemen-elemen dalam iterable secara kumulatif.  

### **3.1.1. Contoh: Menghitung Faktorial dengan `reduce()`**
```python
import functools

numbers = [1, 2, 3, 4, 5]
result = functools.reduce(lambda x, y: x * y, numbers)
print(result)  # Output: 120 (1*2*3*4*5)
```

---

## **3.2. `functools.lru_cache()` – Caching untuk Optimasi**  
Fungsi ini digunakan untuk menyimpan hasil pemanggilan fungsi agar tidak dihitung ulang.  

### **3.2.1. Contoh: Menggunakan Cache untuk Fungsi Rekursif**
```python
import functools

@functools.lru_cache(maxsize=128)  # Menyimpan hasil untuk 128 panggilan terakhir
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)

print(fibonacci(10))  # Output: 55
```
Tanpa `lru_cache()`, program akan melakukan banyak perhitungan ulang.

---

## **3.3. `functools.partial()` – Membuat Fungsi dengan Parameter yang Dikunci**  
Fungsi ini memungkinkan kita untuk membuat versi baru dari fungsi dengan beberapa parameter yang telah ditentukan sebelumnya.  

### **3.3.1. Contoh: Mengunci Satu Parameter dalam Fungsi**
```python
import functools

def pangkat(x, y):
    return x ** y

kuadrat = functools.partial(pangkat, y=2)
print(kuadrat(5))  # Output: 25 (5^2)
```
Di sini, kita membuat fungsi `kuadrat()` dari fungsi `pangkat()` dengan `y=2` yang sudah dikunci.

---

## **3.4. `functools.singledispatch()` – Overloading Fungsi Berdasarkan Tipe Parameter**  
Fungsi ini memungkinkan kita untuk membuat fungsi yang berperilaku berbeda berdasarkan tipe data yang diterima.

### **3.4.1. Contoh: Menggunakan `singledispatch`**
```python
import functools

@functools.singledispatch
def proses(data):
    raise NotImplementedError("Tipe data tidak didukung")

@proses.register(str)
def _(data):
    return data.upper()

@proses.register(list)
def _(data):
    return [x * 2 for x in data]

print(proses("hello"))  # Output: HELLO
print(proses([1, 2, 3]))  # Output: [2, 4, 6]
```

---

## **3.5. `functools.wraps()` – Membuat Dekorator yang Menjaga Metadata**  
Fungsi ini digunakan untuk membuat dekorator yang tidak mengubah metadata asli dari fungsi yang dihias.

### **3.5.1. Contoh: Membuat Dekorator dengan `wraps()`**
```python
import functools

def log_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Memanggil {func.__name__} dengan {args} {kwargs}")
        return func(*args, **kwargs)
    return wrapper

@log_decorator
def tambah(a, b):
    return a + b

print(tambah(3, 4))  # Output: Memanggil tambah dengan (3, 4) {}
                      #         7
```
Tanpa `wraps()`, fungsi `tambah.__name__` akan berubah menjadi `wrapper`.

---

## **3.6. `functools.total_ordering()` – Membantu Implementasi Operator Perbandingan**  
Fungsi ini memungkinkan kita untuk hanya mendefinisikan satu atau dua metode perbandingan dalam kelas, dan sisanya akan otomatis dibuat.

### **3.6.1. Contoh: Menggunakan `total_ordering`**
```python
import functools

@functools.total_ordering
class Kotak:
    def __init__(self, ukuran):
        self.ukuran = ukuran

    def __eq__(self, other):
        return self.ukuran == other.ukuran

    def __lt__(self, other):
        return self.ukuran < other.ukuran

kotak1 = Kotak(5)
kotak2 = Kotak(10)

print(kotak1 < kotak2)  # Output: True
print(kotak1 >= kotak2)  # Output: False
```
Tanpa `total_ordering()`, kita harus menulis semua operator perbandingan secara manual.

---

## **3.7. `functools.cmp_to_key()` – Menggunakan Fungsi Lama untuk Sorting**  
Fungsi ini berguna untuk menggunakan fungsi perbandingan lama (dengan return `-1`, `0`, `1`) dalam `sorted()`.

### **3.7.1. Contoh: Sorting dengan `cmp_to_key`**
```python
import functools

def bandingkan(a, b):
    return (a > b) - (a < b)  # Mengembalikan -1, 0, atau 1

angka = [3, 1, 4, 1, 5, 9]
sorted_angka = sorted(angka, key=functools.cmp_to_key(bandingkan))
print(sorted_angka)  # Output: [1, 1, 3, 4, 5, 9]
```

---

# **4. Kesimpulan**  
Modul `functools` adalah alat yang sangat berguna dalam pemrograman fungsional dan optimasi kode Python.  

| Fungsi | Kegunaan |
|--------|---------|
| `reduce()` | Mengurangi iterable dengan operasi kumulatif |
| `lru_cache()` | Menyimpan hasil fungsi untuk mempercepat eksekusi |
| `partial()` | Membuat fungsi baru dengan beberapa parameter yang dikunci |
| `singledispatch()` | Mengizinkan overloading fungsi berdasarkan tipe data |
| `wraps()` | Menjaga metadata fungsi yang dihias dengan dekorator |
| `total_ordering()` | Membantu implementasi operator perbandingan dalam kelas |
| `cmp_to_key()` | Memungkinkan sorting menggunakan fungsi perbandingan lama |

Menguasai `functools` akan sangat membantu dalam menulis kode yang lebih efisien, modular, dan mudah digunakan kembali!
