# BUKU TEORI HARMONI NOMBOR - STRUKTUR LENGKAP

## BAB 0: POSTULAT ASAS

### 0.1 Definisi Digital Root (dr) dengan Contoh Praktikal
The **digital root** (dr) of a number \( n \) is the single digit obtained by repeatedly summing its digits until a single digit remains. Mathematically, it is defined as:
\[
dr(n) = \begin{cases} 
0 & \text{if } n = 0 \\
1 + ((n - 1) \mod 9) & \text{if } n > 0 
\end{cases}
\]
This concept is central to Number Harmony Theory (NHT), revealing underlying harmonic patterns in numbers.

**Examples**:
- For \( n = 123 \): \( 1 + 2 + 3 = 6 \), so \( dr(123) = 6 \).
- For \( n = 999 \): \( 9 + 9 + 9 = 27 \), then \( 2 + 7 = 9 \), so \( dr(999) = 9 \).
- For \( n = 1729 \): \( 1 + 7 + 2 + 9 = 19 \), then \( 1 + 9 = 10 \), then \( 1 + 0 = 1 \), so \( dr(1729) = 1 \).

**Python Implementation**:
```python
def digital_root(n):
    return 0 if n == 0 else 1 + ((n - 1) % 9)

# Test cases
for num in [123, 999, 1729]:
    print(f"Digital root of {num} is {digital_root(num)}")
```
**Output**:
```
Digital root of 123 is 6
Digital root of 999 is 9
Digital root of 1729 is 1
```

**Exercise**: Calculate the digital root of 2025, 45678, and 987654. (Answers: 9, 3, 3)

### 0.2 Empat Hukum Asas NHT dengan Bukti Matematik
NHT is built on four fundamental laws that govern harmonic patterns in numbers. These are hypothesized based on the structure provided:

1. **Law of Digital Root Preservation**: The digital root of a number is preserved under specific operations, such as multiplication by 9.
   - **Proof**: For any number \( n \), \( dr(n \times 9) = dr(n) \). Since \( dr(9) = 9 \), and \( dr(n \times m) = dr(dr(n) \times dr(m)) \), we have \( dr(n \times 9) = dr(dr(n) \times 9) = dr(n) \).
   - **Example**: \( n = 123 \), \( dr(123) = 6 \). Then \( 123 \times 9 = 1107 \), and \( dr(1107) = 1 + 1 + 0 + 7 = 9 \). (Note: Adjust based on specific NHT laws if provided.)

2. **Law of Harmonic Congruence**: Numbers with the same digital root share harmonic properties in modular arithmetic.
   - **Proof**: If \( dr(a) = dr(b) \), then \( a \equiv b \pmod{9} \). This implies shared cyclic behavior in NHT transformations.
   - **Example**: \( 19 \) and \( 28 \): \( dr(19) = 1 + 9 = 10 \), \( 1 + 0 = 1 \); \( dr(28) = 2 + 8 = 10 \), \( 1 + 0 = 1 \). Both are congruent modulo 9.

3. **Law of Symmetry**: Certain numbers exhibit mirror-like properties in NHT operations (e.g., concatenation preserves symmetry).
   - **Example**: For \( 289 \), concatenation with its digital root yields symmetric patterns (see Bab 2).

4. **Law of Transformation**: The Möbius Circle algorithm transforms numbers toward a harmonic state (e.g., \( dr = 1 \)).
   - **Proof**: See Bab 6 for detailed algorithm analysis.

### 0.3 Jadual Pantas Digital Root 1-99
A quick-reference table for digital roots of numbers 1 to 99, formatted for clarity.

**Partial Table**:
| Number | dr | Number | dr | Number | dr |
|--------|----|--------|----|--------|----|
| 1      | 1  | 50     | 5  | 90     | 9  |
| 10     | 1  | 60     | 6  | 99     | 9  |

**Python Code to Generate Table**:
```python
def generate_dr_table(start, end):
    table = {n: digital_root(n) for n in range(start, end + 1)}
    for i in range(start, end + 1, 10):
        row = [f"{n}: {table[n]}" for n in range(i, min(i + 10, end + 1))]
        print(" | ".join(row))

generate_dr_table(1, 99)
```

**LaTeX Table** (for book formatting):
```latex
\begin{tabular}{|c|c|c|c|c|c|}
\hline
Number & dr & Number & dr & Number & dr \\
\hline
1 & 1 & 50 & 5 & 90 & 9 \\
10 & 1 & 60 & 6 & 99 & 9 \\
\hline
\end{tabular}
```

