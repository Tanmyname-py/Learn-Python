# PYTHON TIME

## **1. Pendahuluan**  
Modul `time` dalam Python adalah modul standar yang menyediakan fungsi untuk bekerja dengan waktu. Modul ini digunakan untuk:  
✅ Mengukur waktu eksekusi program  
✅ Melakukan delay (penundaan) dalam program  
✅ Mengonversi antara waktu Unix (epoch) dan format lain  
✅ Mengambil waktu saat ini dengan format tertentu  

---

## **2. Cara Menggunakan Library `time`**  
Untuk menggunakan modul `time`, kita perlu mengimpornya terlebih dahulu:  
```python
import time
```

---

# **3. Representasi Waktu dalam `time`**  
### **3.1. Waktu Epoch (Unix Timestamp)**  
Waktu epoch adalah waktu dalam detik sejak **1 Januari 1970 00:00:00 UTC**.

### **3.2. Waktu dalam Bentuk Struct_time**  
Struct_time adalah representasi waktu dalam bentuk tuple dengan 9 elemen:  
```python
time.struct_time(tm_year=2025, tm_mon=2, tm_mday=23, tm_hour=14, tm_min=30, tm_sec=10, tm_wday=6, tm_yday=54, tm_isdst=0)
```
| Indeks | Atribut | Keterangan | Contoh |
|--------|---------|------------|--------|
| 0 | `tm_year` | Tahun | 2025 |
| 1 | `tm_mon` | Bulan (1-12) | 2 |
| 2 | `tm_mday` | Tanggal (1-31) | 23 |
| 3 | `tm_hour` | Jam (0-23) | 14 |
| 4 | `tm_min` | Menit (0-59) | 30 |
| 5 | `tm_sec` | Detik (0-61) | 10 |
| 6 | `tm_wday` | Hari dalam seminggu (0 = Senin, 6 = Minggu) | 6 |
| 7 | `tm_yday` | Hari dalam setahun (1-366) | 54 |
| 8 | `tm_isdst` | Daylight Saving Time (-1, 0, 1) | 0 |

---

# **4. Mendapatkan Waktu Saat Ini**
### **4.1. Mendapatkan Timestamp Saat Ini (`time.time()`)**  
```python
timestamp = time.time()
print(timestamp)  # Contoh output: 1745679010.123456
```

### **4.2. Mendapatkan Waktu dalam Format Struct_time (`time.localtime()`)**  
```python
current_time = time.localtime()
print(current_time)  # Output: struct_time(tm_year=2025, tm_mon=2, ...)
```

### **4.3. Mendapatkan Waktu UTC (`time.gmtime()`)**  
```python
utc_time = time.gmtime()
print(utc_time)  # Waktu UTC dalam struct_time
```

---

# **5. Format Waktu (`strftime`)**  
### **5.1. Mengonversi Waktu ke String**  
```python
formatted_time = time.strftime("%d-%m-%Y %H:%M:%S", time.localtime())
print(formatted_time)  # Output: 23-02-2025 14:30:10
```

**Beberapa format penting:**  
| Format | Keterangan | Contoh |
|--------|-----------|--------|
| `%Y`   | Tahun penuh | 2025 |
| `%y`   | Tahun dua digit | 25 |
| `%m`   | Bulan (01-12) | 02 |
| `%d`   | Hari (01-31) | 23 |
| `%H`   | Jam (24 jam) | 14 |
| `%M`   | Menit | 30 |
| `%S`   | Detik | 10 |

---

# **6. Parsing String ke Waktu (`strptime`)**  
```python
date_str = "23-02-2025 14:30:10"
parsed_time = time.strptime(date_str, "%d-%m-%Y %H:%M:%S")
print(parsed_time)  # Output: struct_time(...)
```

---

# **7. Mengubah Waktu ke Timestamp (`mktime`)**  
```python
timestamp = time.mktime(parsed_time)
print(timestamp)  # Output: 1745679010.0
```

---

# **8. Delay dan Pengukuran Waktu**
### **8.1. Menunda Eksekusi Program (`time.sleep()`)**  
```python
print("Menunggu 3 detik...")
time.sleep(3)  # Program akan berhenti selama 3 detik
print("Lanjut eksekusi")
```

### **8.2. Mengukur Waktu Eksekusi (`time.perf_counter()`)**  
```python
start_time = time.perf_counter()
time.sleep(2)  # Simulasi proses yang berjalan 2 detik
end_time = time.perf_counter()

execution_time = end_time - start_time
print(f"Waktu eksekusi: {execution_time:.2f} detik")
```

---

# **9. Fungsi Lanjutan dalam `time`**
### **9.1. Menghitung Waktu CPU yang Digunakan (`time.process_time()`)**  
```python
start_cpu = time.process_time()
for _ in range(1000000):
    pass  # Simulasi perhitungan
end_cpu = time.process_time()

print(f"Waktu CPU yang digunakan: {end_cpu - start_cpu:.5f} detik")
```

### **9.2. Menghitung Zona Waktu Lokal (`time.timezone`)**  
```python
print(time.timezone)  # Offset zona waktu dalam detik dari UTC
```

### **9.3. Menampilkan Nama Zona Waktu**  
```python
print(time.tzname)  # Output: ('WIB', 'WIB') untuk zona waktu Indonesia
```

---

# **10. Konversi Waktu Cepat**
| Fungsi | Keterangan | Contoh Output |
|--------|-----------|--------------|
| `time.time()` | Timestamp sekarang | 1745679010.123456 |
| `time.localtime()` | Waktu sekarang dalam `struct_time` | struct_time(tm_year=2025, tm_mon=2, ...) |
| `time.strftime("%Y-%m-%d %H:%M:%S", time.localtime())` | Format tanggal | "2025-02-23 14:30:10" |
| `time.sleep(3)` | Menunda program 3 detik | - |

---

# **11. Kesimpulan**  
Modul `time` sangat penting dalam Python untuk:  
✅ Mendapatkan waktu saat ini dalam berbagai format  
✅ Mengonversi waktu antara timestamp, `struct_time`, dan string  
✅ Melakukan delay dengan `time.sleep()`  
✅ Mengukur waktu eksekusi program  
✅ Mengakses informasi zona waktu  

Modul `time` sering digunakan dalam **pengolahan data waktu, otomatisasi tugas, dan debugging performa program**.
