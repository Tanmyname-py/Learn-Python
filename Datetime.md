# **Materi Ajar Lengkap: Library `datetime` dalam Python**  

## **1. Pendahuluan**  
Library `datetime` dalam Python adalah modul standar yang digunakan untuk bekerja dengan tanggal dan waktu. Modul ini memungkinkan kita untuk membuat, memanipulasi, dan memformat data waktu dengan berbagai metode yang berguna.

---

## **2. Cara Menggunakan Library `datetime`**  
Untuk menggunakan library `datetime`, kita harus mengimpornya terlebih dahulu:  
```python
import datetime
```

---

# **3. Objek `datetime`**
Objek `datetime` digunakan untuk menyimpan informasi tentang tanggal dan waktu.

### **3.1. Mendapatkan Tanggal dan Waktu Saat Ini**  
```python
import datetime

now = datetime.datetime.now()
print(now)  # Contoh output: 2025-02-23 14:30:10.123456
```

### **3.2. Membuat Objek `datetime` Secara Manual**  
```python
dt = datetime.datetime(2025, 2, 23, 14, 30, 10)  
print(dt)  # Output: 2025-02-23 14:30:10
```

---

# **4. Komponen dalam `datetime`**  
Objek `datetime` memiliki berbagai atribut yang bisa diakses:

```python
print(now.year)   # Tahun
print(now.month)  # Bulan
print(now.day)    # Hari
print(now.hour)   # Jam
print(now.minute) # Menit
print(now.second) # Detik
```

---

# **5. Format Tanggal dan Waktu (`strftime`)**  
Kita bisa mengubah format tanggal menggunakan `strftime()`:

```python
formatted_date = now.strftime("%d-%m-%Y %H:%M:%S")
print(formatted_date)  # Output: 23-02-2025 14:30:10
```

**Beberapa format penting:**
| Format | Keterangan | Contoh |
|--------|-----------|--------|
| `%Y`   | Tahun penuh | 2025 |
| `%y`   | Tahun dua digit | 25 |
| `%m`   | Bulan (01-12) | 02 |
| `%d`   | Hari (01-31) | 23 |
| `%H`   | Jam (24 jam) | 14 |
| `%I`   | Jam (12 jam) | 02 |
| `%p`   | AM/PM | PM |
| `%M`   | Menit | 30 |
| `%S`   | Detik | 10 |

---

# **6. Parsing String ke `datetime` (`strptime`)**  
Kita bisa mengubah string menjadi objek `datetime` menggunakan `strptime()`:

```python
date_str = "23-02-2025 14:30:10"
dt_object = datetime.datetime.strptime(date_str, "%d-%m-%Y %H:%M:%S")
print(dt_object)  # Output: 2025-02-23 14:30:10
```

---

# **7. Objek `date`**  
Jika kita hanya membutuhkan tanggal tanpa waktu, kita bisa menggunakan `date`:

### **7.1. Mendapatkan Tanggal Saat Ini**
```python
today = datetime.date.today()
print(today)  # Output: 2025-02-23
```

### **7.2. Membuat Objek `date` Secara Manual**
```python
d = datetime.date(2025, 2, 23)
print(d)  # Output: 2025-02-23
```

### **7.3. Mendapatkan Hari dalam Seminggu**
```python
print(today.weekday())  # Senin = 0, Minggu = 6
print(today.isoweekday())  # Senin = 1, Minggu = 7
```

---

# **8. Objek `time`**
Jika kita hanya membutuhkan waktu tanpa tanggal, kita bisa menggunakan `time`:

### **8.1. Membuat Objek `time`**
```python
t = datetime.time(14, 30, 10)
print(t)  # Output: 14:30:10
```

### **8.2. Mengakses Komponen Waktu**
```python
print(t.hour)   # 14
print(t.minute) # 30
print(t.second) # 10
```

---

# **9. Objek `timedelta` (Operasi Aritmatika dengan Tanggal dan Waktu)**  
Objek `timedelta` digunakan untuk perhitungan selisih waktu.

### **9.1. Menambah/Mengurangi Waktu**
```python
delta = datetime.timedelta(days=5)
new_date = today + delta
print(new_date)  # Output: 2025-02-28 (5 hari setelah hari ini)
```

### **9.2. Menghitung Selisih Antara Dua Tanggal**
```python
start_date = datetime.date(2025, 2, 1)
end_date = datetime.date(2025, 2, 23)

difference = end_date - start_date
print(difference.days)  # Output: 22 (hari)
```

---

# **10. Mendapatkan Waktu dalam Format Timestamp**
### **10.1. Mengonversi `datetime` ke Timestamp**
```python
timestamp = now.timestamp()
print(timestamp)  # Output: 1745679010.123456 (detik sejak 1 Januari 1970)
```

### **10.2. Mengonversi Timestamp ke `datetime`**
```python
dt_from_timestamp = datetime.datetime.fromtimestamp(timestamp)
print(dt_from_timestamp)  # Output: 2025-02-23 14:30:10
```

---

# **11. Timezone (`pytz` - Modul Eksternal untuk Zona Waktu)**
Python secara default tidak menangani zona waktu. Untuk itu, kita bisa menggunakan **`pytz`**.

### **11.1. Install `pytz`**
```sh
pip install pytz
```

### **11.2. Menampilkan Waktu dalam Zona Waktu Berbeda**
```python
import pytz

utc_now = datetime.datetime.now(pytz.utc)
print(utc_now)  # Waktu UTC saat ini

jakarta_tz = pytz.timezone('Asia/Jakarta')
jakarta_time = utc_now.astimezone(jakarta_tz)
print(jakarta_time)  # Waktu di Jakarta
```

---

# **12. Kesimpulan**  
Modul `datetime` sangat berguna untuk manipulasi tanggal dan waktu dalam Python. Beberapa hal yang telah dipelajari:  
✅ Mendapatkan tanggal & waktu saat ini (`datetime.now()`)  
✅ Membuat objek `datetime`, `date`, `time` secara manual  
✅ Format dan parsing tanggal (`strftime`, `strptime`)  
✅ Operasi matematika dengan `timedelta`  
✅ Konversi ke dan dari timestamp  
✅ Menggunakan zona waktu dengan `pytz`  

Menguasai `datetime` sangat penting dalam pengolahan data yang berkaitan dengan waktu, seperti log sistem, jadwal, dan database!
