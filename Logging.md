# PYTHON LOGGING 

## **1. Pendahuluan**  
`logging` adalah modul bawaan Python yang digunakan untuk mencatat (log) kejadian dalam program. Logging berguna untuk:  
✅ Mendeteksi kesalahan dan debug program  
✅ Mencatat aktivitas sistem dan aplikasi  
✅ Memantau performa dan penggunaan aplikasi  

---

## **2. Cara Kerja Library `logging`**  
Modul `logging` bekerja dengan membuat log berdasarkan tingkat keparahan (severity level), format pesan, dan tujuan penyimpanan log.

---

# **3. Konsep Dasar Logging**
## **3.1. Level Logging**  
Python menyediakan beberapa tingkat keparahan log:

| Level | Nilai Numerik | Kegunaan |
|--------|--------------|-----------|
| `DEBUG` | 10 | Informasi detail untuk debugging |
| `INFO` | 20 | Informasi umum tentang status program |
| `WARNING` | 30 | Peringatan tentang potensi masalah |
| `ERROR` | 40 | Indikasi kesalahan yang terjadi |
| `CRITICAL` | 50 | Kesalahan serius yang bisa menghentikan program |

---

## **4. Penggunaan Dasar `logging`**
### **4.1. Membuat Log Sederhana**
```python
import logging

logging.basicConfig(level=logging.DEBUG)
logging.debug("Ini adalah pesan DEBUG")
logging.info("Ini adalah pesan INFO")
logging.warning("Ini adalah pesan WARNING")
logging.error("Ini adalah pesan ERROR")
logging.critical("Ini adalah pesan CRITICAL")
```
**Output:**
```
WARNING:root:Ini adalah pesan WARNING
ERROR:root:Ini adalah pesan ERROR
CRITICAL:root:Ini adalah pesan CRITICAL
```
Secara default, hanya level WARNING ke atas yang ditampilkan.

### **4.2. Mengubah Level Logging**
```python
logging.basicConfig(level=logging.INFO)
logging.debug("Ini tidak akan muncul")
logging.info("Ini akan muncul")
```

---

# **5. Menyesuaikan Format Log**
Kita bisa mengatur format log menggunakan `basicConfig()`.

```python
logging.basicConfig(
    level=logging.DEBUG,
    format="%(asctime)s - %(levelname)s - %(message)s",
    datefmt="%Y-%m-%d %H:%M:%S"
)

logging.info("Ini adalah log dengan format khusus")
```
**Output Contoh:**
```
2025-02-23 14:30:10 - INFO - Ini adalah log dengan format khusus
```

---

# **6. Menyimpan Log ke File**
Untuk menyimpan log ke file, gunakan `filename` dalam `basicConfig()`.

```python
logging.basicConfig(
    filename="app.log",
    level=logging.DEBUG,
    format="%(asctime)s - %(levelname)s - %(message)s"
)

logging.info("Log ini akan disimpan di file app.log")
```

---

# **7. Logging dengan Handler**
Handler digunakan untuk mengontrol di mana log akan dikirim.

### **7.1. Menulis Log ke File dan Konsol**
```python
logger = logging.getLogger()
logger.setLevel(logging.DEBUG)

# Handler untuk mencetak ke konsol
console_handler = logging.StreamHandler()
console_handler.setLevel(logging.INFO)

# Handler untuk menyimpan log ke file
file_handler = logging.FileHandler("logfile.log")
file_handler.setLevel(logging.DEBUG)

# Format log
formatter = logging.Formatter("%(asctime)s - %(levelname)s - %(message)s")
console_handler.setFormatter(formatter)
file_handler.setFormatter(formatter)

# Menambahkan handler ke logger
logger.addHandler(console_handler)
logger.addHandler(file_handler)

logger.debug("Ini log DEBUG")
logger.info("Ini log INFO")
logger.warning("Ini log WARNING")
```

---

# **8. Logging dengan Exception**
Saat menangkap error dengan `try-except`, kita bisa mencatatnya menggunakan `logging.exception()`.

```python
try:
    1 / 0
except ZeroDivisionError:
    logging.exception("Terjadi kesalahan pembagian dengan nol")
```

**Output di log file:**
```
ERROR:root:Terjadi kesalahan pembagian dengan nol
Traceback (most recent call last):
  File "script.py", line 2, in <module>
    1 / 0
ZeroDivisionError: division by zero
```

---

# **9. Logging dengan Multiple Modules**
Jika program memiliki banyak file, kita bisa menggunakan `logging.getLogger()` untuk membuat logger berbeda.

**`module1.py`**
```python
import logging

logger = logging.getLogger(__name__)
logger.setLevel(logging.DEBUG)

handler = logging.FileHandler("module1.log")
formatter = logging.Formatter("%(name)s - %(levelname)s - %(message)s")
handler.setFormatter(formatter)

logger.addHandler(handler)

def test_function():
    logger.info("Fungsi test_function dieksekusi")
```

**`main.py`**
```python
import module1

module1.test_function()
```
Hasilnya akan disimpan di `module1.log` dengan nama logger dari module tersebut.

---

# **10. Menghapus dan Mengatur Ulang Logging**
Jika kita perlu mengatur ulang konfigurasi logging di runtime:
```python
import logging

logging.getLogger().handlers = []  # Menghapus semua handler
logging.basicConfig(level=logging.INFO)  # Mengatur ulang logging
```

---

# **11. Kesimpulan**
Library `logging` sangat berguna untuk **debugging**, **monitoring aplikasi**, dan **melacak kesalahan** dalam program.  
Hal-hal yang telah dipelajari:  
✅ Menggunakan log dengan berbagai level (`DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`)  
✅ Menyesuaikan format log dengan `basicConfig()`  
✅ Menyimpan log ke file dengan `FileHandler`  
✅ Menggunakan multiple handlers untuk log ke konsol dan file  
✅ Menangani exception dengan `logging.exception()`  
✅ Logging di aplikasi multi-module  

Menggunakan logging dengan baik akan **membantu dalam debugging dan pemeliharaan aplikasi yang lebih besar!**