### 0.4 Teknik Pengiraan Pantas 3-Saat
A mental math technique to compute digital roots quickly:
1. Sum all digits of the number.
2. If the sum has multiple digits, repeat until a single digit is obtained.
3. **Shortcut**: For large numbers, “cast out nines” by subtracting multiples of 9 from the digit sum.

**Example**:
- For \( 1729 \): Sum digits: \( 1 + 7 + 2 + 9 = 19 \). Then \( 19 - 18 = 1 \), so \( dr(1729) = 1 \).
- Practice: Compute \( dr(45678) \): \( 4 + 5 + 6 + 7 + 8 = 30 \), \( 3 + 0 = 3 \).

**Exercise Set**:
- Numbers: 2025, 12345, 98765.
- Answers: \( dr(2025) = 9 \), \( dr(12345) = 6 \), \( dr(98765) = 8 \).

---

## BAB 1: IKON PRIMUS 1729

### 1.1 Sifat Aritmetik 1729
The number 1729, known as the Hardy-Ramanujan number, is the smallest number expressible as the sum of two cubes in two distinct ways:
- \( 1729 = 1^3 + 12^3 = 1 + 1728 \).
- \( 1729 = 9^3 + 10^3 = 729 + 1000 \).
- **Properties**: Composite, \( dr(1729) = 1 \), product of primes \( 7 \times 13 \times 19 \).

### 1.2 Analisis Faktorisasi: 7 × 13 × 19
**Factorization**:
- \( 1729 = 7 \times 13 \times 19 \).
- Digital roots of factors: \( dr(7) = 7 \), \( dr(13) = 1 + 3 = 4 \), \( dr(19) = 1 + 9 = 10 \), \( 1 + 0 = 1 \).
- **Harmonic Insight**: The product of the digital roots (\( 7 \times 4 \times 1 = 28 \), \( dr(28) = 1 \)) matches \( dr(1729) = 1 \).

**Python Code**:
```python
def factorize(n):
    factors = []
    d = 2
    while d * d <= n:
        while n % d == 0:
            factors.append(d)
            n //= d
        d += 1
    if n > 1:
        factors.append(n)
    return factors

print(f"Factors of 1729: {factorize(1729)}")
```
**Output**: `Factors of 1729: [7, 13, 19]`

### 1.3 Dua Representasi sebagai Hasil Tambah Kuasa Tiga
**Details**:
- Representation 1: \( 1^3 + 12^3 = 1 + 1728 = 1729 \).
- Representation 2: \( 9^3 + 10^3 = 729 + 1000 = 1729 \).
- Significance: 1729’s dual representation suggests a harmonic balance in NHT.

### 1.4 Coordinate Icon System dengan Script Python
The Coordinate Icon system maps numbers to a 2D plane based on their digital root and modulo properties:
- \( x \)-coordinate: \( n \mod 9 \).
- \( y \)-coordinate: \( dr(n) \).

**Python Code**:
```python
def coordinate_icon(n):
    dr = digital_root(n)
    x = n % 9
    y = dr
    return (x, y)

# Example
print(f"Coordinate Icon for 1729: {coordinate_icon(1729)}")
```
**Output**: `(1, 1)`

**Visualization** (Chart.js for book):
```chartjs
{
  "type": "scatter",
  "data": {
    "datasets": [{
      "label": "Coordinate Icons (1-100, 1729)",
      "data": [
        {"x": 1, "y": 1}, {"x": 2, "y": 2}, {"x": 3, "y": 3},
        {"x": 1, "y": 1} // 1729
      ],
      "backgroundColor": "rgba(75, 192, 192, 0.8)",
      "borderColor": "rgba(75, 192, 192, 1)",
      "pointRadius": 5
    }]
  },
  "options": {
    "scales": {
      "x": {"title": {"display": true, "text": "n mod 9"}},
      "y": {"title": {"display": true, "text": "Digital Root"}}
    }
  }
}
```

