# PYTHON ARGPARSE   

## **1. Pendahuluan**  
Library `argparse` adalah modul standar Python yang digunakan untuk **mengelola argumen command-line**. Dengan `argparse`, kita dapat dengan mudah membuat **program Python berbasis CLI (Command Line Interface)** yang menerima input dari pengguna.

---

## **2. Cara Kerja `argparse` dalam Python**  
Modul `argparse` bekerja dengan **mendefinisikan argumen**, **mem-parsing argumen dari command-line**, dan **menghasilkan output berdasarkan input tersebut**.  

**Langkah-langkah dasar menggunakan `argparse`**:
1. **Membuat parser** → `parser = argparse.ArgumentParser()`
2. **Menambahkan argumen** → `parser.add_argument("--nama", type=str, help="Nama pengguna")`
3. **Memproses argumen** → `args = parser.parse_args()`
4. **Menggunakan nilai argumen** → `print(args.nama)`

---

## **3. Membuat Program CLI Sederhana dengan `argparse`**  
```python
import argparse

# 1. Membuat parser
parser = argparse.ArgumentParser(description="Program CLI sederhana")

# 2. Menambahkan argumen
parser.add_argument("--nama", type=str, help="Nama pengguna")
parser.add_argument("--umur", type=int, help="Umur pengguna")

# 3. Memproses argumen
args = parser.parse_args()

# 4. Menggunakan nilai argumen
print(f"Halo, {args.nama}! Kamu berusia {args.umur} tahun.")
```

**Cara menjalankan program di terminal:**  
```sh
python script.py --nama "Andi" --umur 25
```
**Output:**  
```
Halo, Andi! Kamu berusia 25 tahun.
```

---

# **4. Argumen dalam `argparse`**  
### **4.1. Argumen Positional (Wajib)**  
Argumen **positional** harus diberikan tanpa awalan `--`.  
```python
parser.add_argument("nama", type=str, help="Nama pengguna")
```
**Cara menjalankan:**  
```sh
python script.py Andi
```

---

### **4.2. Argumen Optional (Tidak Wajib, dengan `--`)**  
Argumen **optional** menggunakan awalan `--` dan tidak wajib diberikan.  
```python
parser.add_argument("--umur", type=int, help="Umur pengguna", default=18)
```
Jika tidak diberikan, nilai default akan digunakan.  

---

### **4.3. Argumen dengan Boolean (`store_true` & `store_false`)**  
Argumen **boolean** digunakan untuk **mengaktifkan atau menonaktifkan opsi**.  
```python
parser.add_argument("--verbose", action="store_true", help="Tampilkan informasi tambahan")
```
Jika **dijalankan tanpa `--verbose`**, nilai default adalah `False`.  
Jika **dijalankan dengan `--verbose`**, nilai menjadi `True`.  

---

### **4.4. Argumen dengan Beberapa Nilai (`nargs`)**  
Menggunakan `nargs` untuk menerima **beberapa nilai sekaligus**.  
```python
parser.add_argument("--angka", nargs=3, type=int, help="Masukkan tiga angka")
```
**Cara menjalankan:**  
```sh
python script.py --angka 10 20 30
```
**Output:**  
```
[10, 20, 30]
```

---

### **4.5. Memilih dari Pilihan (`choices`)**  
Membatasi input ke pilihan tertentu.  
```python
parser.add_argument("--warna", choices=["merah", "biru", "hijau"], help="Pilih warna favorit")
```
Jika pengguna memasukkan warna yang tidak valid, program akan menampilkan error.

---

### **4.6. Menggunakan `default` untuk Nilai Default**  
Jika pengguna tidak memberikan input, kita bisa menetapkan nilai default.  
```python
parser.add_argument("--kota", type=str, help="Kota tempat tinggal", default="Jakarta")
```

---

# **5. Menampilkan Bantuan Otomatis (`--help`)**  
Setiap program dengan `argparse` memiliki bantuan bawaan.  

**Menjalankan perintah ini di terminal:**  
```sh
python script.py --help
```
**Output contoh:**  
```
usage: script.py [-h] [--nama NAMA] [--umur UMUR]

Program CLI sederhana

options:
  -h, --help   show this help message and exit
  --nama NAMA  Nama pengguna
  --umur UMUR  Umur pengguna
```

---

# **6. Mengelompokkan Argumen (`argparse.ArgumentParser`)**  
Kita bisa mengelompokkan argumen agar lebih rapi dengan `add_argument_group()`.  
```python
parser = argparse.ArgumentParser(description="Program dengan argumen terkelompok")

# Kelompok 1: Data Pribadi
group1 = parser.add_argument_group("Data Pribadi")
group1.add_argument("--nama", type=str, help="Nama lengkap")
group1.add_argument("--umur", type=int, help="Umur")

# Kelompok 2: Pilihan Tambahan
group2 = parser.add_argument_group("Pilihan Tambahan")
group2.add_argument("--verbose", action="store_true", help="Mode verbose")

args = parser.parse_args()
```

---

# **7. Menampilkan Error Kustom (`parser.error()`)**  
Jika ingin menangani error dengan pesan sendiri:  
```python
if args.umur < 0:
    parser.error("Umur tidak boleh negatif!")
```

---

# **8. Contoh Program CLI Lengkap**
Berikut adalah contoh program CLI yang menangani berbagai jenis argumen:  
```python
import argparse

parser = argparse.ArgumentParser(description="Program CLI Lengkap")

# Argumen wajib
parser.add_argument("nama", type=str, help="Nama pengguna")

# Argumen optional
parser.add_argument("--umur", type=int, default=18, help="Umur pengguna")
parser.add_argument("--hobi", nargs="+", type=str, help="Daftar hobi")
parser.add_argument("--status", choices=["pelajar", "pekerja"], help="Status pengguna")

# Argumen boolean
parser.add_argument("--verbose", action="store_true", help="Tampilkan detail")

args = parser.parse_args()

# Menampilkan hasil
print(f"Halo, {args.nama}! Umur: {args.umur}")
if args.hobi:
    print(f"Hobi: {', '.join(args.hobi)}")
if args.status:
    print(f"Status: {args.status}")
if args.verbose:
    print("Mode verbose aktif!")
```

### **Cara Menjalankan:**
```sh
python script.py Andi --umur 25 --hobi membaca menulis --status pekerja --verbose
```

**Output:**
```
Halo, Andi! Umur: 25
Hobi: membaca, menulis
Status: pekerja
Mode verbose aktif!
```

---

# **9. Kesimpulan**  
Modul `argparse` sangat berguna untuk membuat **program CLI yang fleksibel**.  

### **Ringkasan yang telah dipelajari:**  
✅ Membuat **parser** untuk mengelola argumen  
✅ Menggunakan **argumen positional & optional**  
✅ Menangani **boolean, multiple values, dan pilihan tetap**  
✅ Menggunakan **bantuan otomatis (`--help`)**  
✅ Membuat **error handling kustom**  
✅ Mengelompokkan argumen untuk program yang kompleks  

Modul ini **sangat berguna untuk membuat tools berbasis command-line**, seperti skrip otomatisasi, data processing, dan aplikasi berbasis terminal.
