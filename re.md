# PYTHON RE

## **1. Pendahuluan**  
Modul `re` dalam Python adalah modul standar yang digunakan untuk bekerja dengan **Regular Expressions (RegEx)**. Dengan `re`, kita bisa:  
✅ Mencari pola teks dalam string  
✅ Memvalidasi format teks (misalnya email, nomor telepon)  
✅ Mengganti teks berdasarkan pola tertentu  
✅ Membagi string dengan pola tertentu  

---

## **2. Cara Menggunakan Library `re`**  
Untuk menggunakan `re`, kita perlu mengimpornya terlebih dahulu:  
```python
import re
```

---

# **3. Dasar-Dasar Regular Expressions (RegEx)**  

### **3.1. Karakter Spesial dalam RegEx**  
| Simbol | Keterangan | Contoh |
|--------|-----------|--------|
| `.` | Karakter apa saja kecuali newline | `a.c` cocok dengan `"abc", "adc"` |
| `^` | Awal string | `^Hello` cocok dengan `"Hello world"` |
| `$` | Akhir string | `world$` cocok dengan `"Hello world"` |
| `*` | Ulangi 0 atau lebih kali | `ab*` cocok dengan `"a", "ab", "abb"` |
| `+` | Ulangi 1 atau lebih kali | `ab+` cocok dengan `"ab", "abb"` tetapi tidak `"a"` |
| `?` | 0 atau 1 kali kemunculan | `ab?` cocok dengan `"a", "ab"` |
| `{n}` | Tepat n kali kemunculan | `a{3}` cocok dengan `"aaa"` |
| `{n,}` | Minimal n kali kemunculan | `a{2,}` cocok dengan `"aa", "aaa", "aaaa"` |
| `{n,m}` | Minimal n dan maksimal m kali kemunculan | `a{2,4}` cocok dengan `"aa", "aaa", "aaaa"` |
| `[]` | Karakter dalam range tertentu | `[a-z]` cocok dengan `"a" - "z"` |
| `|` | Atau | `ab|cd` cocok dengan `"ab" atau "cd"` |
| `()` | Kelompok | `(ab)+` cocok dengan `"ab", "abab", "ababab"` |

---

# **4. Fungsi-Fungsi Utama dalam `re`**

## **4.1. `re.search()` - Mencari Pola dalam String**
Fungsi `re.search()` digunakan untuk mencari pola pertama yang cocok dalam sebuah string.

```python
import re

text = "Halo, nama saya Budi dan saya berumur 25 tahun."
match = re.search(r"\d+", text)

if match:
    print("Ditemukan:", match.group())  # Output: 25
```
✅ Menggunakan `\d+` untuk mencari angka dalam teks  

---

## **4.2. `re.findall()` - Mencari Semua Pola dalam String**
Fungsi `re.findall()` mengembalikan daftar semua kecocokan yang ditemukan.

```python
text = "Saya punya 3 kucing, 5 anjing, dan 2 burung."
matches = re.findall(r"\d+", text)

print(matches)  # Output: ['3', '5', '2']
```
✅ Menggunakan `\d+` untuk mencari semua angka dalam teks  

---

## **4.3. `re.match()` - Mencocokkan Pola di Awal String**
Fungsi `re.match()` hanya cocok jika pola ditemukan di awal string.

```python
text = "Python adalah bahasa pemrograman."
match = re.match(r"Python", text)

if match:
    print("Cocok!")  # Output: Cocok!
```
✅ `re.match()` hanya cocok jika `"Python"` ada di awal string  

---

## **4.4. `re.split()` - Membagi String Berdasarkan Pola**
Fungsi `re.split()` membagi string berdasarkan pola tertentu.

```python
text = "apel, jeruk; mangga - pisang"
result = re.split(r"[,\s;-]+", text)

print(result)  # Output: ['apel', 'jeruk', 'mangga', 'pisang']
```
✅ Memisahkan string berdasarkan koma, spasi, titik koma, dan tanda hubung  

---

## **4.5. `re.sub()` - Mengganti Teks Berdasarkan Pola**
Fungsi `re.sub()` digunakan untuk mengganti teks yang cocok dengan pola tertentu.

```python
text = "Harga lama: Rp 100.000, Harga baru: Rp 150.000"
result = re.sub(r"\d+\.\d+", "XXX", text)

print(result)  # Output: Harga lama: Rp XXX, Harga baru: Rp XXX
```
✅ Menggunakan `\d+\.\d+` untuk mengganti angka dengan "XXX"  

---

# **5. Contoh Penggunaan RegEx dalam Kehidupan Nyata**

### **5.1. Validasi Alamat Email**
```python
def is_valid_email(email):
    pattern = r"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$"
    return re.match(pattern, email) is not None

print(is_valid_email("user@example.com"))  # Output: True
print(is_valid_email("user@com"))  # Output: False
```
✅ Memastikan email memiliki format yang benar  

---

### **5.2. Validasi Nomor Telepon**
```python
def is_valid_phone(phone):
    pattern = r"^\+?62\d{9,12}$"
    return re.match(pattern, phone) is not None

print(is_valid_phone("+6281234567890"))  # Output: True
print(is_valid_phone("081234567890"))  # Output: False
```
✅ Memastikan nomor telepon dalam format Indonesia (`+62xxxxxxx`)  

---

### **5.3. Ekstraksi Hashtag dari Teks**
```python
text = "Hari ini sangat menyenangkan! #happy #fun #python"
hashtags = re.findall(r"#\w+", text)

print(hashtags)  # Output: ['#happy', '#fun', '#python']
```
✅ Menggunakan `#\w+` untuk mengekstrak semua hashtag dalam teks  

---

# **6. Menggunakan `re.compile()` untuk Efisiensi**  
Jika pola akan digunakan berkali-kali, lebih efisien menggunakan `re.compile()`.

```python
pattern = re.compile(r"\d+")
text = "Umur saya 25 tahun dan kakak saya 30 tahun."

print(pattern.findall(text))  # Output: ['25', '30']
```
✅ `re.compile()` mempercepat pencocokan karena tidak perlu membuat ulang pola setiap kali  

---

# **7. Flags dalam `re` untuk Modifikasi Pencocokan**
| Flag | Keterangan | Contoh |
|------|-----------|--------|
| `re.IGNORECASE` / `re.I` | Tidak membedakan huruf besar/kecil | `re.search("hello", "HELLO", re.I)` |
| `re.MULTILINE` / `re.M` | Cocokkan di beberapa baris | `re.search("^Hello", text, re.M)` |
| `re.DOTALL` / `re.S` | `.` cocok dengan newline | `re.search("a.*b", "a\nb", re.S)` |

---

# **8. Kesimpulan**  
Modul `re` sangat penting untuk pemrosesan teks dalam Python. Beberapa hal yang telah dipelajari:  
✅ **Pencarian teks dengan `re.search()`, `re.findall()`, `re.match()`**  
✅ **Manipulasi teks dengan `re.split()` dan `re.sub()`**  
✅ **Validasi data seperti email dan nomor telepon**  
✅ **Optimasi pencocokan dengan `re.compile()`**  
✅ **Penggunaan flags untuk fleksibilitas pencocokan**  

Memahami **Regular Expressions (`re`)** sangat berguna dalam pengolahan teks, **web scraping, validasi input, dan NLP (Natural Language Processing)!**
