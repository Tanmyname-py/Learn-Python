# PYTHON ITERTOOLS 

## **1. Pendahuluan**  
Library `itertools` dalam Python adalah modul bawaan yang menyediakan fungsi untuk bekerja dengan **iterasi** secara efisien. Modul ini memungkinkan kita untuk membuat kombinasi, permutasi, mengelola pengulangan, dan mengolah data secara efisien tanpa perlu membuat list besar di memori.

✅ **Kelebihan `itertools`:**  
✔ Efisien dalam penggunaan memori  
✔ Dapat menangani perulangan besar  
✔ Cocok untuk kombinasi dan permutasi  

Untuk menggunakan `itertools`, kita perlu mengimpornya terlebih dahulu:  
```python
import itertools
```

---

# **2. Fungsi Dasar dalam `itertools`**  
## **2.1. `count()` – Perulangan Tak Terbatas**  
Digunakan untuk membuat iterasi angka yang terus bertambah.
```python
import itertools

for i in itertools.count(10, 2):  # Mulai dari 10, naik 2 setiap langkah
    print(i)
    if i >= 20:
        break
```
**Output:**  
```
10  
12  
14  
16  
18  
20  
```

---

## **2.2. `cycle()` – Mengulang Elemen Secara Tak Terbatas**  
Digunakan untuk mengulang elemen dalam iterable tanpa henti.
```python
colors = ["red", "blue", "green"]
counter = 0
for color in itertools.cycle(colors):
    print(color)
    counter += 1
    if counter == 6:
        break
```
**Output:**  
```
red  
blue  
green  
red  
blue  
green  
```

---

## **2.3. `repeat()` – Mengulang Elemen Secara Terbatas**  
```python
for item in itertools.repeat("Python", 3):
    print(item)
```
**Output:**  
```
Python  
Python  
Python  
```

---

# **3. Kombinasi dan Permutasi**
## **3.1. `permutations()` – Menghasilkan Semua Urutan yang Mungkin**
Digunakan untuk membuat semua kemungkinan urutan dari iterable.  
```python
data = ['A', 'B', 'C']
permutasi = itertools.permutations(data)
for p in permutasi:
    print(p)
```
**Output:**  
```
('A', 'B', 'C')  
('A', 'C', 'B')  
('B', 'A', 'C')  
('B', 'C', 'A')  
('C', 'A', 'B')  
('C', 'B', 'A')  
```

---

## **3.2. `combinations()` – Kombinasi Tanpa Urutan**
Menghasilkan semua kombinasi tanpa memperhatikan urutan elemen.  
```python
data = ['A', 'B', 'C']
kombinasi = itertools.combinations(data, 2)
for c in kombinasi:
    print(c)
```
**Output:**  
```
('A', 'B')  
('A', 'C')  
('B', 'C')  
```

---

## **3.3. `combinations_with_replacement()` – Kombinasi dengan Pengulangan**
Menghasilkan kombinasi dengan pengulangan elemen yang sama.  
```python
data = ['A', 'B', 'C']
kombinasi = itertools.combinations_with_replacement(data, 2)
for c in kombinasi:
    print(c)
```
**Output:**  
```
('A', 'A')  
('A', 'B')  
('A', 'C')  
('B', 'B')  
('B', 'C')  
('C', 'C')  
```

---

# **4. Manipulasi Data**
## **4.1. `chain()` – Menggabungkan Beberapa Iterable**
```python
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']
gabung = itertools.chain(list1, list2)

print(list(gabung))
```
**Output:**  
```
[1, 2, 3, 'a', 'b', 'c']
```

---

## **4.2. `islice()` – Memotong Iterasi**
```python
angka = itertools.count(10, 2)
hasil = itertools.islice(angka, 5)

print(list(hasil))
```
**Output:**  
```
[10, 12, 14, 16, 18]
```

---

## **4.3. `starmap()` – Menggunakan Fungsi dengan Tuple**
```python
import operator

data = [(2, 3), (4, 5), (6, 7)]
hasil = itertools.starmap(operator.mul, data)

print(list(hasil))
```
**Output:**  
```
[6, 20, 42]
```

---

## **5. Filter Data**
## **5.1. `dropwhile()` – Membuang Elemen Selama Kondisi Benar**
```python
data = [1, 3, 5, 7, 9, 2, 4, 6]
hasil = itertools.dropwhile(lambda x: x < 5, data)

print(list(hasil))
```
**Output:**  
```
[5, 7, 9, 2, 4, 6]
```

---

## **5.2. `takewhile()` – Mengambil Elemen Selama Kondisi Benar**
```python
hasil = itertools.takewhile(lambda x: x < 5, data)

print(list(hasil))
```
**Output:**  
```
[1, 3]
```

---

## **6. Grouping dan Pengulangan**
## **6.1. `groupby()` – Mengelompokkan Data**
```python
data = [
    {'name': 'Alice', 'age': 25},
    {'name': 'Bob', 'age': 25},
    {'name': 'Charlie', 'age': 30},
    {'name': 'David', 'age': 30}
]

data.sort(key=lambda x: x['age'])
grup = itertools.groupby(data, key=lambda x: x['age'])

for k, v in grup:
    print(f"Age {k}: {list(v)}")
```
**Output:**  
```
Age 25: [{'name': 'Alice', 'age': 25}, {'name': 'Bob', 'age': 25}]  
Age 30: [{'name': 'Charlie', 'age': 30}, {'name': 'David', 'age': 30}]  
```

---

# **7. Kesimpulan**
✅ `itertools.count()` → Perulangan angka tanpa batas  
✅ `itertools.cycle()` → Mengulang iterable tanpa batas  
✅ `itertools.permutations()` → Membuat semua urutan kemungkinan  
✅ `itertools.combinations()` → Menghasilkan kombinasi unik  
✅ `itertools.chain()` → Menggabungkan iterable  
✅ `itertools.groupby()` → Mengelompokkan data  

Modul `itertools` sangat berguna untuk **pengolahan data, optimasi algoritma, dan manipulasi iterasi yang kompleks**!
