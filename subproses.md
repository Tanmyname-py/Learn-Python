# PYTHON SUBPROSES
## **1. Pendahuluan**  
Modul `subprocess` dalam Python digunakan untuk menjalankan perintah sistem (command-line) dari dalam kode Python. Dengan `subprocess`, kita dapat:  
✅ Menjalankan perintah shell/command-line  
✅ Mengambil output dari perintah yang dieksekusi  
✅ Mengontrol input/output/error proses eksternal  
✅ Menangani proses secara asynchronous  

---

## **2. Cara Menggunakan Library `subprocess`**  
Untuk menggunakan `subprocess`, kita harus mengimpornya terlebih dahulu:  
```python
import subprocess
```

---

# **3. Menjalankan Perintah dengan `subprocess.run()`**  
### **3.1. Menjalankan Perintah Sederhana**  
```python
import subprocess

subprocess.run(["ls", "-l"])  # Linux/macOS
# subprocess.run(["dir"], shell=True)  # Windows
```
Perintah ini akan mencetak daftar file di direktori saat ini.

### **3.2. Menjalankan Perintah dengan Output Ditampilkan**  
```python
result = subprocess.run(["echo", "Hello, World!"])
print(result)  # Akan mencetak status eksekusi perintah
```

---

# **4. Mengambil Output Perintah (`capture_output=True`)**  
### **4.1. Menyimpan Output ke Variabel**
```python
result = subprocess.run(["echo", "Hello, Python!"], capture_output=True, text=True)
print(result.stdout)  # Output: Hello, Python!
```

### **4.2. Mengambil Error Output (`stderr`)**  
```python
result = subprocess.run(["ls", "folder_tidak_ada"], capture_output=True, text=True)
print(result.stderr)  # Akan mencetak pesan error
```

---

# **5. Menjalankan Perintah dengan `check=True`**  
Jika kita ingin Python menghentikan eksekusi saat terjadi error, gunakan `check=True`:
```python
subprocess.run(["ls", "folder_tidak_ada"], check=True)  # Akan memunculkan exception jika gagal
```
Jika perintah gagal, `subprocess.CalledProcessError` akan muncul.

---

# **6. Menggunakan `subprocess.Popen()` untuk Kontrol yang Lebih Fleksibel**  
### **6.1. Menjalankan Perintah dengan `Popen`**
```python
process = subprocess.Popen(["echo", "Hello from Popen!"], stdout=subprocess.PIPE, text=True)
output, _ = process.communicate()
print(output)  # Output: Hello from Popen!
```
Fungsi `Popen` digunakan untuk menjalankan proses secara lebih fleksibel dibanding `run()`.

### **6.2. Menjalankan Perintah Secara Asynchronous**
```python
process = subprocess.Popen(["sleep", "5"])  # Linux/macOS
# process = subprocess.Popen(["timeout", "5"])  # Windows
print("Proses berjalan di latar belakang...")
process.wait()  # Tunggu hingga selesai
print("Proses selesai!")
```

---

# **7. Memberikan Input ke Perintah (`stdin`)**
### **7.1. Mengirim Input ke Perintah**
```python
process = subprocess.Popen(["python3", "-c", "print(input())"], stdin=subprocess.PIPE, stdout=subprocess.PIPE, text=True)
output, _ = process.communicate(input="Hello, Input!")
print(output)  # Output: Hello, Input!
```

---

# **8. Menggabungkan Beberapa Perintah (`subprocess.PIPE`)**  
### **8.1. Menghubungkan Output ke Perintah Lain**
```python
p1 = subprocess.Popen(["echo", "Hello"], stdout=subprocess.PIPE, text=True)
p2 = subprocess.Popen(["tr", "a-z", "A-Z"], stdin=p1.stdout, stdout=subprocess.PIPE, text=True)
output, _ = p2.communicate()
print(output)  # Output: HELLO
```
Perintah `tr` di atas mengubah teks menjadi huruf besar.

---

# **9. Menangani Timeout dalam Eksekusi Perintah**
```python
subprocess.run(["sleep", "5"], timeout=2)  # Akan menimbulkan exception jika lebih dari 2 detik
```
Jika perintah tidak selesai dalam batas waktu, `subprocess.TimeoutExpired` akan muncul.

---

# **10. Menjalankan Perintah dalam Shell (`shell=True`)**
```python
subprocess.run("echo Hello from Shell!", shell=True)
```
Gunakan `shell=True` jika ingin menjalankan perintah langsung di shell.

⚠ **Peringatan**: Jangan gunakan `shell=True` dengan input dari pengguna karena rentan terhadap **command injection**.

---

# **11. Kesimpulan**  
Modul `subprocess` sangat berguna untuk menjalankan perintah eksternal dari Python.  
✅ `run()` → Menjalankan perintah dengan kontrol sederhana  
✅ `capture_output=True` → Mengambil output perintah  
✅ `Popen()` → Menjalankan proses secara lebih fleksibel  
✅ `PIPE` → Menghubungkan output antar perintah  
✅ `shell=True` → Menjalankan perintah di shell (gunakan dengan hati-hati)  

Menguasai `subprocess` sangat penting dalam **otomatisasi tugas, scripting, dan pengembangan sistem berbasis command-line!**
