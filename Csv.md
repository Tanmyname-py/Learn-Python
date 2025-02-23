# PYTHON CSV

## **1. Pendahuluan**  
Library `csv` dalam Python adalah modul bawaan yang digunakan untuk membaca dan menulis file **CSV (Comma-Separated Values)**. Format CSV banyak digunakan untuk menyimpan data dalam bentuk tabel yang dapat dibuka dengan **Excel, Google Sheets, atau database**.  

---

## **2. Cara Menggunakan Library `csv`**  
Untuk menggunakan modul `csv`, kita perlu mengimpornya terlebih dahulu:  
```python
import csv
```

---

# **3. Membaca File CSV (`csv.reader`)**  
Fungsi `csv.reader()` digunakan untuk membaca file CSV dan mengubahnya menjadi **list of lists**.

### **3.1. Membaca File CSV dengan Default Separator (`,`)**
Contoh file **`data.csv`**:  
```
Nama,Usia,Kota
Budi,25,Jakarta
Siti,30,Surabaya
Joko,27,Bandung
```

Kode untuk membaca file:
```python
import csv

with open("data.csv", mode="r", newline="") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```
#### **Output:**
```python
['Nama', 'Usia', 'Kota']
['Budi', '25', 'Jakarta']
['Siti', '30', 'Surabaya']
['Joko', '27', 'Bandung']
```

### **3.2. Membaca File CSV Tanpa Header**
```python
with open("data.csv", mode="r", newline="") as file:
    reader = csv.reader(file)
    next(reader)  # Lewati baris pertama (header)
    for row in reader:
        print(row)
```

---

# **4. Membaca File CSV dengan `csv.DictReader`**  
`DictReader` mengubah setiap baris dalam file CSV menjadi dictionary dengan **key dari header**.

```python
with open("data.csv", mode="r", newline="") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row)
```

#### **Output:**
```python
{'Nama': 'Budi', 'Usia': '25', 'Kota': 'Jakarta'}
{'Nama': 'Siti', 'Usia': '30', 'Kota': 'Surabaya'}
{'Nama': 'Joko', 'Usia': '27', 'Kota': 'Bandung'}
```

---

# **5. Menulis File CSV (`csv.writer`)**  
### **5.1. Menulis CSV dari List**  
```python
data = [
    ["Nama", "Usia", "Kota"],
    ["Budi", 25, "Jakarta"],
    ["Siti", 30, "Surabaya"],
    ["Joko", 27, "Bandung"]
]

with open("output.csv", mode="w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)
```

### **5.2. Menulis CSV dari Dictionary (`csv.DictWriter`)**  
```python
data = [
    {"Nama": "Budi", "Usia": 25, "Kota": "Jakarta"},
    {"Nama": "Siti", "Usia": 30, "Kota": "Surabaya"},
    {"Nama": "Joko", "Usia": 27, "Kota": "Bandung"}
]

with open("output.csv", mode="w", newline="") as file:
    fieldnames = ["Nama", "Usia", "Kota"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)

    writer.writeheader()  # Menulis header
    writer.writerows(data)  # Menulis data
```

---

# **6. Menggunakan Separator yang Berbeda (`delimiter`)**  
Secara default, CSV menggunakan **koma (`,`)** sebagai pemisah. Kita bisa mengubahnya dengan **titik koma (`;`)** atau tab (`\t`).

```python
with open("data.csv", mode="r", newline="") as file:
    reader = csv.reader(file, delimiter=";")  # Menggunakan pemisah titik koma
    for row in reader:
        print(row)
```

---

# **7. Menggunakan Quote (`quotechar`) untuk Data dengan Koma**  
Jika ada teks yang mengandung koma, kita bisa menggunakan **quotechar** untuk menghindari kesalahan parsing.

Contoh data:
```
Nama,Alamat
Budi,"Jl. Merdeka, No 10"
Siti,"Jl. Soekarno-Hatta, Blok A"
```

```python
with open("data.csv", mode="r", newline="") as file:
    reader = csv.reader(file, quotechar='"')
    for row in reader:
        print(row)
```

---

# **8. Menangani Error Saat Membaca CSV**  
Jika file CSV rusak atau formatnya tidak sesuai, kita bisa menangani error menggunakan `try-except`.

```python
try:
    with open("data.csv", mode="r", newline="") as file:
        reader = csv.reader(file)
        for row in reader:
            print(row)
except FileNotFoundError:
    print("File tidak ditemukan!")
except csv.Error as e:
    print(f"Terjadi kesalahan saat membaca CSV: {e}")
```

---

# **9. Contoh Lengkap: Membaca dan Menulis CSV**  
```python
import csv

# Menulis data ke file CSV
data = [
    {"Nama": "Budi", "Usia": 25, "Kota": "Jakarta"},
    {"Nama": "Siti", "Usia": 30, "Kota": "Surabaya"},
    {"Nama": "Joko", "Usia": 27, "Kota": "Bandung"}
]

with open("data.csv", mode="w", newline="") as file:
    fieldnames = ["Nama", "Usia", "Kota"]
    writer = csv.DictWriter(file, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerows(data)

# Membaca data dari file CSV
with open("data.csv", mode="r", newline="") as file:
    reader = csv.DictReader(file)
    for row in reader:
        print(row)
```

---

# **10. Kesimpulan**  
✅ **`csv.reader()`** → Membaca file CSV sebagai list  
✅ **`csv.DictReader()`** → Membaca file CSV sebagai dictionary  
✅ **`csv.writer()`** → Menulis CSV dari list  
✅ **`csv.DictWriter()`** → Menulis CSV dari dictionary  
✅ **Menggunakan delimiter kustom (`delimiter`)**  
✅ **Menangani error saat membaca CSV**  

Library `csv` sangat berguna untuk **pengolahan data, ekspor-impor data, dan interaksi dengan spreadsheet**.