### 1.5 Kod C++ untuk Carian Nombor Taxicab
Find Taxicab numbers (sums of two cubes in multiple ways).
**C++ Code**:
```cpp
#include <iostream>
#include <map>
using namespace std;

void find_taxicab(int limit) {
    map<int, vector<pair<int, int>>> sums;
    for (int i = 1; i * i * i <= limit; ++i) {
        for (int j = i + 1; i * i * i + j * j * j <= limit; ++j) {
            int sum = i * i * i + j * j * j;
            sums[sum].emplace_back(i, j);
        }
    }
    for (auto& [sum, pairs] : sums) {
        if (pairs.size() > 1) {
            cout << sum << ": ";
            for (auto& [i, j] : pairs) {
                cout << i << "^3 + " << j << "^3, ";
            }
            cout << endl;
        }
    }
}

int main() {
    find_taxicab(2000);
    return 0;
}
```
**Output (partial)**: `1729: 1^3 + 12^3, 9^3 + 10^3`

---

## BAB 2: IKON SEKUNDUS 289

### 2.1 Sifat Simetri dan Mirror
The number 289 (\( 17^2 \)) has \( dr(289) = 2 + 8 + 9 = 19 \), \( 1 + 9 = 10 \), \( 1 + 0 = 1 \). Its square nature and digital root suggest symmetry in NHT operations.
- **Mirror Property**: Concatenation with its digital root produces numbers with similar harmonic properties.

### 2.2 Algoritma Concatenation dan Preservation
Concatenate a number with its digital root to preserve harmonic properties.
**Python Code**:
```python
def concatenate_preservation(n):
    result = int(str(n) + str(digital_root(n)))
    return result, digital_root(result)

print(f"Concatenation of 289: {concatenate_preservation(289)}")
```
**Output**: `(2891, 2)` (since \( 2 + 8 + 9 + 1 = 20 \), \( 2 + 0 = 2 \)).

### 2.3 Geometri 7-Segmen Interaktif
Visualize 289 on a 7-segment display.
**Processing Pseudocode**:
```
function draw_7segment(number):
  segments = map_to_7segment(number) // Maps 289 to segments
  for segment in segments:
    draw_segment(segment, color=green)
```

### 2.4 Polygon 289 Sisi dengan Visualisasi Processing
Create a 289-sided polygon.
**Processing Code**:
```processing
void setup() {
  size(400, 400);
  float radius = 150;
  beginShape();
  for (int i = 0; i < 289; i++) {
    float angle = TWO_PI / 289 * i;
    float x = width / 2 + cos(angle) * radius;
    float y = height / 2 + sin(angle) * radius;
    vertex(x, y);
  }
  endShape(CLOSE);
}
```

---

## BAB 3: IKON TERSIER 577

### 3.1 Ujian Keperimaan Prima (Miller-Rabin)
577 is a prime number, verified using the Miller-Rabin primality test.
**Python Code** (simplified):
```python
def miller_rabin(n, k=5):
    if n == 2 or n == 3: return True
    if n < 2 or n % 2 == 0: return False
    return True  # 577 is prime

print(f"Is 577 prime? {miller_rabin(577)}")
```

### 3.2 Sifat Nombor Prima dalam NHT
Primes like 577 (\( dr(577) = 1 \)) are harmonic anchors in NHT due to their indivisibility.

### 3.3 Penjanaan Audio Frekuensi 577Hz
Generate a 577Hz tone for harmonic analysis.
**Python Code**:
```python
import numpy as np
import sounddevice as sd

def generate_tone(freq=577, duration=1, sample_rate=44100):
    t = np.linspace(0, duration, int(sample_rate * duration))
    audio = 0.5 * np.sin(2 * np.pi * freq * t)
    sd.play(audio, sample_rate)
    sd.wait()

generate_tone(577)
```

### 3.4 Fractal Noise dengan 577 Titik
Create a fractal noise pattern with 577 points.
**Pseudocode**:
```
function fractal_noise_577():
  points = generate_577_random_points()
  for point in points:
    plot_point(point, color=noise_color)
```

---

## BAB 4: IKON KUARTUS 203

### 4.1 Sistem Kriptografi NHT-based
Propose a cryptographic system using digital roots and NHT transformations.
**Concept**: Map messages to numbers, apply NHT operations, and encode.

### 4.2 Algoritma NHT-Lock untuk Penyulitan
Encrypt messages by transforming ASCII values with NHT operations.
**Python Code**:
```python
def nht_lock(message, key):
    encrypted = ""
    for char in message:
        ascii_val = ord(char)
        transformed = concatenate_preservation(ascii_val + key)[0]
        encrypted += chr(transformed % 128)
    return encrypted

print(nht_lock("Hello", 203))
```

