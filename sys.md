# PYTHON SYS

## **1. Pendahuluan**  
Library `sys` dalam Python adalah modul standar yang menyediakan fungsi dan variabel untuk berinteraksi dengan interpreter Python. Modul ini memungkinkan kita untuk mengakses parameter sistem, menangani input/output, mengelola path, menangani exception, dan banyak lagi.

### **1.1. Cara Menggunakan Library `sys`**  
Untuk menggunakan `sys`, kita harus mengimpornya terlebih dahulu:  
```python
import sys
```

---

# **2. Cara Kerja `sys` dalam Python**  
Modul `sys` bekerja dengan menyediakan antarmuka antara interpreter Python dan sistem operasi. Dengan `sys`, kita bisa mengakses argumen command-line, membaca/mengubah konfigurasi interpreter, mengelola path sistem, dan menangani error.

---

# **3. Argumen Command-Line (`sys.argv`)**  
### **3.1. Mengakses Argumen dari Command-Line**  
`sys.argv` menyimpan daftar argumen yang dikirimkan saat menjalankan skrip Python.  
```python
import sys

print("Nama skrip:", sys.argv[0])  # Nama file Python yang dieksekusi
if len(sys.argv) > 1:
    print("Argumen pertama:", sys.argv[1])
```
#### **Contoh Eksekusi di Terminal:**  
```sh
python script.py argumen1 argumen2
```
#### **Output:**  
```
Nama skrip: script.py
Argumen pertama: argumen1
```

### **3.2. Menghitung Jumlah Argumen**  
```python
print("Jumlah argumen:", len(sys.argv))
```

---

# **4. Manipulasi Sistem dan Path (`sys.path`)**  
### **4.1. Menampilkan Path yang Digunakan Python**  
```python
print(sys.path)  # Menampilkan daftar direktori yang dicari Python untuk modul
```

### **4.2. Menambahkan Direktori ke Path Python**  
```python
sys.path.append('/my/custom/path')  # Menambahkan direktori ke path import
```

---

# **5. Input dan Output Standar (`sys.stdin`, `sys.stdout`, `sys.stderr`)**  
### **5.1. Membaca Input dari Pengguna**  
```python
data = sys.stdin.read()  # Membaca input dari pengguna
print("Data yang dimasukkan:", data)
```

### **5.2. Menulis Output ke Konsol**  
```python
sys.stdout.write("Ini adalah output ke stdout\n")
```

### **5.3. Menulis Error ke Konsol**  
```python
sys.stderr.write("Ini adalah pesan error!\n")
```

---

# **6. Mengontrol Program dengan `sys.exit()`**  
### **6.1. Keluar dari Program dengan Kode Keluar**  
```python
sys.exit(0)  # Keluar dari program dengan kode sukses
sys.exit(1)  # Keluar dari program dengan kode error
```

---

# **7. Informasi tentang Interpreter Python**
### **7.1. Mendapatkan Versi Python**  
```python
print(sys.version)  # Menampilkan versi Python yang sedang digunakan
print(sys.version_info)  # Menampilkan informasi detail versi Python
```

### **7.2. Mendapatkan Informasi tentang Platform**  
```python
print(sys.platform)  # Menampilkan platform OS (misal: 'win32', 'linux', 'darwin')
```

---

# **8. Manajemen Memori dan Batasan Sistem**
### **8.1. Melihat Batasan Rekursi Maksimum**  
```python
print(sys.getrecursionlimit())  # Menampilkan batas rekursi
```

### **8.2. Mengubah Batas Rekursi**  
```python
sys.setrecursionlimit(2000)  # Mengubah batas rekursi maksimum
```

### **8.3. Menampilkan Ukuran Objek dalam Memori**  
```python
import sys
x = "Hello, Python!"
print(sys.getsizeof(x))  # Ukuran objek dalam byte
```

---

# **9. Menangani Exception dengan `sys.exc_info()`**  
### **9.1. Mendapatkan Informasi Exception yang Terjadi**  
```python
try:
    1 / 0
except Exception:
    print(sys.exc_info())  # Menampilkan detail exception yang terjadi
```

---

# **10. Kesimpulan**  
Modul `sys` sangat berguna untuk interaksi dengan sistem operasi dan interpreter Python. Dengan memahami `sys`, kita bisa:  
✅ Mengelola argumen command-line  
✅ Mengontrol path modul Python  
✅ Mengelola input, output, dan error  
✅ Mendapatkan informasi tentang sistem dan interpreter  
✅ Menangani error dan exception lebih efisien  

Menguasai `sys` akan sangat berguna dalam pengembangan aplikasi berbasis CLI dan manajemen sistem!
