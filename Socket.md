# PYTHON SOCKET 

## **1. Pendahuluan**  
Modul `socket` dalam Python digunakan untuk komunikasi jaringan melalui protokol TCP dan UDP. Modul ini memungkinkan pembuatan server dan client untuk bertukar data melalui jaringan.  

### **1.1. Fungsi Utama Modul `socket`**  
✅ Membuat dan mengelola koneksi jaringan  
✅ Mengirim dan menerima data melalui TCP atau UDP  
✅ Menghubungkan client ke server  
✅ Menangani komunikasi berbasis jaringan  

### **1.2. Cara Menggunakan `socket`**  
Untuk menggunakan library `socket`, kita harus mengimpornya terlebih dahulu:  
```python
import socket
```

---

# **2. Jenis Socket dalam Python**  
Ada dua jenis protokol utama dalam socket:  
1. **TCP (Transmission Control Protocol)** → Menggunakan koneksi, andal  
2. **UDP (User Datagram Protocol)** → Tanpa koneksi, lebih cepat tetapi kurang andal  

### **2.1. Membuat Objek Socket**
```python
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # TCP
s_udp = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)  # UDP
```
**Penjelasan parameter:**  
- `AF_INET` → Menggunakan IPv4  
- `AF_INET6` → Menggunakan IPv6  
- `SOCK_STREAM` → Menggunakan protokol TCP  
- `SOCK_DGRAM` → Menggunakan protokol UDP  

---

# **3. Membuat Server dan Client dengan TCP**
### **3.1. Membuat Server TCP**
```python
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(("127.0.0.1", 12345))  # Bind ke alamat IP dan port
server_socket.listen(5)  # Maksimum 5 koneksi yang menunggu

print("Menunggu koneksi...")
conn, addr = server_socket.accept()
print(f"Koneksi dari {addr}")

data = conn.recv(1024).decode()  # Menerima data (maks 1024 byte)
print(f"Pesan dari client: {data}")

conn.send("Pesan diterima!".encode())  # Mengirim balasan
conn.close()
```

### **3.2. Membuat Client TCP**
```python
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(("127.0.0.1", 12345))  # Hubungkan ke server

client_socket.send("Halo, server!".encode())  # Kirim pesan
response = client_socket.recv(1024).decode()  # Terima balasan
print(f"Balasan dari server: {response}")

client_socket.close()
```

---

# **4. Membuat Server dan Client dengan UDP**
### **4.1. Membuat Server UDP**
```python
import socket

server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
server_socket.bind(("127.0.0.1", 12345))

print("Menunggu pesan...")
data, addr = server_socket.recvfrom(1024)  # Menerima data
print(f"Pesan dari {addr}: {data.decode()}")

server_socket.sendto("Pesan diterima!".encode(), addr)  # Mengirim balasan
```

### **4.2. Membuat Client UDP**
```python
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

client_socket.sendto("Halo, server!".encode(), ("127.0.0.1", 12345))
response, server = client_socket.recvfrom(1024)
print(f"Balasan dari server: {response.decode()}")

client_socket.close()
```

---

# **5. Mengetahui Alamat IP dari Nama Domain**
```python
import socket

hostname = "www.google.com"
ip_address = socket.gethostbyname(hostname)
print(f"Alamat IP {hostname} adalah {ip_address}")
```

---

# **6. Mengetahui Nama Host dari Alamat IP**
```python
import socket

ip_address = "8.8.8.8"
host_name = socket.gethostbyaddr(ip_address)
print(f"Hostname untuk {ip_address} adalah {host_name}")
```

---

# **7. Mendapatkan Informasi tentang Socket**
### **7.1. Mendapatkan Nama Host Lokal**
```python
import socket

hostname = socket.gethostname()
print(f"Nama host: {hostname}")
```

### **7.2. Mendapatkan Alamat IP Host Lokal**
```python
import socket

local_ip = socket.gethostbyname(socket.gethostname())
print(f"Alamat IP lokal: {local_ip}")
```

### **7.3. Mendapatkan Informasi tentang Port**
```python
import socket

port = socket.getservbyname("http", "tcp")
print(f"Port HTTP: {port}")
```

---

# **8. Timeout dan Non-Blocking Socket**
### **8.1. Mengatur Timeout untuk Koneksi**
```python
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.settimeout(5)  # Timeout setelah 5 detik
try:
    s.connect(("example.com", 80))
    print("Koneksi berhasil")
except socket.timeout:
    print("Koneksi timeout!")
```

### **8.2. Mode Non-Blocking**
```python
s.setblocking(False)  # Socket menjadi non-blocking
```

---

# **9. Multithreading pada Socket**
Jika ingin menangani banyak koneksi dalam satu server, kita bisa menggunakan **multithreading**.

### **9.1. Server dengan Multithreading**
```python
import socket
import threading

def handle_client(client_socket):
    data = client_socket.recv(1024).decode()
    print(f"Pesan diterima: {data}")
    client_socket.send("Pesan diterima!".encode())
    client_socket.close()

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(("127.0.0.1", 12345))
server_socket.listen(5)

print("Menunggu koneksi...")

while True:
    client_socket, addr = server_socket.accept()
    print(f"Koneksi dari {addr}")
    client_thread = threading.Thread(target=handle_client, args=(client_socket,))
    client_thread.start()
```

---

# **10. Kesimpulan**  
Modul `socket` sangat berguna untuk komunikasi berbasis jaringan di Python. Dalam materi ini, kita telah mempelajari:  
✅ Cara membuat socket TCP dan UDP  
✅ Membuat server dan client sederhana  
✅ Menggunakan socket untuk mendapatkan informasi jaringan  
✅ Menangani banyak koneksi dengan **multithreading**  
✅ Mengatur timeout dan mode non-blocking  

Modul ini sangat penting untuk **pembuatan aplikasi berbasis jaringan, server, komunikasi antar komputer, dan pengembangan aplikasi IoT**.