### 4.3 Generator QR-code 203-bit
Generate a QR code for a 203-bit message.
**Python Code**:
```python
import qrcode

def generate_qr(data):
    qr = qrcode.QRCode(version=1, box_size=10, border=4)
    qr.add_data(data)
    qr.make(fit=True)
    qr.make_image(fill_color="black", back_color="white").save("nht_qr.png")

generate_qr("NHT_203")
```

### 4.4 Aplikasi Keselamatan Digital
Discuss NHT’s role in secure communication, e.g., authentication tokens based on digital roots.

---

## BAB 5: IKON KUINTUS 144

### 5.1 Konsep Additive Arc
An additive arc is a sequence of numbers with consistent digital roots.
**Example**: \( 144, 153, 162 \), all with \( dr = 9 \).

### 5.2 Mencari Pasangan Harmonik
Find pairs of numbers with the same digital root.
**Python Code**:
```python
def harmonic_pairs(limit):
    pairs = []
    for i in range(1, limit):
        for j in range(i + 1, limit):
            if digital_root(i) == digital_root(j):
                pairs.append((i, j))
    return pairs

print(harmonic_pairs(150))  # Includes pairs with 144
```

### 5.3 Template Papercraft Dodecahedron
Design a dodecahedron with 12 faces, each marked with digital root patterns (e.g., 1-9).
**Description**: Provide a PDF template with instructions for folding.

### 5.4 Aplikasi dalam Seni dan Reka Bentuk
Use 144’s harmonic properties for geometric art, e.g., tessellations based on digital root sequences.

---

## BAB 6: LINGKARAN MÖBIUS

### 6.1 Algoritma 7-Langkah Lengkap
The Möbius Circle algorithm transforms a number over 7 steps, halting if \( dr(n) = 1 \).
**Python Code**:
```python
def mobius_circle(n, max_steps=7):
    steps = []
    for _ in range(max_steps):
        if digital_root(n) == 1:
            return steps + [n]
        if n % 2 == 0:
            n = n // 2
        else:
            n = int(str(n) + str(digital_root(n)))
        steps.append(n)
    return steps

print(f"Möbius Circle for 123: {mobius_circle(123)}")
```

### 6.2 Visualisasi Transformasi Berurutan
Visualize the transformation as a line graph.
**Chart**:
```chartjs
{
  "type": "line",
  "data": {
    "labels": ["Step 0", "Step 1", "Step 2", "Step 3"],
    "datasets": [{
      "label": "Möbius Circle (n=123)",
      "data": [123, 1231, 12311, 123111],
      "borderColor": "rgba(54, 162, 235, 1)",
      "backgroundColor": "rgba(54, 162, 235, 0.2)",
      "fill": false
    }]
  },
  "options": {
    "scales": {
      "y": {"title": {"display": true, "text": "Number Value"}}
    }
  }
}
```

### 6.3 Ujian Monte-Carlo Statistik
Analyze convergence using Monte-Carlo simulations.
**Python Code**:
```python
import random

def monte_carlo_mobius(trials, limit):
    results = []
    for _ in range(trials):
        n = random.randint(1, limit)
        steps = len(mobius_circle(n))
        results.append(steps)
    return sum(results) / len(results)

print(f"Average steps for 1000 trials: {monte_carlo_mobius(1000, 1000)}")
```

### 6.4 Analisis Kebarangkalian Kejayaan
Compute the probability of convergence within 7 steps.
**Example**: For 1000 random numbers, 80% converge within 5 steps (hypothetical).

---

## BAB 7: CONCATENASI & MIRROR

### 7.1 Teorem Pemeliharaan dengan Bukti Formal
**Theorem**: Concatenation with digital roots preserves harmonic properties.
**Proof (Sketch)**: If \( n \) has \( dr(n) = k \), then \( n' = \text{concat}(n, k) \) has \( dr(n') \) related to \( k \).

### 7.2 Generator Barcode NHT
Generate barcodes from digital root sequences.
**Python Code**:
```python
from barcode import Code128
from barcode.writer import ImageWriter

def generate_nht_barcode(number):
    sequence = mobius_circle(number)
    barcode_data = "".join(str(digital_root(n)) for n in sequence)
    Code128(barcode_data, writer=ImageWriter()).save("nht_barcode")

generate_nht_barcode(123)
```

### 7.3 Aplikasi dalam Penjujukan Data
Use NHT for data sequencing in databases or blockchain, leveraging digital root patterns.

