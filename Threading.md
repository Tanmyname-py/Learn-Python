# PYTHON THREADING

## **1. Pendahuluan**  
Library `threading` dalam Python digunakan untuk menjalankan banyak tugas (proses) secara bersamaan dalam satu program. **Threading** memungkinkan eksekusi kode secara paralel, meningkatkan efisiensi program dalam mengelola tugas yang tidak bergantung satu sama lain.  

### **Kapan Menggunakan `threading`?**  
✅ Untuk tugas yang memerlukan multitasking ringan, seperti pemrosesan data dalam aplikasi GUI  
✅ Untuk menjalankan operasi I/O (misalnya membaca file atau melakukan permintaan HTTP) tanpa menghentikan program utama  
✅ Untuk mengontrol beberapa tugas secara bersamaan tanpa menunggu tugas lain selesai  

---

## **2. Cara Menggunakan Library `threading`**  
Untuk menggunakan `threading`, kita harus mengimpornya terlebih dahulu:  
```python
import threading
```

---

# **3. Membuat dan Menjalankan Thread**  
### **3.1. Membuat Thread dengan `threading.Thread`**  
```python
import threading

def print_hello():
    print("Hello dari thread!")

# Membuat thread baru
thread1 = threading.Thread(target=print_hello)

# Menjalankan thread
thread1.start()

# Menunggu thread selesai sebelum melanjutkan program utama
thread1.join()

print("Program selesai")
```
✅ `target=print_hello` → Menentukan fungsi yang akan dijalankan oleh thread  
✅ `.start()` → Memulai eksekusi thread  
✅ `.join()` → Menunggu thread selesai sebelum melanjutkan eksekusi program utama  

### **3.2. Membuat Thread dengan Argumen**  
```python
def print_message(message):
    print(message)

thread2 = threading.Thread(target=print_message, args=("Halo, ini thread kedua!",))
thread2.start()
thread2.join()
```
✅ `args=("Halo, ini thread kedua!",)` → Mengirim argumen ke fungsi  

---

# **4. Membuat Thread dengan Kelas (`Thread` Subclass)**  
```python
class MyThread(threading.Thread):
    def __init__(self, name):
        threading.Thread.__init__(self)
        self.name = name

    def run(self):  # Metode utama yang dieksekusi dalam thread
        print(f"Thread {self.name} sedang berjalan")

# Membuat dan menjalankan thread
thread3 = MyThread("Thread-3")
thread3.start()
thread3.join()
```
✅ Metode `run()` digunakan untuk mengeksekusi logika thread  
✅ `.start()` menjalankan thread dengan memanggil `run()`  

---

# **5. Sinkronisasi Thread**  
Ketika beberapa thread berbagi sumber daya yang sama, kita harus memastikan tidak ada konflik menggunakan **Lock**.

### **5.1. Menggunakan `Lock` untuk Menghindari Konflik**  
```python
import time

lock = threading.Lock()

def print_numbers():
    with lock:  # Mengamankan akses ke kode di dalam blok ini
        for i in range(5):
            time.sleep(1)
            print(i)

thread4 = threading.Thread(target=print_numbers)
thread5 = threading.Thread(target=print_numbers)

thread4.start()
thread5.start()

thread4.join()
thread5.join()
```
✅ `lock = threading.Lock()` → Membuat objek **Lock**  
✅ `with lock:` → Mengunci akses ke kode dalam blok tertentu untuk satu thread pada satu waktu  

---

# **6. Daemon Thread**  
Daemon thread berjalan di latar belakang dan akan dihentikan secara otomatis ketika semua **non-daemon** thread selesai.

```python
def background_task():
    while True:
        print("Daemon thread berjalan...")
        time.sleep(2)

# Membuat daemon thread
daemon_thread = threading.Thread(target=background_task, daemon=True)
daemon_thread.start()

time.sleep(5)  # Menunggu beberapa detik sebelum program selesai
print("Program utama selesai")
```
✅ `.daemon = True` → Mengatur thread sebagai daemon  
✅ **Daemon thread akan berhenti ketika program utama selesai**  

---

# **7. Menjalankan Banyak Thread Sekaligus (`Thread Pooling`)**  
### **7.1. Menggunakan `ThreadPoolExecutor` untuk Menjalankan Banyak Thread**  
```python
from concurrent.futures import ThreadPoolExecutor

def task(name):
    print(f"Tugas {name} dimulai")
    time.sleep(2)
    print(f"Tugas {name} selesai")

# Membuat thread pool dengan 3 thread
with ThreadPoolExecutor(max_workers=3) as executor:
    executor.map(task, ["A", "B", "C", "D", "E"])
```
✅ `ThreadPoolExecutor(max_workers=3)` → Membatasi maksimal 3 thread berjalan bersamaan  
✅ `.map(task, [...])` → Menjalankan fungsi `task` untuk setiap item dalam daftar  

---

# **8. Komunikasi Antar Thread dengan `Queue`**  
Library `queue` dapat digunakan untuk berbagi data antar thread secara aman.

```python
import queue

task_queue = queue.Queue()

def worker():
    while not task_queue.empty():
        item = task_queue.get()
        print(f"Memproses item: {item}")
        task_queue.task_done()

# Menambahkan item ke dalam queue
for i in range(5):
    task_queue.put(i)

# Membuat dan menjalankan worker thread
thread6 = threading.Thread(target=worker)
thread7 = threading.Thread(target=worker)

thread6.start()
thread7.start()

task_queue.join()  # Menunggu hingga semua item diproses
```
✅ `queue.Queue()` → Struktur data FIFO (First In, First Out)  
✅ `.put()` → Menambahkan item ke queue  
✅ `.get()` → Mengambil item dari queue  
✅ `.task_done()` → Menandai item sebagai selesai diproses  

---

# **9. Menampilkan Semua Thread yang Sedang Berjalan**  
```python
all_threads = threading.enumerate()
print("Thread yang sedang berjalan:", all_threads)
```

---

# **10. Perbandingan `threading` vs `multiprocessing`**  
| **Fitur** | **`threading`** | **`multiprocessing`** |
|-----------|---------------|------------------|
| Eksekusi | Multithreading | Multiprocessing |
| CPU Bound Tasks | ❌ Tidak efektif | ✅ Efektif |
| I/O Bound Tasks | ✅ Sangat efektif | ❌ Tidak diperlukan |
| Berbagi Memori | ✅ Ya | ❌ Tidak |
| Keamanan | ⚠️ Risiko Race Condition | ✅ Lebih aman |

Gunakan **`threading`** untuk **tugas I/O (input/output)** seperti **HTTP request, database query, atau membaca file**.  
Gunakan **`multiprocessing`** untuk **tugas berat CPU**, seperti **perhitungan matematis yang kompleks**.  

---

# **11. Kesimpulan**  
✅ `threading` memungkinkan kita menjalankan banyak tugas secara bersamaan dalam satu program  
✅ Gunakan `.start()` dan `.join()` untuk mengontrol eksekusi thread  
✅ Gunakan `Lock` untuk menghindari konflik antar thread  
✅ `Daemon thread` berguna untuk tugas latar belakang yang tidak mempengaruhi program utama  
✅ `ThreadPoolExecutor` adalah cara yang lebih efisien untuk menjalankan banyak thread sekaligus  
✅ `Queue` digunakan untuk berbagi data antar thread secara aman  

Dengan memahami **`threading`**, kita bisa membuat program Python yang lebih **efisien, cepat, dan responsif** dalam menangani tugas-tugas multitasking!
