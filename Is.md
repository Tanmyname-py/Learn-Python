Sepertinya Anda mengacu pada metode string seperti `.islower()`, `.isupper()`, `.isdigit()`, dll. Berikut adalah **daftar lengkap** metode yang diawali dengan **"is"** dalam Python, beserta penjelasan dan contohnya.  

---

# **1. Daftar Lengkap Metode "is" dalam Python**
Berikut adalah metode yang umum digunakan untuk mengecek kondisi dalam string, angka, dan karakter:

| Metode | Kegunaan | Contoh |
|--------|---------|--------|
| `islower()` | Apakah semua huruf kecil? | `"python".islower()` → `True` |
| `isupper()` | Apakah semua huruf besar? | `"PYTHON".isupper()` → `True` |
| `isdigit()` | Apakah semua karakter angka? | `"1234".isdigit()` → `True` |
| `isalpha()` | Apakah semua karakter huruf? | `"Python".isalpha()` → `True` |
| `isalnum()` | Apakah semua karakter huruf atau angka? | `"Python123".isalnum()` → `True` |
| `isspace()` | Apakah hanya terdiri dari spasi? | `"   ".isspace()` → `True` |
| `istitle()` | Apakah setiap kata dimulai dengan huruf besar? | `"Hello World".istitle()` → `True` |
| `isidentifier()` | Apakah valid sebagai nama variabel? | `"my_var".isidentifier()` → `True` |
| `isdecimal()` | Apakah hanya terdiri dari angka desimal? | `"123".isdecimal()` → `True` |
| `isnumeric()` | Apakah semua karakter angka (termasuk pecahan dan pangkat)? | `"⅔".isnumeric()` → `True` |
| `isprintable()` | Apakah semua karakter dapat dicetak? | `"Hello\n".isprintable()` → `False` |

---

# **2. Penjelasan dan Contoh Lengkap**

## **2.1. `.islower()` → Apakah semua huruf kecil?**
Metode ini mengecek apakah semua huruf dalam string adalah huruf kecil (`a-z`).

```python
print("python".islower())   # True
print("Python".islower())   # False (karena ada huruf besar)
print("python123".islower()) # True (angka diabaikan)
print("python!".islower())  # True (simbol diabaikan)
```

---

## **2.2. `.isupper()` → Apakah semua huruf besar?**
Metode ini mengecek apakah semua huruf dalam string adalah huruf besar (`A-Z`).

```python
print("PYTHON".isupper())  # True
print("Python".isupper())  # False (karena ada huruf kecil)
print("PYTHON123".isupper())  # True (angka diabaikan)
print("PYTHON!".isupper())  # True (simbol diabaikan)
```

---

## **2.3. `.isdigit()` → Apakah semua karakter angka?**
Metode ini mengecek apakah string hanya berisi angka (`0-9`).

```python
print("12345".isdigit())  # True
print("123a".isdigit())   # False (karena ada huruf)
print("½".isdigit())      # False (karena bukan angka standar 0-9)
```

---

## **2.4. `.isalpha()` → Apakah semua karakter huruf?**
Metode ini mengecek apakah string hanya berisi huruf (`a-z`, `A-Z`) tanpa angka atau simbol.

```python
print("Python".isalpha())  # True
print("Python123".isalpha())  # False (ada angka)
print("Hello!".isalpha())  # False (ada tanda seru)
```

---

## **2.5. `.isalnum()` → Apakah semua karakter huruf atau angka?**
Metode ini mengecek apakah string hanya terdiri dari huruf dan angka (`a-z`, `A-Z`, `0-9`).

```python
print("Python123".isalnum())  # True
print("Python!".isalnum())   # False (ada tanda seru)
print("123".isalnum())       # True
print(" ".isalnum())         # False (karena hanya spasi)
```

---

## **2.6. `.isspace()` → Apakah hanya terdiri dari spasi?**
Metode ini mengecek apakah string hanya terdiri dari spasi (`" "`), tab (`"\t"`), atau newline (`"\n"`).

```python
print("   ".isspace())  # True
print("\t".isspace())   # True
print("Hello World".isspace())  # False (karena ada huruf)
```

---

## **2.7. `.istitle()` → Apakah setiap kata diawali huruf besar?**
Metode ini mengecek apakah string dalam format **Title Case** (Setiap kata diawali huruf besar).

```python
print("Hello World".istitle())  # True
print("hello world".istitle())  # False
print("Hello world".istitle())  # False
```

---

## **2.8. `.isidentifier()` → Apakah string valid sebagai nama variabel?**
Metode ini mengecek apakah string bisa digunakan sebagai **nama variabel Python**.

```python
print("my_var".isidentifier())  # True
print("123abc".isidentifier())  # False (karena dimulai dengan angka)
print("my-var".isidentifier())  # False (karena ada tanda hubung)
print("_myVar".isidentifier())  # True (underscore boleh di awal)
```

---

## **2.9. `.isdecimal()` → Apakah hanya terdiri dari angka desimal?**
Metode ini mengecek apakah string hanya berisi angka desimal (`0-9`), tanpa simbol atau pecahan.

```python
print("123".isdecimal())   # True
print("½".isdecimal())     # False (bukan angka desimal)
print("123.45".isdecimal()) # False (karena ada titik desimal)
```

---

## **2.10. `.isnumeric()` → Apakah semua karakter angka (termasuk pecahan dan pangkat)?**
Metode ini mirip dengan `.isdigit()`, tetapi juga mengenali **angka non-Arabic** seperti pecahan (`½`) dan pangkat (`²`).

```python
print("123".isnumeric())  # True
print("½".isnumeric())    # True
print("⅔".isnumeric())    # True
print("123.45".isnumeric()) # False (karena ada titik)
```

---

## **2.11. `.isprintable()` → Apakah semua karakter dapat dicetak?**
Metode ini mengecek apakah semua karakter dalam string dapat dicetak (bukan karakter kontrol seperti `\n`, `\t`).

```python
print("Hello World".isprintable())  # True
print("Hello\nWorld".isprintable()) # False (karena ada newline)
print("123".isprintable())          # True
```

---

# **3. Kesimpulan**  
✅ Metode `is` dalam Python digunakan untuk **validasi string** berdasarkan karakter yang dikandungnya.  
✅ Berguna untuk **validasi input pengguna** dalam aplikasi berbasis teks.  
✅ Metode ini sering digunakan dalam **pemrosesan string dan validasi data** di program Python.  

Menggunakan metode `is` dengan benar akan membantu dalam **filtering data dan keamanan input**, terutama dalam **form validation, parsing data, dan text processing**!
