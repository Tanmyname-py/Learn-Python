# PYTHON MATH

## **1. Pendahuluan**  
Modul `math` dalam Python adalah modul standar yang menyediakan berbagai fungsi matematika tingkat tinggi seperti operasi aritmetika, trigonometri, logaritma, eksponensial, dan konstanta matematika. Modul ini sangat berguna dalam berbagai bidang seperti data science, machine learning, fisika, dan teknik.  

### **Cara Menggunakan Library `math`**  
Untuk menggunakan `math`, kita harus mengimpornya terlebih dahulu:  
```python
import math
```

---

# **2. Konstanta dalam `math`**  
Modul `math` memiliki beberapa konstanta penting yang sering digunakan:  

| Konstanta | Keterangan | Nilai |
|-----------|-----------|--------|
| `math.pi` | Nilai π (pi) | 3.141592653589793 |
| `math.e` | Bilangan Euler | 2.718281828459045 |
| `math.tau` | Tau (2π) | 6.283185307179586 |
| `math.inf` | Infinity (tak hingga) | ∞ |
| `math.nan` | Not a Number (NaN) | - |

### **Contoh Penggunaan Konstanta**  
```python
import math

print(math.pi)   # Output: 3.141592653589793
print(math.e)    # Output: 2.718281828459045
print(math.inf)  # Output: inf
print(math.nan)  # Output: nan
```

---

# **3. Operasi Dasar Matematika**
### **3.1. Pembulatan dan Truncation**
| Fungsi | Keterangan | Contoh |
|--------|-----------|--------|
| `math.ceil(x)` | Membulatkan ke atas | `math.ceil(4.2) → 5` |
| `math.floor(x)` | Membulatkan ke bawah | `math.floor(4.9) → 4` |
| `math.trunc(x)` | Menghilangkan desimal | `math.trunc(4.9) → 4` |
| `round(x, n)` | Membulatkan ke n desimal | `round(4.567, 2) → 4.57` |

```python
print(math.ceil(4.2))   # Output: 5
print(math.floor(4.9))  # Output: 4
print(math.trunc(4.9))  # Output: 4
print(round(4.567, 2))  # Output: 4.57
```

---

### **3.2. Pangkat dan Akar**
| Fungsi | Keterangan | Contoh |
|--------|-----------|--------|
| `math.sqrt(x)` | Akar kuadrat | `math.sqrt(25) → 5` |
| `math.pow(x, y)` | Pangkat | `math.pow(2, 3) → 8.0` |
| `math.exp(x)` | e^x | `math.exp(2) → 7.389` |

```python
print(math.sqrt(25))   # Output: 5.0
print(math.pow(2, 3))  # Output: 8.0
print(math.exp(2))     # Output: 7.38905609893065
```

---

### **3.3. Logaritma**
| Fungsi | Keterangan | Contoh |
|--------|-----------|--------|
| `math.log(x)` | Logaritma natural (ln) | `math.log(10) → 2.302` |
| `math.log(x, base)` | Logaritma basis tertentu | `math.log(8, 2) → 3.0` |
| `math.log10(x)` | Logaritma basis 10 | `math.log10(100) → 2` |
| `math.log2(x)` | Logaritma basis 2 | `math.log2(8) → 3` |

```python
print(math.log(10))      # Output: 2.302585092994046
print(math.log(8, 2))    # Output: 3.0
print(math.log10(100))   # Output: 2.0
print(math.log2(8))      # Output: 3.0
```

---

# **4. Operasi Trigonometri**
| Fungsi | Keterangan | Contoh |
|--------|-----------|--------|
| `math.sin(x)` | Sinus | `math.sin(math.pi/2) → 1.0` |
| `math.cos(x)` | Kosinus | `math.cos(math.pi) → -1.0` |
| `math.tan(x)` | Tangen | `math.tan(math.pi/4) → 1.0` |
| `math.asin(x)` | Arcsin | `math.asin(1) → 1.57` |
| `math.acos(x)` | Arccos | `math.acos(0) → 1.57` |
| `math.atan(x)` | Arctan | `math.atan(1) → 0.78` |
| `math.radians(x)` | Konversi derajat ke radian | `math.radians(180) → 3.14` |
| `math.degrees(x)` | Konversi radian ke derajat | `math.degrees(math.pi) → 180.0` |

```python
print(math.sin(math.pi/2))  # Output: 1.0
print(math.cos(math.pi))    # Output: -1.0
print(math.tan(math.pi/4))  # Output: 1.0
print(math.degrees(math.pi)) # Output: 180.0
print(math.radians(180))    # Output: 3.141592653589793
```

---

# **5. Operasi Kombinatorik dan Statistik**
| Fungsi | Keterangan | Contoh |
|--------|-----------|--------|
| `math.factorial(x)` | Faktorial | `math.factorial(5) → 120` |
| `math.gcd(x, y)` | FPB (Greatest Common Divisor) | `math.gcd(48, 18) → 6` |
| `math.lcm(x, y)` | KPK (Least Common Multiple) | `math.lcm(4, 6) → 12` |

```python
print(math.factorial(5))  # Output: 120
print(math.gcd(48, 18))   # Output: 6
print(math.lcm(4, 6))     # Output: 12
```

---

# **6. Operasi Floating-Point**
| Fungsi | Keterangan | Contoh |
|--------|-----------|--------|
| `math.fmod(x, y)` | Sisa pembagian (lebih akurat dari `%`) | `math.fmod(10, 3) → 1.0` |
| `math.isfinite(x)` | Apakah x bukan inf atau NaN | `math.isfinite(math.inf) → False` |
| `math.isnan(x)` | Apakah x NaN | `math.isnan(math.nan) → True` |

```python
print(math.fmod(10, 3))     # Output: 1.0
print(math.isfinite(100))   # Output: True
print(math.isnan(math.nan)) # Output: True
```

---

# **7. Kesimpulan**  
Modul `math` dalam Python menyediakan banyak fungsi matematika yang berguna untuk berbagai keperluan, termasuk:  
✅ **Operasi dasar matematika (pembulatan, pangkat, akar, logaritma)**  
✅ **Fungsi trigonometri (sinus, kosinus, tangen)**  
✅ **Operasi kombinatorik dan statistik (faktorial, FPB, KPK)**  
✅ **Operasi floating-point (modulo, validasi angka)**  

Memahami modul `math` sangat penting dalam **pemrograman ilmiah, analisis data, machine learning, dan teknik!**
