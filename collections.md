# PYTHON COLLECTIONS 

## **1. Pendahuluan**  
Modul `collections` dalam Python adalah modul standar yang menyediakan struktur data tambahan di luar tipe data bawaan seperti `list`, `tuple`, `dict`, dan `set`. Struktur data ini dirancang untuk meningkatkan efisiensi dan kemudahan dalam pengolahan data.

---

## **2. Cara Menggunakan Library `collections`**  
Untuk menggunakan modul `collections`, kita perlu mengimpornya terlebih dahulu:  
```python
import collections
```

---

# **3. Struktur Data dalam `collections`**
Berikut adalah struktur data utama dalam `collections`:
1. **`Counter`** → Menghitung elemen dalam iterable  
2. **`defaultdict`** → Dictionary dengan default value  
3. **`OrderedDict`** → Dictionary yang mempertahankan urutan  
4. **`deque`** → List dengan operasi cepat di kedua ujungnya  
5. **`namedtuple`** → Tuple dengan nama untuk setiap elemen  
6. **`ChainMap`** → Gabungan beberapa dictionary  
7. **`UserDict`**, **`UserList`**, **`UserString`** → Versi kustom dari `dict`, `list`, dan `str`  

---

# **4. `Counter`: Menghitung Elemen dalam Iterable**
`Counter` adalah subclass dari `dict` yang digunakan untuk menghitung frekuensi elemen dalam iterable.

### **4.1. Membuat Counter**
```python
from collections import Counter

data = ["apple", "banana", "apple", "orange", "banana", "banana"]
counter = Counter(data)
print(counter)  # Output: Counter({'banana': 3, 'apple': 2, 'orange': 1})
```

### **4.2. Mendapatkan Elemen yang Paling Banyak Muncul**
```python
print(counter.most_common(2))  # Output: [('banana', 3), ('apple', 2)]
```

---

# **5. `defaultdict`: Dictionary dengan Default Value**
`defaultdict` adalah dictionary yang menghindari `KeyError` dengan memberikan nilai default untuk kunci yang belum ada.

### **5.1. Membuat `defaultdict` dengan Default Tipe Data**
```python
from collections import defaultdict

dd = defaultdict(int)  # Default value = 0
dd["apple"] += 1
print(dd["apple"])  # Output: 1
print(dd["banana"])  # Output: 0 (karena default int adalah 0)
```

### **5.2. Menggunakan `defaultdict` dengan List**
```python
dd = defaultdict(list)
dd["buah"].append("apple")
dd["buah"].append("banana")
print(dd["buah"])  # Output: ['apple', 'banana']
```

---

# **6. `OrderedDict`: Dictionary dengan Urutan Terjaga**
Sebelum Python 3.7, dictionary bawaan (`dict`) tidak mempertahankan urutan elemen. `OrderedDict` memastikan bahwa urutan elemen tetap terjaga.

### **6.1. Membuat `OrderedDict`**
```python
from collections import OrderedDict

od = OrderedDict()
od["a"] = 1
od["b"] = 2
od["c"] = 3

print(od)  # Output: OrderedDict([('a', 1), ('b', 2), ('c', 3)])
```

---

# **7. `deque`: Struktur Data Double-Ended Queue**
`deque` adalah list yang lebih cepat untuk operasi di kedua ujungnya dibandingkan dengan `list`.

### **7.1. Membuat `deque`**
```python
from collections import deque

dq = deque(["a", "b", "c"])
print(dq)  # Output: deque(['a', 'b', 'c'])
```

### **7.2. Operasi pada `deque`**
```python
dq.append("d")  # Menambah di akhir
dq.appendleft("z")  # Menambah di awal
print(dq)  # Output: deque(['z', 'a', 'b', 'c', 'd'])

dq.pop()  # Menghapus dari akhir
dq.popleft()  # Menghapus dari awal
print(dq)  # Output: deque(['a', 'b', 'c'])
```

---

# **8. `namedtuple`: Tuple dengan Nama untuk Setiap Elemen**
`namedtuple` adalah subclass dari `tuple` yang memungkinkan akses elemen dengan nama.

### **8.1. Membuat `namedtuple`**
```python
from collections import namedtuple

Point = namedtuple("Point", ["x", "y"])
p = Point(10, 20)
print(p.x, p.y)  # Output: 10 20
```

### **8.2. Menggunakan `namedtuple` seperti Dictionary**
```python
print(p._asdict())  # Output: {'x': 10, 'y': 20}
```

---

# **9. `ChainMap`: Gabungan Beberapa Dictionary**
`ChainMap` memungkinkan penggabungan beberapa dictionary menjadi satu tampilan.

### **9.1. Membuat `ChainMap`**
```python
from collections import ChainMap

dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}
cm = ChainMap(dict1, dict2)

print(cm["b"])  # Output: 2 (mengambil dari dict1)
print(cm["c"])  # Output: 4 (mengambil dari dict2)
```

---

# **10. `UserDict`, `UserList`, dan `UserString`: Versi Kustom dari `dict`, `list`, dan `str`**
Modul `collections` menyediakan **`UserDict`**, **`UserList`**, dan **`UserString`** yang memungkinkan kita membuat subclass dengan perilaku kustom.

### **10.1. Membuat `UserDict`**
```python
from collections import UserDict

class MyDict(UserDict):
    def __setitem__(self, key, value):
        if not isinstance(value, int):
            raise ValueError("Hanya bisa menyimpan angka!")
        super().__setitem__(key, value)

d = MyDict()
d["a"] = 100  # Berhasil
# d["b"] = "hello"  # Akan error: ValueError
```

---

# **11. Kesimpulan**
✅ **`Counter`** → Menghitung elemen dalam iterable  
✅ **`defaultdict`** → Dictionary dengan nilai default otomatis  
✅ **`OrderedDict`** → Dictionary dengan urutan yang terjaga  
✅ **`deque`** → List yang cepat untuk operasi di kedua ujungnya  
✅ **`namedtuple`** → Tuple dengan nama untuk setiap elemen  
✅ **`ChainMap`** → Gabungan beberapa dictionary  
✅ **`UserDict`, `UserList`, `UserString`** → Versi kustom dari dictionary, list, dan string  

Modul `collections` sangat berguna dalam **pemrosesan data yang lebih efisien**, **penggunaan dictionary yang lebih fleksibel**, dan **struktur data yang lebih optimal** dalam pemrograman Python!
