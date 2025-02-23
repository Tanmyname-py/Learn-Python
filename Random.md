# PYTHON RANDOM 

## **1. Pendahuluan**  
Modul `random` dalam Python adalah modul standar yang digunakan untuk menghasilkan angka acak. Modul ini sering digunakan dalam:  
✅ Simulasi dan pemodelan probabilitas  
✅ Pembuatan data acak  
✅ Permainan (game development)  
✅ Pemilihan elemen secara acak dari suatu koleksi  

---

## **2. Cara Menggunakan Library `random`**  
Untuk menggunakan modul `random`, kita perlu mengimpornya terlebih dahulu:  
```python
import random
```

---

# **3. Fungsi-Fungsi Utama dalam `random`**

## **3.1. Menghasilkan Angka Acak**
### **`random.random()` - Menghasilkan Angka Acak antara 0 dan 1**  
```python
print(random.random())  # Contoh output: 0.7283
```
✅ Menghasilkan angka floating-point antara `0.0` hingga `1.0`  

### **`random.uniform(a, b)` - Menghasilkan Angka Acak dalam Rentang Tertentu**
```python
print(random.uniform(10, 20))  # Contoh output: 15.234
```
✅ Menghasilkan angka floating-point antara `a` dan `b`  

### **`random.randint(a, b)` - Menghasilkan Bilangan Bulat Acak**
```python
print(random.randint(1, 10))  # Contoh output: 7
```
✅ Menghasilkan bilangan bulat antara `a` dan `b` (termasuk `b`)  

### **`random.randrange(start, stop, step)` - Menghasilkan Bilangan Bulat Acak dengan Langkah Tertentu**
```python
print(random.randrange(1, 10, 2))  # Contoh output: 3, 5, atau 9
```
✅ Menghasilkan bilangan bulat dalam rentang tertentu dengan langkah tertentu  

---

## **3.2. Pemilihan Elemen Acak dari Koleksi**
### **`random.choice(sequence)` - Memilih Satu Elemen Secara Acak**
```python
names = ["Alice", "Bob", "Charlie", "David"]
print(random.choice(names))  # Contoh output: "Charlie"
```
✅ Memilih satu elemen dari list atau tuple  

### **`random.choices(sequence, k=n)` - Memilih Beberapa Elemen dengan Pengulangan**
```python
print(random.choices(names, k=2))  # Contoh output: ['Alice', 'Alice']
```
✅ Memilih `k` elemen dengan kemungkinan elemen yang sama terpilih lebih dari sekali  

### **`random.sample(sequence, k=n)` - Memilih Beberapa Elemen Tanpa Pengulangan**
```python
print(random.sample(names, k=2))  # Contoh output: ['Bob', 'David']
```
✅ Memilih `k` elemen **tanpa pengulangan**  

---

## **3.3. Mengacak Urutan Elemen**
### **`random.shuffle(sequence)` - Mengacak Urutan Elemen dalam List**
```python
numbers = [1, 2, 3, 4, 5]
random.shuffle(numbers)
print(numbers)  # Contoh output: [4, 1, 3, 5, 2]
```
✅ Mengubah urutan elemen dalam list secara acak  

---

## **3.4. Distribusi Probabilitas**
### **`random.gauss(mu, sigma)` - Distribusi Normal (Gaussian)**
```python
print(random.gauss(0, 1))  # Contoh output: -0.4769
```
✅ `mu` adalah rata-rata dan `sigma` adalah standar deviasi  

### **`random.expovariate(lambda)` - Distribusi Eksponensial**
```python
print(random.expovariate(1.5))  # Contoh output: 0.4231
```
✅ Digunakan dalam pemodelan probabilitas eksponensial  

### **`random.betavariate(alpha, beta)` - Distribusi Beta**
```python
print(random.betavariate(0.5, 0.5))  # Contoh output: 0.672
```
✅ Digunakan dalam analisis Bayesian  

---

# **4. Mengatur Seed untuk Reproduksi Hasil Acak**
Untuk memastikan hasil acak dapat direproduksi (misalnya dalam pengujian), gunakan `random.seed()`.  
```python
random.seed(42)
print(random.random())  # Selalu menghasilkan angka yang sama jika seed sama
```
✅ Menggunakan seed yang sama akan menghasilkan angka acak yang sama setiap kali  

---

# **5. Contoh Penggunaan dalam Kehidupan Nyata**
## **5.1. Simulasi Pelemparan Dadu**
```python
def roll_dice():
    return random.randint(1, 6)

print(roll_dice())  # Contoh output: 3
```
✅ Menggunakan `random.randint(1, 6)` untuk mensimulasikan dadu  

---

## **5.2. Pemilihan Pemenang Undian**
```python
participants = ["A", "B", "C", "D", "E"]
winner = random.choice(participants)
print(f"Pemenangnya adalah: {winner}")
```
✅ Menggunakan `random.choice()` untuk memilih pemenang  

---

## **5.3. Simulasi Pengacakan Soal Ujian**
```python
questions = ["Q1", "Q2", "Q3", "Q4", "Q5"]
random.shuffle(questions)
print(questions)
```
✅ Menggunakan `random.shuffle()` untuk mengacak urutan soal  

---

## **5.4. Simulasi Pemilihan Tim Secara Acak**
```python
players = ["Alice", "Bob", "Charlie", "David", "Eve", "Frank"]
team = random.sample(players, k=3)
print("Tim terpilih:", team)
```
✅ Menggunakan `random.sample()` untuk memilih tim tanpa duplikasi  

---

# **6. Perbandingan Fungsi `random`**
| Fungsi | Keterangan | Contoh Output |
|--------|-----------|--------------|
| `random.random()` | Angka float antara `0.0` - `1.0` | `0.7283` |
| `random.uniform(a, b)` | Angka float antara `a` dan `b` | `15.234` |
| `random.randint(a, b)` | Bilangan bulat antara `a` dan `b` | `7` |
| `random.choice(sequence)` | Memilih 1 elemen dari list | `'Alice'` |
| `random.choices(sequence, k=n)` | Memilih `n` elemen (boleh duplikat) | `['Alice', 'Alice']` |
| `random.sample(sequence, k=n)` | Memilih `n` elemen (tanpa duplikat) | `['Bob', 'David']` |
| `random.shuffle(sequence)` | Mengacak elemen dalam list | `[4, 1, 3, 5, 2]` |
| `random.gauss(mu, sigma)` | Angka dengan distribusi normal | `-0.4769` |

---

# **7. Kesimpulan**  
Modul `random` sangat berguna dalam berbagai keperluan pemrograman. Beberapa hal yang telah dipelajari:  
✅ **Menghasilkan angka acak (bilangan bulat, float, dan distribusi probabilitas)**  
✅ **Memilih elemen acak dari list**  
✅ **Mengacak urutan elemen dalam list**  
✅ **Menggunakan `random.seed()` untuk reproduksi hasil acak**  

Modul ini sering digunakan dalam **game development, simulasi probabilitas, pengujian, dan data sampling!**
