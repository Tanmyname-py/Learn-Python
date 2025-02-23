# PYTHON HASHLIB

## **1. Pendahuluan**  
Modul `hashlib` dalam Python digunakan untuk membuat **hash** dari data. Hash digunakan dalam berbagai aplikasi seperti:  
✅ Keamanan data (penyimpanan password)  
✅ Verifikasi integritas file  
✅ Kriptografi  

---

## **2. Cara Kerja `hashlib` dalam Python**  
Hash adalah nilai unik yang dihasilkan dari input data menggunakan algoritma hashing. Hash bersifat **satu arah**, artinya tidak bisa dikembalikan ke bentuk aslinya.

**Algoritma Hashing yang Didukung `hashlib`:**  
- MD5 (`md5`)  
- SHA-1 (`sha1`)  
- SHA-256 (`sha256`)  
- SHA-512 (`sha512`)  
- Dan lainnya (`sha224`, `sha384`, dll.)

Untuk menggunakan `hashlib`, kita perlu mengimpornya terlebih dahulu:  
```python
import hashlib
```

---

## **3. Membuat Hash dengan `hashlib`**  
### **3.1. Membuat Hash MD5**  
```python
hash_md5 = hashlib.md5(b"Hello, World!")  # b"" untuk data dalam bentuk byte
print(hash_md5.hexdigest())  # Output: 65a8e27d8879283831b664bd8b7f0ad4
```

### **3.2. Membuat Hash SHA-1**  
```python
hash_sha1 = hashlib.sha1(b"Hello, World!")
print(hash_sha1.hexdigest())  # Output: 2ef7bde608ce5404e97d5f042f95f89f1c232871
```

### **3.3. Membuat Hash SHA-256**  
```python
hash_sha256 = hashlib.sha256(b"Hello, World!")
print(hash_sha256.hexdigest())  # Output: c0535e4be2b79ffd93291305436bf889314e4a3faec05ecffcbb9e460c2...
```

### **3.4. Membuat Hash SHA-512**  
```python
hash_sha512 = hashlib.sha512(b"Hello, World!")
print(hash_sha512.hexdigest())  # Output: 3615f80c9d293ed7402687a3d4016f05... (panjang)
```

---

## **4. Menggunakan `update()` untuk Hash Bertahap**
`update()` memungkinkan kita membuat hash secara bertahap, misalnya saat membaca file besar.  
```python
hash_md5 = hashlib.md5()
hash_md5.update(b"Hello, ")
hash_md5.update(b"World!")
print(hash_md5.hexdigest())  # Output tetap sama: 65a8e27d8879283831b664bd8b7f0ad4
```

---

## **5. Verifikasi Hash dan Keamanan**  
### **5.1. Memeriksa Hash File**
```python
def hash_file(file_path):
    hasher = hashlib.sha256()
    with open(file_path, "rb") as file:
        while chunk := file.read(4096):
            hasher.update(chunk)
    return hasher.hexdigest()

file_hash = hash_file("example.txt")
print(file_hash)  # Output: hash SHA-256 dari file
```

### **5.2. Memeriksa Hash Password**
```python
stored_password_hash = hashlib.sha256(b"mypassword").hexdigest()
input_password_hash = hashlib.sha256(b"mypassword").hexdigest()

if stored_password_hash == input_password_hash:
    print("Password benar")
else:
    print("Password salah")
```

---

## **6. HMAC (Hash-based Message Authentication Code)**
HMAC digunakan untuk meningkatkan keamanan hashing dengan menambahkan kunci rahasia.

```python
import hmac

key = b"my_secret_key"
message = b"Hello, World!"

hmac_result = hmac.new(key, message, hashlib.sha256).hexdigest()
print(hmac_result)  # Output: hash HMAC-SHA256
```

---

## **7. Daftar Algoritma yang Didukung**
```python
print(hashlib.algorithms_available)
```
Hasilnya bisa berisi algoritma seperti:  
`{'md5', 'sha1', 'sha256', 'sha512', 'sha3_256', 'blake2b', 'blake2s', ...}`

---

## **8. Kesimpulan**  
Modul `hashlib` sangat berguna untuk keamanan dan verifikasi data.  
✅ Mendukung berbagai algoritma hash (MD5, SHA-256, dll.)  
✅ Dapat digunakan untuk hashing string, password, dan file  
✅ Bisa digunakan untuk meningkatkan keamanan dengan HMAC  

Dengan memahami `hashlib`, kita bisa mengamankan data lebih baik di aplikasi kita!
