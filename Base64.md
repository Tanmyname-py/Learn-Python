# PYTHON BASE64

## **1. Pendahuluan**  
Modul `base64` dalam Python adalah modul standar yang digunakan untuk encoding (mengubah data biner menjadi teks berbasis ASCII) dan decoding (mengubah kembali ke data biner). Base64 sering digunakan untuk:  

✅ Encoding data biner agar dapat dikirim melalui teks  
✅ Mengamankan data dalam format yang tidak mudah dibaca langsung  
✅ Digunakan dalam komunikasi HTTP (seperti Basic Authentication)  
✅ Encoding gambar atau file untuk disematkan dalam dokumen teks  

---

## **2. Cara Menggunakan Library `base64`**  
Untuk menggunakan `base64`, kita harus mengimpornya terlebih dahulu:  
```python
import base64
```

---

# **3. Encoding dan Decoding String**
### **3.1. Encoding String ke Base64**
```python
import base64

text = "Hello, Python!"
encoded_bytes = base64.b64encode(text.encode("utf-8"))
encoded_str = encoded_bytes.decode("utf-8")

print(encoded_str)  # Output: SGVsbG8sIFB5dGhvbiE=
```

**Penjelasan:**  
- `.encode("utf-8")` → Mengubah string menjadi bytes  
- `base64.b64encode()` → Mengubah bytes menjadi format Base64  
- `.decode("utf-8")` → Mengembalikan hasil encoding dalam bentuk string  

---

### **3.2. Decoding Base64 ke String**
```python
decoded_bytes = base64.b64decode(encoded_str)
decoded_str = decoded_bytes.decode("utf-8")

print(decoded_str)  # Output: Hello, Python!
```

**Penjelasan:**  
- `base64.b64decode()` → Mengubah Base64 kembali ke bytes  
- `.decode("utf-8")` → Mengubah bytes kembali ke string  

---

# **4. Encoding dan Decoding File**
### **4.1. Encoding File ke Base64**
```python
with open("image.jpg", "rb") as image_file:
    encoded_bytes = base64.b64encode(image_file.read())
    encoded_str = encoded_bytes.decode("utf-8")

print(encoded_str)  # Output: Base64 dari gambar
```

### **4.2. Decoding Base64 ke File**
```python
with open("decoded_image.jpg", "wb") as image_file:
    image_file.write(base64.b64decode(encoded_str))
```

---

# **5. Variasi Encoding Base64**
### **5.1. URL-safe Base64 Encoding**
Digunakan untuk data yang akan dikirim dalam URL (menggunakan `-` dan `_` sebagai pengganti `+` dan `/`).
```python
url_safe_encoded = base64.urlsafe_b64encode(b"Hello, World!")
print(url_safe_encoded)  # Output: SGVsbG8sIFdvcmxkIQ==

decoded = base64.urlsafe_b64decode(url_safe_encoded)
print(decoded.decode("utf-8"))  # Output: Hello, World!
```

---

### **5.2. Base32 Encoding**
Base32 menggunakan alfabet `A-Z` dan `2-7`, lebih panjang dari Base64 tetapi lebih mudah diketik secara manual.
```python
encoded = base64.b32encode(b"Hello, Python!")
print(encoded)  # Output: JBSWY3DPEBLW64TMMQQQ====

decoded = base64.b32decode(encoded)
print(decoded.decode("utf-8"))  # Output: Hello, Python!
```

---

### **5.3. Base16 Encoding**
Base16 (hexadecimal encoding), sering digunakan untuk representasi nilai biner dalam format yang mudah dibaca.
```python
encoded = base64.b16encode(b"Hello, Python!")
print(encoded)  # Output: 48656C6C6F2C20507974686F6E21

decoded = base64.b16decode(encoded)
print(decoded.decode("utf-8"))  # Output: Hello, Python!
```

---

# **6. Menggunakan Padding dalam Base64**
Base64 menggunakan padding `=` untuk memastikan panjang data selalu kelipatan 4. Jika data tidak memiliki panjang yang tepat, decoding akan gagal.

### **6.1. Menghapus Padding**
```python
encoded = base64.b64encode(b"Hello").decode("utf-8").rstrip("=")
print(encoded)  # Output: SGVsbG8
```

### **6.2. Menambahkan Padding Sebelum Decoding**
```python
def add_padding(encoded_str):
    return encoded_str + "=" * ((4 - len(encoded_str) % 4) % 4)

padded_str = add_padding("SGVsbG8")
decoded = base64.b64decode(padded_str).decode("utf-8")
print(decoded)  # Output: Hello
```

---

# **7. Keamanan dan Kelemahan Base64**
✅ **Kelebihan Base64**  
- Mudah digunakan untuk encoding data biner  
- Banyak digunakan dalam komunikasi jaringan  
- Bisa digunakan untuk menyembunyikan data secara sederhana  

❌ **Kelemahan Base64**  
- **Tidak aman untuk enkripsi**, karena dapat dengan mudah didekode  
- **Ukuran data bertambah** sekitar 33% dari ukuran aslinya  
- **Tidak efisien untuk data besar**  

---

# **8. Contoh Penggunaan Base64 dalam HTTP Authentication**
Base64 digunakan dalam HTTP Basic Authentication untuk encoding username dan password.

### **8.1. Encoding Username dan Password**
```python
credentials = "user:password"
encoded_credentials = base64.b64encode(credentials.encode("utf-8")).decode("utf-8")

print(f"Authorization: Basic {encoded_credentials}")
```
**Output:**
```
Authorization: Basic dXNlcjpwYXNzd29yZA==
```

### **8.2. Decoding Credentials**
```python
decoded_credentials = base64.b64decode(encoded_credentials).decode("utf-8")
print(decoded_credentials)  # Output: user:password
```

---

# **9. Kesimpulan**
✅ `base64` digunakan untuk encoding dan decoding data biner ke teks ASCII  
✅ Digunakan dalam komunikasi jaringan, encoding file, dan otentikasi HTTP  
✅ Base64 bukan metode enkripsi, hanya encoding sederhana  
✅ Ada berbagai varian seperti Base64, Base32, Base16, dan URL-safe Base64  
✅ Harus berhati-hati dalam mengelola padding `=` agar decoding berhasil  

Menguasai `base64` sangat penting dalam **pengolahan data, komunikasi jaringan, dan keamanan data dasar!**
