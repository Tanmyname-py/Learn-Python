# PYTHON FOR LOOP

## **1. Pendahuluan**  
Looping (perulangan) dalam Python memungkinkan kita untuk menjalankan kode secara berulang tanpa harus menulis ulang. Salah satu bentuk looping yang paling sering digunakan adalah **`for` loop**.  

### **Kegunaan `for` loop:**  
✅ Mengulang item dalam **list, tuple, string, dictionary, dan set**  
✅ Menggunakan **range()** untuk perulangan dengan batas tertentu  
✅ Menggunakan **break** dan **continue** untuk kontrol alur program  
✅ Menggunakan **else dalam for loop**  
✅ Menggunakan **list comprehension** untuk membuat loop yang lebih efisien  

---

# **2. Struktur Dasar `for` Loop**
### **Sintaks `for` loop**
```python
for variable in iterable:
    # Blok kode yang akan diulang
```
- **`variable`** adalah variabel yang akan menyimpan elemen dari `iterable`  
- **`iterable`** adalah objek yang bisa diiterasi, seperti **list, tuple, string, range, atau dictionary**  
- **Blok kode** di dalam loop akan dijalankan berulang kali  

---

## **3. Menggunakan `for` Loop dengan Berbagai Iterable**
### **3.1. `for` Loop dengan List**
```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```
**Output:**
```
apple
banana
cherry
```

### **3.2. `for` Loop dengan Tuple**
```python
numbers = (10, 20, 30)
for num in numbers:
    print(num)
```

### **3.3. `for` Loop dengan String (Mengecek Huruf)**
```python
text = "Python"
for char in text:
    print(char)
```

### **3.4. `for` Loop dengan Dictionary**
```python
student = {"name": "Alice", "age": 20, "grade": "A"}
for key in student:
    print(key, ":", student[key])
```

### **3.5. `for` Loop dengan Set**
```python
unique_numbers = {1, 2, 3, 4, 5}
for num in unique_numbers:
    print(num)
```

---

## **4. `for` Loop dengan `range()`**
`range(start, stop, step)` digunakan untuk perulangan dengan batas tertentu.

### **4.1. Perulangan dengan `range()`**
```python
for i in range(5):  # 0 sampai 4
    print(i)
```
**Output:**  
```
0  
1  
2  
3  
4  
```

### **4.2. `range()` dengan Mulai dan Berhenti**
```python
for i in range(2, 10):  # Mulai dari 2, berhenti sebelum 10
    print(i)
```

### **4.3. `range()` dengan Langkah (`step`)**
```python
for i in range(1, 10, 2):  # Melangkah 2 angka
    print(i)
```
**Output:**
```
1
3
5
7
9
```

---

## **5. `break` dan `continue` dalam `for` Loop**
### **5.1. `break` (Menghentikan Loop)**
```python
for num in range(10):
    if num == 5:
        break  # Menghentikan perulangan saat num = 5
    print(num)
```

**Output:**
```
0  
1  
2  
3  
4  
```

### **5.2. `continue` (Melewati Iterasi Tertentu)**
```python
for num in range(5):
    if num == 2:
        continue  # Melewati angka 2
    print(num)
```

**Output:**
```
0  
1  
3  
4  
```

---

## **6. `else` dalam `for` Loop**
`else` akan dieksekusi **jika perulangan selesai tanpa `break`**.

```python
for i in range(5):
    print(i)
else:
    print("Loop selesai tanpa break!")
```

Tetapi jika ada `break`, `else` tidak akan dieksekusi:

```python
for i in range(5):
    if i == 3:
        break
    print(i)
else:
    print("Loop selesai!")  # Ini tidak akan dijalankan
```

---

## **7. Nested `for` Loop (Perulangan Bersarang)**
```python
for i in range(1, 3):
    for j in range(1, 4):
        print(f"i={i}, j={j}")
```

**Output:**
```
i=1, j=1  
i=1, j=2  
i=1, j=3  
i=2, j=1  
i=2, j=2  
i=2, j=3  
```

---

## **8. `for` Loop dengan List Comprehension (Efisiensi)**
List comprehension adalah cara singkat untuk membuat list menggunakan `for` loop.

```python
numbers = [x for x in range(10) if x % 2 == 0]
print(numbers)  # [0, 2, 4, 6, 8]
```

Contoh lainnya:
```python
squared_numbers = [x**2 for x in range(1, 6)]
print(squared_numbers)  # [1, 4, 9, 16, 25]
```

---

## **9. Menggunakan `enumerate()` untuk Loop dengan Index**
Fungsi `enumerate()` memberikan index sekaligus elemen dalam loop.

```python
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"Index {index}: {fruit}")
```

**Output:**
```
Index 0: apple  
Index 1: banana  
Index 2: cherry  
```

---

## **10. Efisiensi dan Best Practices dalam `for` Loop**
### **10.1. Gunakan `range()` dengan Langkah Optimal**
Jika hanya butuh angka, gunakan `range()` tanpa membuat list:
```python
for i in range(10):  # Lebih efisien daripada list(range(10))
    print(i)
```

### **10.2. Gunakan List Comprehension Jika Bisa**
Lebih efisien dibandingkan loop biasa:
```python
squares = [x**2 for x in range(10)]  # Lebih cepat
```
Daripada:
```python
squares = []
for x in range(10):
    squares.append(x**2)  # Lebih lambat
```

### **10.3. Gunakan `enumerate()` untuk Loop dengan Index**
```python
for index, value in enumerate(my_list):
    print(index, value)
```

---

# **Kesimpulan**
✅ `for` loop digunakan untuk mengulang elemen dalam **list, tuple, string, dictionary, dan set**.  
✅ Bisa menggunakan `range()` untuk membuat perulangan dengan batas tertentu.  
✅ `break` menghentikan loop, `continue` melewati iterasi tertentu.  
✅ `else` dalam `for` loop hanya dieksekusi jika loop selesai **tanpa `break`**.  
✅ `list comprehension` dapat membuat kode lebih efisien.  
✅ Gunakan `enumerate()` jika perlu index dalam loop.  

Dengan memahami `for` loop, kita bisa membuat program Python yang lebih **efektif dan efisien**!
