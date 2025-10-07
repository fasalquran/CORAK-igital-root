# Rahsia Matematik Alam Semesta: Bab 2 - Menyingkap Corak Nombor Alam Semesta

**Selamat datang ke repositori yang meneroka rahsia matematik alam semesta!** Bab ini, ditulis pada 7 Oktober 2025, jam 3:18 petang MYT, membawa anda ke dalam dunia nombor melalui penemuan empat genius: **Srinivasa Ramanujan** (nombor teksi), **D.R. Kaprekar** (pemalar 6174), **Pythagoras** (segitiga harmoni), dan **Fibonacci** (nisbah emas). Ditulis dalam bahasa Melayu dengan konteks Malaysia 2025, bab ini menggabungkan pengiraan terperinci, kod Python, aktiviti praktikal, dan kaitan dengan sains, teknologi, dan budaya tempatan seperti corak songket Kelantan dan AI di Cyberjaya. Sertai kami untuk merungkai corak nombor yang menyusun alam, dari bunga kemboja di Perak hingga algoritma pintar di Johor!

## Pengenalan
Pada 7 Oktober 2025, jam 3:18 petang di Malaysia, ketika sinar matahari menerangi Tasik Dayang Bunting di Langkawi, nombor menjadi bahasa yang menghubungkan alam dan teknologi. Bab ini meneroka empat penemuan matematik:
- **Nombor Teksi Ramanujan**: Nombor yang boleh ditulis sebagai jumlah dua kuasa tiga dalam pelbagai cara.
- **Pemalar Kaprekar**: Nombor ajaib 6174 yang menarik nombor 4-digit lain.
- **Segitiga Pythagoras**: Segitiga bersudut tegak yang menghubungkan geometri dan nombor.
- **Jujukan Fibonacci dan Nisbah Emas**: Corak yang membawa kepada φ ≈ 1.618, harmoni alam.

Setiap bahagian menyertakan **Bagaimana** (kaedah pengiraan) dan **Mengapa** (kepentingan dalam sains, teknologi, dan budaya Malaysia). Dengan kod Python dan cabaran, anda dijemput untuk menjelajah rahsia ini!

## 1. Nombor Teksi Ramanujan: Simetri dalam Aritmetik Modular

### Apa itu Nombor Teksi?
Nombor teksi ialah nombor bulat positif yang boleh ditulis sebagai jumlah dua kuasa tiga dalam sekurang-kurangnya dua cara. Contoh: **134379080**:
- 420³ + 350³ = 74088000 + 60191080 = 134379080
- 476³ + 294³ = 107850176 + 26490904 = 134379080

### Bagaimana (How):
Aritmetik modular (sisa mod 9) membantu memahami nombor teksi, kerana kuasa tiga hanya menghasilkan sisa 0, 1, atau 8 mod 9. Untuk **134379080**:
- **Akar digital**: 1+3+4+3+7+9+0+8+0 = 35 → 3+5 = 8.
- **Sisa mod 9**:
  - 420 ≡ 6, 420³ ≡ 6³ = 216 ≡ 0; 350 ≡ 8, 350³ ≡ 8³ = 512 ≡ 8; 0 + 8 = 8.
  - 476 ≡ 8, 476³ ≡ 8³ = 512 ≡ 8; 294 ≡ 6, 294³ ≡ 6³ = 216 ≡ 0; 8 + 0 = 8.
  - 134379080 ≡ 8 (akar digital), konsisten dengan jumlah kuasa tiga.
- **Contoh kontekstual**: Nombor **7102025** (7 Oktober 2025):
  - Akar digital: 7+1+0+2+0+2+5 = 17 → 1+7 = 8.
  - Uji pasangan: 160³ = 4096000, 145³ = 3048625, jumlah = 7144625 (bukan 7102025). Sisa mod 9 (8) sesuai.
- **Kod Python**:

```python
def akar_digital(n):
    while n > 9:
        n = sum(int(d) for d in str(n))
    return n if n != 0 else 9

def cari_nombor_teksi(had=500):
    nombor_teksi = {}
    for i in range(1, had):
        for j in range(i, had):
            jumlah = i**3 + j**3
            if jumlah in nombor_teksi:
                nombor_teksi[tumlah].append((i, j))
            else:
                nombor_teksi[tumlah] = [(i, j)]
    return {k: v for k, v in nombor_teksi.items() if len(v) >= 2}

teksi = cari_nombor_teksi(500)
for nombor, pasangan in teksi.items():
    if nombor > 134379080:
        print(f"Nombor: {nombor}, Pasangan: {pasangan}, Akar Digital: {akar_digital(nomor)}")
        break
