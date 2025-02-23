# PYTHON JSON

## **1. Pendahuluan**  
Library `json` dalam Python adalah modul bawaan yang digunakan untuk mengelola data dalam format **JSON (JavaScript Object Notation)**. JSON adalah format pertukaran data yang ringan dan sering digunakan dalam API, database, dan file konfigurasi.  

---

## **2. Cara Menggunakan Library `json`**  
Untuk menggunakan modul `json`, kita perlu mengimpornya terlebih dahulu:  
```python
import json
```

---

# **3. Representasi JSON dalam Python**  
JSON memiliki struktur yang mirip dengan **dictionary** dalam Python. Berikut adalah konversi antara JSON dan Python:

| Tipe Data JSON | Tipe Data Python |
|---------------|----------------|
| `object {}` | `dict {}` |
| `array []` | `list []` |
| `string` | `str` |
| `number (integer, float)` | `int, float` |
| `true, false` | `True, False` |
| `null` | `None` |

---

# **4. Konversi Data Python ke JSON (`json.dumps`)**  
### **4.1. Mengubah Dictionary Python ke JSON**  
```python
import json

data = {
    "nama": "Budi",
    "usia": 25,
    "kota": "Jakarta",
    "hobi": ["membaca", "coding"]
}

json_data = json.dumps(data)
print(json_data)  # Output dalam format JSON
```
#### **Hasil Output:**
```json
{"nama": "Budi", "usia": 25, "kota": "Jakarta", "hobi": ["membaca", "coding"]}
```

### **4.2. Mengubah JSON dengan Format yang Lebih Rapi (`indent`)**  
```python
json_data = json.dumps(data, indent=4)
print(json_data)
```
#### **Hasil Output:**
```json
{
    "nama": "Budi",
    "usia": 25,
    "kota": "Jakarta",
    "hobi": ["membaca", "coding"]
}
```

---

# **5. Konversi JSON ke Python (`json.loads`)**  
### **5.1. Mengubah JSON ke Dictionary Python**  
```python
json_string = '{"nama": "Budi", "usia": 25, "kota": "Jakarta"}'
data_dict = json.loads(json_string)

print(data_dict["nama"])  # Output: Budi
```

---

# **6. Membaca dan Menulis JSON ke File**  
### **6.1. Menyimpan JSON ke File (`json.dump`)**  
```python
with open("data.json", "w") as file:
    json.dump(data, file, indent=4)
```

### **6.2. Membaca JSON dari File (`json.load`)**  
```python
with open("data.json", "r") as file:
    data_from_file = json.load(file)

print(data_from_file)  # Output: {'nama': 'Budi', 'usia': 25, 'kota': 'Jakarta'}
```

---

# **7. Menangani Error pada JSON**  
Jika JSON tidak valid, Python akan menampilkan error. Kita bisa menangani error menggunakan `try-except`.

### **7.1. Menangani Kesalahan Parsing JSON**
```python
json_string = '{"nama": "Budi", "usia": 25, "kota": "Jakarta" '  # JSON tidak valid

try:
    data = json.loads(json_string)
except json.JSONDecodeError as e:
    print(f"Terjadi kesalahan: {e}")
```

---

# **8. Custom Encoder dan Decoder**  
### **8.1. Menggunakan `default` untuk Mengonversi Tipe Data Kustom**  
```python
import json
from datetime import datetime

class CustomEncoder(json.JSONEncoder):
    def default(self, obj):
        if isinstance(obj, datetime):
            return obj.isoformat()
        return super().default(obj)

data = {
    "nama": "Budi",
    "waktu": datetime.now()
}

json_data = json.dumps(data, cls=CustomEncoder, indent=4)
print(json_data)
```

---

# **9. Kesimpulan**  
✅ **`json.dumps()`** → Konversi Python ke JSON  
✅ **`json.loads()`** → Konversi JSON ke Python  
✅ **`json.dump()`** → Menyimpan JSON ke file  
✅ **`json.load()`** → Membaca JSON dari file  
✅ **Handling error** dengan `try-except`  
✅ **Custom Encoder** untuk tipe data khusus  

Library `json` sangat berguna untuk komunikasi antar sistem, API, dan penyimpanan data ringan.