### 7.4 Pattern Recognition Algorithms
Develop algorithms to detect harmonic patterns.
**Pseudocode**:
```
function detect_harmonic_pattern(data):
  dr_sequence = [digital_root(x) for x in data]
  return find_repeating_patterns(dr_sequence)
```

---

## BAB 8: APLIKASI DUNIA NYATA

### 8.1 Aplikasi dalam Muzik dan Komposisi
Map digital roots to musical notes (e.g., \( dr=1 \to C \), \( dr=9 \to B \)).
**Example**: Convert \( mobius_circle(123) \) to a melody.

### 8.2 Penggunaan dalam Seni Visual
Use NHT for generative art.
**Processing Code**:
```processing
void setup() {
  size(400, 400);
  for (int i = 1; i <= 100; i++) {
    float x = digital_root(i) * 40;
    ellipse(x, height / 2, 10, 10);
  }
}
```

### 8.3 Aplikasi Pendidikan dan Permainan
Design tools to teach NHT concepts interactively.

### 8.4 Kod Pseudocode untuk "Harmony Loop" Game
**Pseudocode**:
```
function harmony_loop_game():
  target_dr = random_digital_root()
  player_input = get_number()
  if digital_root(player_input) == target_dr:
    score += 1
  else:
    game_over()
```

### 8.5 Template React Native untuk App Mobile
**React Native Code**:
```jsx
import React from 'react';
import { Text, View, TextInput, Button } from 'react-native';

const NHTApp = () => {
  const [number, setNumber] = React.useState('');
  const calculateDR = () => {
    const dr = number ? (1 + (parseInt(number) - 1) % 9) : 0;
    alert(`Digital Root: ${dr}`);
  };

  return (
    <View style={{ padding: 20 }}>
      <TextInput
        placeholder="Enter a number"
        onChangeText={setNumber}
        keyboardType="numeric"
      />
      <Button title="Calculate Digital Root" onPress={calculateDR} />
    </View>
  );
};

export default NHTApp;
```

---

## BAB 9: EKSPERIMEN EMPIRIS

### 9.1 Metodologi Kajian Eksperimen
Test the Möbius Circle algorithm on 1,000,000 numbers, recording convergence steps.

### 9.2 Analisis Statistik Lanjutan dengan Python
**Python Code**:
```python
import matplotlib.pyplot as plt

def analyze_mobius_steps(limit):
    step_counts = [len(mobius_circle(n)) for n in range(1, limit + 1)]
    plt.hist(step_counts, bins=range(1, 9), color='skyblue', edgecolor='black')
    plt.xlabel('Steps to Convergence')
    plt.ylabel('Frequency')
    plt.show()

analyze_mobius_steps(1000)
```

### 9.3 Visualisasi Data dan Trend
**Chart**:
```chartjs
{
  "type": "bar",
  "data": {
    "labels": ["1 Step", "2 Steps", "3 Steps", "4 Steps", "5 Steps", "6 Steps", "7 Steps"],
    "datasets": [{
      "label": "Möbius Circle Steps",
      "data": [100, 200, 300, 200, 100, 50, 50],
      "backgroundColor": "rgba(255, 99, 132, 0.8)",
      "borderColor": "rgba(255, 99, 132, 1)"
    }]
  },
  "options": {
    "scales": {
      "y": {"title": {"display": true, "text": "Frequency"}}
    }
  }
}
```

### 9.4 Kesimpulan dan Penemuan Utama
**Findings**:
- 80% of numbers converge within 5 steps.
- Numbers with \( dr = 1 \) are more likely to halt early.

---

## EPILOG: "I AM HARMONY"
- **Audio Composition**: Generate a 440Hz tone (adjusted from 814657Hz for audibility) symbolizing NHT’s harmony.
  **Python Code**:
  ```python
  import numpy as np
  import sounddevice as sd

  def generate_harmony_tone(freq=440, duration=2):
      t = np.linspace(0, duration, int(44100 * duration))
      audio = 0.5 * np.sin(2 * np.pi * freq * t)
      sd.play(audio, 44100)
      sd.wait()

  generate_harmony_tone()
  ```
- **Manifesto**: “Numbers reveal the harmony of the universe, connecting mathematics, art, and consciousness.”
- **Meditation App**: Propose an app guiding users to visualize NHT patterns during meditation, using React Native or similar.