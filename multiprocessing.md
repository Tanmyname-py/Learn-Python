# PYTHON MULTIPROCESSING

## **1. Pendahuluan**  
Modul `multiprocessing` dalam Python memungkinkan kita menjalankan beberapa proses secara paralel menggunakan **multiple CPU cores**. Ini sangat berguna untuk **komputasi berat** dan **task paralel**, berbeda dengan **threading** yang masih terikat dengan **Global Interpreter Lock (GIL)**.

### **Kapan Menggunakan `multiprocessing`?**
✅ Komputasi berat (matematika, AI, machine learning)  
✅ Proses independen (misalnya download file secara paralel)  
✅ Memanfaatkan **multiple CPU cores**  

---

## **2. Cara Menggunakan Library `multiprocessing`**
Untuk menggunakan `multiprocessing`, kita harus mengimpornya terlebih dahulu:  
```python
import multiprocessing
```

---

# **3. Membuat dan Menjalankan Proses**  
### **3.1. Contoh Dasar `multiprocessing.Process`**
```python
import multiprocessing

def print_hello():
    print("Hello from process!")

if __name__ == "__main__":
    process = multiprocessing.Process(target=print_hello)
    process.start()
    process.join()  # Menunggu proses selesai
```
### **Penjelasan:**
- `multiprocessing.Process(target=function_name)`: Membuat proses baru
- `.start()`: Memulai eksekusi proses
- `.join()`: Menunggu proses selesai sebelum melanjutkan eksekusi utama

---

# **4. Menggunakan Banyak Proses (Parallel Processing)**
```python
import multiprocessing

def worker(num):
    print(f"Proses {num} berjalan")

if __name__ == "__main__":
    processes = []
    for i in range(4):  # Jalankan 4 proses
        p = multiprocessing.Process(target=worker, args=(i,))
        processes.append(p)
        p.start()

    for p in processes:
        p.join()
```
### **Hasil Eksekusi (Paralel)**
```
Proses 0 berjalan
Proses 1 berjalan
Proses 2 berjalan
Proses 3 berjalan
```

---

# **5. Pool: Menjalankan Banyak Proses dengan `multiprocessing.Pool`**
### **5.1. Menggunakan `Pool.map()`**
```python
import multiprocessing

def square(n):
    return n * n

if __name__ == "__main__":
    with multiprocessing.Pool(processes=4) as pool:
        results = pool.map(square, [1, 2, 3, 4, 5])
    print(results)  # Output: [1, 4, 9, 16, 25]
```
**Penjelasan:**  
- `Pool.map(function, iterable)`: Membagi tugas ke beberapa CPU

---

# **6. Berbagi Data Antar Proses**
### **6.1. Menggunakan `Value` untuk Berbagi Data**
```python
import multiprocessing

def worker(val):
    val.value += 1  # Memodifikasi nilai di dalam proses

if __name__ == "__main__":
    shared_val = multiprocessing.Value('i', 0)  # 'i' = integer
    process = multiprocessing.Process(target=worker, args=(shared_val,))
    process.start()
    process.join()
    print(shared_val.value)  # Output: 1
```

### **6.2. Menggunakan `Array` untuk Berbagi Data**
```python
import multiprocessing

def worker(arr):
    arr[0] += 1

if __name__ == "__main__":
    shared_arr = multiprocessing.Array('i', [1, 2, 3])
    process = multiprocessing.Process(target=worker, args=(shared_arr,))
    process.start()
    process.join()
    print(shared_arr[:])  # Output: [2, 2, 3]
```

---

# **7. Komunikasi Antar Proses**
### **7.1. Menggunakan Queue**
```python
import multiprocessing

def worker(queue):
    queue.put("Data dari proses!")

if __name__ == "__main__":
    queue = multiprocessing.Queue()
    process = multiprocessing.Process(target=worker, args=(queue,))
    process.start()
    process.join()
    print(queue.get())  # Output: "Data dari proses!"
```

### **7.2. Menggunakan Pipe**
```python
import multiprocessing

def worker(conn):
    conn.send("Hello from child process")
    conn.close()

if __name__ == "__main__":
    parent_conn, child_conn = multiprocessing.Pipe()
    process = multiprocessing.Process(target=worker, args=(child_conn,))
    process.start()
    process.join()
    print(parent_conn.recv())  # Output: "Hello from child process"
```

---

# **8. Sinkronisasi Antar Proses**
### **8.1. Menggunakan Lock untuk Mencegah Race Condition**
```python
import multiprocessing
import time

def worker(lock):
    with lock:
        print("Proses sedang berjalan")
        time.sleep(1)

if __name__ == "__main__":
    lock = multiprocessing.Lock()
    processes = [multiprocessing.Process(target=worker, args=(lock,)) for _ in range(3)]
    
    for p in processes:
        p.start()
    
    for p in processes:
        p.join()
```
**Penjelasan:**  
- `Lock` mencegah beberapa proses mengakses sumber daya secara bersamaan.

---

# **9. Menjalankan Fungsi Secara Background (`daemon`)**
```python
import multiprocessing
import time

def background_task():
    while True:
        print("Daemon process running...")
        time.sleep(2)

if __name__ == "__main__":
    process = multiprocessing.Process(target=background_task, daemon=True)
    process.start()
    time.sleep(5)
    print("Main process selesai")
```
**Penjelasan:**  
- `.daemon = True`: Proses akan berhenti jika proses utama selesai.

---

# **10. Perbedaan `multiprocessing` vs `threading`**
| Fitur | `multiprocessing` | `threading` |
|--------|------------------|-------------|
| Eksekusi | Paralel (multi-core) | Konkurensi (single-core) |
| GIL | Tidak terpengaruh | Terpengaruh |
| Gunakan untuk | CPU-bound tasks | I/O-bound tasks |

---

# **11. Kesimpulan**  
Modul `multiprocessing` memungkinkan kita untuk menjalankan tugas secara **paralel menggunakan banyak CPU core**.  
✅ **Membuat dan menjalankan proses dengan `Process`**  
✅ **Menjalankan banyak proses dengan `Pool`**  
✅ **Berbagi data antar proses dengan `Value` dan `Array`**  
✅ **Menggunakan `Queue` dan `Pipe` untuk komunikasi antar proses**  
✅ **Mengelola sinkronisasi dengan `Lock`**  
✅ **Menjalankan tugas di background dengan daemon process**  

Dengan menguasai `multiprocessing`, kita bisa membuat program yang lebih **efisien dan cepat**, terutama untuk **pemrosesan data besar dan AI/ML**!
