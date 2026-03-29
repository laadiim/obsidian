
# Lineární soustavy rovnic – **velmi podrobný studijní souhrn**

---

# 1. Základní formulace

Řešíme soustavu lineárních rovnic ve tvaru:

\[
A x = b
\]

kde:
- \(A \in \mathbb{R}^{n \times n}\) – matice koeficientů
- \(x \in \mathbb{R}^n\) – vektor neznámých
- \(b \in \mathbb{R}^n\) – pravá strana

---

# 2. Základní pojmy

## 🔹 Hodnost matice (rank)
- počet lineárně nezávislých řádků/sloupců

## 🔹 Regulární matice
\[
\det(A) \neq 0
\]
→ existuje inverze \(A^{-1}\)

## 🔹 Singulární matice
\[
\det(A) = 0
\]

---

# 3. Typy řešení soustavy

## ✔ Jednoznačné řešení
- \( \text{rank}(A) = n \)

## ✔ Nekonečně mnoho řešení
- \( \text{rank}(A) < n \)
- volné proměnné

## ❌ Žádné řešení
- \( \text{rank}(A) \neq \text{rank}(A|b) \)

---

# 4. Gaussova eliminace

## 🔹 Princip
Transformujeme soustavu na trojúhelníkový tvar.

---

## 🔹 Kroky

### 1. Dopředná eliminace
- nulujeme prvky pod diagonálou

### 2. Zpětná substituce
- dopočítáme řešení

---

## 🔹 Elementární úpravy
- prohození řádků
- násobení řádku
- přičtení násobku řádku

---

## 🔹 Pivotace

### Částečná pivotace
- vybíráme největší prvek ve sloupci

### Úplná pivotace
- vybíráme maximum v celé podmatici

---

## 🔹 Výhody / nevýhody

+ univerzální metoda  
+ přesná  
- numerické chyby  
- složitost \(O(n^3)\)

---

# 5. LU rozklad

## 🔹 Tvar
\[
A = LU
\]

kde:
- \(L\) dolní trojúhelníková
- \(U\) horní trojúhelníková

---

## 🔹 Řešení
1. \(Ly = b\)
2. \(Ux = y\)

---

## 🔹 Výhody
- rychlé opakované řešení
- využívá strukturu matice

---

# 6. Iterační metody

Používají se pro velké a řídké matice.

---

# 6.1 Jacobiho metoda

## 🔹 Vzorec
\[
x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j \neq i} a_{ij}x_j^{(k)}\right)
\]

---

## 🔹 Vlastnosti
+ jednoduchá  
+ paralelizovatelná  
- pomalejší než GS  

---

# 6.2 Gauss-Seidelova metoda

## 🔹 Vzorec
\[
x_i^{(k+1)} = \frac{1}{a_{ii}}\left(b_i - \sum_{j<i} a_{ij}x_j^{(k+1)} - \sum_{j>i} a_{ij}x_j^{(k)}\right)
\]

---

## 🔹 Vlastnosti
+ rychlejší než Jacobi  
- sekvenční výpočet  

---

# 6.3 SOR metoda (relaxační)

\[
x^{(k+1)} = (1-\omega)x^{(k)} + \omega x^{GS}
\]

- \( \omega \in (0,2) \)

---

# 7. Podmínky konvergence

## ✔ Diagonální dominance
\[
|a_{ii}| > \sum_{j \neq i} |a_{ij}|
\]

## ✔ Symetrická pozitivně definitní matice

---

# 8. Chyby a stabilita

## 🔹 Typy chyb
- zaokrouhlovací
- aproximační

## 🔹 Kondice úlohy
\[
\kappa(A) = ||A|| \cdot ||A^{-1}||
\]

- velká hodnota → nestabilní úloha

---

# 9. Složitost

| Metoda | Složitost |
|--------|----------|
| Gauss | O(n^3) |
| LU | O(n^3) |
| Iterační | O(n^2) / iterace |

---

# 10. Srovnání metod

| Metoda | Výhoda | Nevýhoda |
|--------|--------|---------|
| Gauss | univerzální | pomalý |
| LU | opakované řešení | příprava |
| Jacobi | jednoduchý | pomalý |
| GS | rychlejší | sekvenční |

---

# 11. Co umět na test

- definice \(Ax=b\)
- hodnost, determinant
- Gaussova eliminace (postup!)
- LU rozklad (princip)
- Jacobi vs Gauss-Seidel
- podmínky konvergence
- rozdíl přímé vs iterační metody

---

# 12. Super shrnutí

- řešíme lineární systém
- Gauss = základ
- LU = efektivní
- iterace = velké systémy
- konvergence = klíčová
