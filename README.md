# PYTHON OS
## **1. Pendahuluan**  
Pustaka `os` dalam Python adalah modul standar yang digunakan untuk berinteraksi dengan sistem operasi. Modul ini menyediakan fungsi untuk bekerja dengan file, direktori, variabel lingkungan, proses sistem, dan lainnya.

## **2. Cara Menggunakan Library `os`**  
Untuk menggunakan pustaka `os`, kita harus mengimpornya terlebih dahulu:  
```python
import os
```

---

# **3. Mengakses Informasi Sistem**
## **3.1. Mengetahui Sistem Operasi**  
```python
print(os.name)  # 'posix' untuk Linux/macOS, 'nt' untuk Windows
```

## **3.2. Mendapatkan Variabel Lingkungan**
```python
print(os.environ)  # Menampilkan semua variabel lingkungan
print(os.environ.get('HOME'))  # Direktori home pengguna (Linux/macOS)
print(os.environ.get('USERNAME'))  # Nama pengguna (Windows)
```

## **3.3. Menentukan Path Home Pengguna**  
```python
print(os.path.expanduser("~"))  # Mendapatkan direktori home
```

---

# **4. Manipulasi Direktori**
## **4.1. Mendapatkan Direktori Kerja Saat Ini**
```python
print(os.getcwd())  # Menampilkan path direktori saat ini
```

## **4.2. Berpindah Direktori**
```python
os.chdir('/path/to/directory')  # Mengubah direktori kerja
print(os.getcwd())  # Konfirmasi direktori baru
```

## **4.3. Membuat Direktori**
```python
os.mkdir('folder_baru')  # Membuat satu folder
os.makedirs('folder1/folder2/folder3')  # Membuat folder bertingkat
```

## **4.4. Menghapus Direktori**
```python
os.rmdir('folder_baru')  # Menghapus folder kosong
os.removedirs('folder1/folder2/folder3')  # Menghapus folder bertingkat
```

## **4.5. Menampilkan Isi Direktori**
```python
print(os.listdir('.'))  # Menampilkan isi direktori saat ini
```

---

# **5. Manipulasi File**
## **5.1. Mengecek Keberadaan File atau Folder**
```python
print(os.path.exists('file.txt'))  # True jika file ada
print(os.path.isdir('folder'))  # True jika path adalah folder
print(os.path.isfile('file.txt'))  # True jika path adalah file
```

## **5.2. Menghapus File**
```python
os.remove('file.txt')  # Menghapus file
```

## **5.3. Mengganti Nama File atau Folder**
```python
os.rename('file_lama.txt', 'file_baru.txt')  # Mengganti nama file
os.rename('folder_lama', 'folder_baru')  # Mengganti nama folder
```

---

# **6. Manipulasi Path (os.path)**
Modul `os.path` membantu dalam manipulasi path file dan direktori.

## **6.1. Menggabungkan Path**
```python
path_baru = os.path.join('folder', 'subfolder', 'file.txt')
print(path_baru)  # Output: folder/subfolder/file.txt (Linux/macOS) atau folder\subfolder\file.txt (Windows)
```

## **6.2. Mendapatkan Nama File dan Direktori**
```python
print(os.path.basename('/home/user/file.txt'))  # Output: file.txt
print(os.path.dirname('/home/user/file.txt'))  # Output: /home/user
```

## **6.3. Memisahkan Path**
```python
print(os.path.split('/home/user/file.txt'))  # Output: ('/home/user', 'file.txt')
```

## **6.4. Menentukan Ekstensi File**
```python
print(os.path.splitext('dokumen.pdf'))  # Output: ('dokumen', '.pdf')
```

---

# **7. Eksekusi Perintah Sistem**
## **7.1. Menjalankan Perintah Shell**
```python
os.system('ls')  # Linux/macOS
os.system('dir')  # Windows
```

## **7.2. Mendapatkan Path Eksekusi Python**
```python
print(os.path.abspath(__file__))  # Menampilkan path file Python yang sedang dieksekusi
```

---

# **8. Proses dan Threading**
## **8.1. Mendapatkan ID Proses**
```python
print(os.getpid())  # Menampilkan ID proses Python
```

## **8.2. Membuat dan Menghentikan Proses**
```python
pid = os.fork()  # Hanya untuk Linux/macOS
if pid == 0:
    print("Ini adalah proses anak")
else:
    print("Ini adalah proses induk")
```

## **8.3. Menjalankan Program Lain dari Python**
```python
os.execvp('python3', ['python3', '--version'])  # Menjalankan Python dari Python
```

---

# **9. Menentukan Hak Akses File**
## **9.1. Mengecek Hak Akses**
```python
print(os.access('file.txt', os.R_OK))  # Cek apakah file bisa dibaca
print(os.access('file.txt', os.W_OK))  # Cek apakah file bisa ditulis
print(os.access('file.txt', os.X_OK))  # Cek apakah file bisa dieksekusi
```

## **9.2. Mengubah Hak Akses File**
```python
os.chmod('file.txt', 0o777)  # Memberikan hak akses penuh
```

---

# **10. Kesimpulan**  
Library `os` sangat berguna untuk mengelola file, direktori, sistem, dan proses. Memahami fungsi-fungsi di dalamnya akan membantu dalam membuat skrip otomatisasi dan interaksi dengan sistem operasi secara efisien.
