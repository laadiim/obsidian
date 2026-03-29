# Vlastní čísla a vlastní vektory – velmi podrobný studijní souhrn

Tento souhrn je zpracován jako detailní studijní materiál k tématu **výpočtu vlastních čísel a vlastních vektorů**. Vychází z přiloženého souboru `vlastni_cisla.pdf` a systematicky shrnuje definice, význam, typy úloh i hlavní numerické metody. Součástí jsou také praktické poznámky, interpretace a srovnání metod.

---

# 1. Základní motivace

S pojmem **vlastní číslo** jsme se setkali už dříve například u iteračních metod pro řešení soustav lineárních algebraických rovnic, kde velikost vlastních čísel iterační matice rozhodovala o konvergenci příslušné metody. Úlohy na vlastní čísla se navíc objevují v mnoha technických a fyzikálních aplikacích. Patří mezi základní témata numerické matematiky.  

---

# 2. Co je úloha na vlastní čísla

Je dána čtvercová matice \(A\) řádu \(n\). Hledáme taková čísla \(\lambda\), pro která má soustava

\[
Av = \lambda v
\]

nenulové řešení \(v \neq 0\).

Tuto rovnici lze přepsat do tvaru

\[
(A-\lambda I)v = 0,
\]

kde:
- \(I\) je jednotková matice,
- \(\lambda\) je hledané vlastní číslo,
- \(v\) je odpovídající vlastní vektor.

Aby homogenní soustava měla **nenulové řešení**, musí být matice \(A-\lambda I\) singulární, tedy musí platit

\[
\det(A-\lambda I)=0.
\]

To vede na tzv. **charakteristickou rovnici**.

---

# 3. Definice

## 3.1 Vlastní čísla

Je dána čtvercová matice \(A\) řádu \(n\). Vlastní čísla \(\lambda_1,\lambda_2,\dots,\lambda_n\) jsou kořeny charakteristické rovnice

\[
p_A(\lambda)=\det(A-\lambda I)=0.
\]

Polynom \(p_A(\lambda)\) se nazývá **charakteristický polynom** matice \(A\).

---

## 3.2 Vlastní vektory

Ke každému vlastnímu číslu \(\lambda_i\) existuje alespoň jedno nenulové řešení soustavy

\[
Av=\lambda_i v.
\]

Každý takový nenulový vektor \(v\) se nazývá **vlastní vektor odpovídající vlastnímu číslu \(\lambda_i\)**.

---

## 3.3 Spektrální matice

Matice

\[
\Lambda = \operatorname{diag}(\lambda_1,\lambda_2,\dots,\lambda_n)
\]

se nazývá **spektrální matice** matice \(A\).

---

# 4. Jak se vlastní čísla hledají

Základní postup je:

1. zapíšeme rovnici
   \[
   (A-\lambda I)v=0,
   \]
2. požadujeme, aby existovalo nenulové řešení,
3. proto musí platit
   \[
   \det(A-\lambda I)=0,
   \]
4. tím získáme charakteristickou rovnici,
5. její kořeny jsou vlastní čísla,
6. pro každé takové \(\lambda\) řešíme homogenní soustavu
   \[
   (A-\lambda I)v=0
   \]
   a dostaneme vlastní vektory.

---

# 5. Ukázkový příklad z definice

Uvažujme matici

\[
A=
\begin{bmatrix}
2 & 0 & 0\\
2 & 2 & 1\\
1 & 1 & 2
\end{bmatrix}.
\]

Hledáme \(\lambda\), pro která má soustava

\[
Av=\lambda v
\]

nenulové řešení. To znamená řešíme

\[
(A-\lambda I)v=
\begin{bmatrix}
2-\lambda & 0 & 0\\
2 & 2-\lambda & 1\\
1 & 1 & 2-\lambda
\end{bmatrix}
\begin{bmatrix}
v_1\\v_2\\v_3
\end{bmatrix}
=
\begin{bmatrix}
0\\0\\0
\end{bmatrix}.
\]

Aby soustava měla nenulové řešení, musí být

\[
\det(A-\lambda I)=0.
\]

V materiálu vychází

\[
-\lambda^3 + 6\lambda^2 - 11\lambda + 6 = 0.
\]

Kořeny jsou:

\[
\lambda_1=3,\quad \lambda_2=2,\quad \lambda_3=1.
\]

To jsou vlastní čísla matice.

Například pro \(\lambda_1=3\) řešíme soustavu

\[
(A-3I)v=0.
\]

V materiálu vychází, že jejím řešením je např. systém vektorů tvaru

\[
[0,r,r]^T,
\]

a jako konkrétní vlastní vektor můžeme zvolit například

\[
v^{(1)}=[0,1,1]^T.
\]

Důležité je, že vlastní vektor není určen jednoznačně. Když je \(v\) vlastní vektor, pak i každý jeho nenulový násobek je vlastním vektorem odpovídajícím témuž vlastnímu číslu.

---

# 6. Důležité poznámky k teorii

## 6.1 Charakteristický polynom je stupně \(n\)

Proto má matice řádu \(n\) právě \(n\) vlastních čísel, počítáme-li je i s násobností.

---

## 6.2 Vlastní čísla horní trojúhelníkové matice

Je-li matice horní trojúhelníková, její vlastní čísla jsou rovna diagonálním prvkům. Důvod je ten, že charakteristický polynom má tvar

\[
p_A(\lambda)=(a_{11}-\lambda)(a_{22}-\lambda)\cdots(a_{nn}-\lambda).
\]

To je velmi důležitá a praktická vlastnost, protože řada numerických metod se snaží převést obecnou matici na trojúhelníkový nebo téměř trojúhelníkový tvar.

---

## 6.3 Násobnost vlastních čísel a počet vlastních vektorů

Materiál ukazuje, že **počet lineárně nezávislých vlastních vektorů může být menší než řád matice**. To je důležitá věc.

Například mohou existovat matice, které mají jedno vlastní číslo několikanásobné, ale ne tolik lineárně nezávislých vlastních vektorů, kolik by odpovídalo jeho algebraické násobnosti.

To znamená:
- vlastní číslo může být násobné,
- ale počet odpovídajících lineárně nezávislých vlastních vektorů může být menší.

---

# 7. Příklad čtyř matic se stejným charakteristickým polynomem

Materiál porovnává čtyři matice:

\[
A=
\begin{bmatrix}
2&0&0\\
0&2&0\\
0&0&2
\end{bmatrix},
\quad
B=
\begin{bmatrix}
2&1&0\\
0&2&0\\
0&0&2
\end{bmatrix},
\quad
C=
\begin{bmatrix}
2&0&0\\
0&2&1\\
0&0&2
\end{bmatrix},
\quad
D=
\begin{bmatrix}
2&1&0\\
0&2&1\\
0&0&2
\end{bmatrix}.
\]

Všechny mají stejný charakteristický polynom

\[
p(\lambda)=(2-\lambda)^3,
\]

tedy všechny mají trojnásobné vlastní číslo

\[
\lambda=2.
\]

Ale vlastní vektory nejsou stejné:

- u matice \(A\) máme tři lineárně nezávislé vlastní vektory,
- u matice \(B\) už méně,
- u matice \(C\) také méně,
- u matice \(D\) pouze jeden lineárně nezávislý vlastní vektor.

### Hlavní závěr
Stejná vlastní čísla ještě neznamenají stejnou strukturu vlastních vektorů. To je zásadní rozdíl mezi algebraickou a geometrickou stránkou spektra matice.

---

# 8. Rozdělení úloh na vlastní čísla

Materiál dělí úlohy na dvě základní skupiny:

## 8.1 Úplný problém vlastních čísel
Úloha najít **všechna vlastní čísla** matice.

To znamená:
- chceme celé spektrum matice,
- často i všechny vlastní vektory.

---

## 8.2 Částečný problém vlastních čísel
Úloha najít pouze **některá vlastní čísla**, obvykle:
- s největší absolutní hodnotou,
- s nejmenší absolutní hodnotou,
- případně dominantní vlastní číslo.

V numerické praxi je často mnohem důležitější právě částečný problém než úplné nalezení celého spektra.

---

# 9. Přístupy k řešení úplného problému vlastních čísel

Materiál uvádí tři hlavní skupiny metod.

## 9.1 Metody založené na charakteristickém polynomu

Základní princip:
- vypočítáme
  \[
  p_A(\lambda)=\det(A-\lambda I),
  \]
- a poté hledáme jeho kořeny.

### Nevýhoda
Pro větší matice je tento postup nevýhodný, protože výpočet determinantu a následné řešení polynomu je numericky i výpočetně obtížné.

Tato metoda je vhodná spíš pro malé matice a teoretické úvahy.

---

## 9.2 Metody využívající podobnosti matic

Tyto metody využívají fakt, že **podobné matice mají stejná vlastní čísla**.

Jestliže existuje regulární matice \(S\), že

\[
B=S^{-1}AS,
\]

pak matice \(A\) a \(B\) mají stejná vlastní čísla.

### Princip
Konstruujeme posloupnost matic navzájem podobných původní matici tak, aby konvergovaly k matici, jejíž vlastní čísla se určují snadno – typicky k horní trojúhelníkové nebo diagonální matici.

---

## 9.3 Smíšené metody

Tyto metody nejprve převedou obecnou matici na třídiagonální tvar a teprve poté efektivně počítají kořeny charakteristického polynomu upravené matice.

V materiálu jsou zmíněny:
- Givensova metoda,
- Householderova metoda,
- Lanczosova metoda.

Tyto metody jsou důležité zejména pro větší úlohy a moderní numerické výpočty.

---

# 10. Metoda LU-rozkladu pro výpočet vlastních čísel
## (LR-transformace, LR-algoritmus)

Tato metoda patří mezi metody založené na podobnosti matic.

---

## 10.1 Základní idea

Rozložíme matici \(A\) na součin

\[
A=LU,
\]

kde:
- \(L\) je dolní trojúhelníková matice,
- \(U\) je horní trojúhelníková matice.

Pak vytvoříme novou matici

\[
B=UL.
\]

Protože platí

\[
U=L^{-1}A,
\]

dostáváme

\[
B=UL=L^{-1}AL.
\]

To znamená, že \(B\) je podobná matici \(A\), a tedy má stejná vlastní čísla.

---

## 10.2 Iterační postup

Sestrojujeme posloupnost matic \(A_k\):

1. \(A_0=A\)
2. provedeme LU rozklad
   \[
   A_k=L_kU_k
   \]
3. sestrojíme novou matici
   \[
   A_{k+1}=U_kL_k
   \]
4. pokud je \(A_{k+1}\) horní trojúhelníková, skončíme,
5. jinak pokračujeme.

Pokud posloupnost konverguje, dostáváme horní trojúhelníkovou matici, na jejíž diagonále jsou vlastní čísla.

---

## 10.3 Proč to funguje

Každá nová matice je podobná předchozí:

\[
A_{k+1}=L_k^{-1}A_kL_k.
\]

Tedy všechny matice \(A_k\) mají stejná vlastní čísla jako původní matice \(A_0\).

Jestliže posloupnost \(A_k\) konverguje k horní trojúhelníkové matici, pak její diagonální prvky jsou vlastní čísla původní matice.

---

## 10.4 Speciální případ – symetrická pozitivně definitní matice

Je-li matice \(A\) symetrická a pozitivně definitní, používá se LU rozklad ve smyslu **Choleského rozkladu**

\[
A=LL^T.
\]

V tom případě lze ukázat, že posloupnost \(A_k\) konverguje k diagonální matici.

To je výrazně lepší situace, protože diagonální matice přímo obsahuje vlastní čísla na diagonále.

---

## 10.5 Nevýhody LR algoritmu

Materiál uvádí několik nevýhod:

- pomalá konvergence,
- velký počet operací pro větší matice,
- nelze snadno realizovat pro obecné matice.

Proto se v praxi často používají spíše metody ortogonálních transformací.

---

## 10.6 Přibližné vlastní vektory

Jestliže pro velké \(k\) je matice \(A_k\) téměř horní trojúhelníková, pak vlastní vektory jsou přibližně sloupce matice

\[
B_k=L_0L_1\cdots L_{k-1}.
\]

To znamená, že algoritmus neposkytuje jen vlastní čísla, ale i aproximace vlastních vektorů.

---

# 11. Metody ortogonálních transformací

Tyto metody jsou numericky důležitější než předchozí, protože jsou stabilnější.

---

## 11.1 Základní princip

Sestrojujeme posloupnost matic

\[
A_{k+1}=Q_k^T A_k Q_k,
\]

kde \(Q_k\) je ortogonální matice.

Ortogonální matice splňuje

\[
Q_kQ_k^T=I,
\quad \text{tedy} \quad Q_k^{-1}=Q_k^T.
\]

Tím pádem je \(A_{k+1}\) podobná matici \(A_k\), a tedy všechny matice v posloupnosti mají stejná vlastní čísla.

---

## 11.2 Výhoda ortogonálních transformací

Hlavní výhodou je **numerická stabilita**.

To je velmi důležitý důvod, proč mají QR a příbuzné algoritmy v numerické matematice tak zásadní postavení.

---

## 11.3 QR-transformace

U obecné matice používáme rozklad

\[
A=QU,
\]

kde:
- \(Q\) je ortogonální matice,
- \(U\) je horní trojúhelníková matice.

Novou matici definujeme

\[
B=UQ.
\]

Protože

\[
U=Q^{-1}A=Q^TA,
\]

máme

\[
B=UQ=Q^{-1}AQ=Q^TAQ.
\]

Tedy \(B\) je podobná matici \(A\).

Opakováním tohoto kroku dostáváme posloupnost matic, která za vhodných podmínek konverguje k horní trojúhelníkové matici. Na její diagonále jsou pak vlastní čísla.

---

# 12. Motivační příklad ortogonální transformace

Materiál ukazuje jednoduchý případ pro matici

\[
A=
\begin{bmatrix}
2 & 1\\
1 & 3
\end{bmatrix}
\]

a rotační matici

\[
Q(\alpha)=
\begin{bmatrix}
\cos\alpha & -\sin\alpha\\
\sin\alpha & \cos\alpha
\end{bmatrix}.
\]

Hledáme takové \(\alpha\), aby v matici

\[
B=Q^T(\alpha)AQ(\alpha)
\]

byl prvek \(b_{12}=0\).

Po dosazení a úpravě v materiálu vychází podmínka

\[
\tan(2\alpha)=-2,
\]

odkud dostaneme přibližně

\[
\alpha \approx -0{,}5535.
\]

Po dosazení vznikne diagonální matice

\[
B=
\begin{bmatrix}
3{,}6180 & 0\\
0 & 1{,}3819
\end{bmatrix}.
\]

Protože \(B\) je podobná matici \(A\), má stejná vlastní čísla. Takže vlastní čísla původní matice jsou přibližně

\[
\lambda_1 \approx 3{,}6180,
\quad
\lambda_2 \approx 1{,}3819.
\]

### Hlavní význam příkladu
Jedním vhodně zvoleným ortogonálním přechodem lze vynulovat mimodiagonální prvek a přiblížit se diagonálnímu tvaru.

---

# 13. Jacobiova diagonalizace

Jde o speciální případ QR-transformace pro **reálné symetrické matice**.

---

## 13.1 Základní věta

Je-li \(A\) reálná symetrická matice, potom existuje ortogonální matice \(Q\), že

\[
Q^TAQ=\Lambda,
\]

kde \(\Lambda\) je diagonální matice s vlastními čísly na diagonále.

To je velmi důležitý výsledek. Znamená, že každou reálnou symetrickou matici lze ortogonálně diagonalizovat.

---

## 13.2 Princip metody

Matici \(Q\) získáme jako součin jednoduchých rotačních matic \(Q_{p,q}(\alpha)\), které působí jen ve dvou vybraných souřadnicích \(p,q\).

Úhel \(\alpha\) volíme tak, aby se vynuloval prvek v pozici \((p,q)\), a tím i symetrický prvek \((q,p)\).

Tento postup opakujeme tak dlouho, až jsou všechny mimodiagonální prvky dostatečně malé.

---

## 13.3 Jak vypadá matice \(Q_{p,q}(\alpha)\)

Je to v podstatě jednotková matice, ve které je v řádcích a sloupcích \(p\) a \(q\) vložen rotační blok

\[
\begin{bmatrix}
\cos\alpha & -\sin\alpha\\
\sin\alpha & \cos\alpha
\end{bmatrix}.
\]

Taková transformace mění jen dvě souřadnice a ostatní nechává beze změny.

---

## 13.4 Strategie volby prvků \(p,q\)

Materiál zmiňuje dvě základní možnosti:

### a) Postupné nulování všech mimodiagonálních prvků
Podobně jako v Gaussově eliminaci systematicky procházíme matici.

Nevýhoda:
- nulové prvky vytvořené v předchozích krocích se obecně nemusí zachovat.

### b) Volíme vždy mimodiagonální prvek s největší absolutní hodnotou
To většinou vede k rychlejší konvergenci.

Nevýhoda:
- v každém kroku musíme vyhledávat největší mimodiagonální prvek, což zpomaluje výpočet.

---

## 13.5 Zastavovací podmínka

Iterační proces ukončíme, když norma trojúhelníkové části pod diagonálou je menší než zadaná tolerance.

To prakticky znamená, že mimodiagonální prvky už jsou dostatečně malé a matice je téměř diagonální.

---

## 13.6 Výsledek Jacobiovy diagonalizace

- na diagonále dostaneme aproximace vlastních čísel,
- ve sloupcích výsledné ortogonální matice dostaneme vlastní vektory.

To je obrovská výhoda této metody pro symetrické matice.

---

# 14. Částečný problém vlastních čísel

Často nepotřebujeme znát všechna vlastní čísla, ale jen jedno nebo několik nejdůležitějších.

Materiál uvádí dvě metody:
1. **mocninnou metodu**,
2. **metodu Rayleighova podílu**.

Tyto metody hledají dominantní vlastní číslo, tedy vlastní číslo s největší absolutní hodnotou.

---

# 15. Mocninná metoda

## 15.1 Cíl metody

Chceme určit vlastní číslo matice \(A\) s největší absolutní hodnotou, tzv. **dominantní vlastní číslo**.

---

## 15.2 Předpoklady

Materiál uvádí tyto předpoklady:

1. matice \(A\) má \(n\) lineárně nezávislých vlastních vektorů,
2. existuje jediné dominantní vlastní číslo,
3. vlastní čísla lze uspořádat tak, že
   \[
   |\lambda_1| > |\lambda_2| \ge |\lambda_3| \ge \dots \ge |\lambda_n|.
   \]

---

## 15.3 Myšlenka metody

Zvolíme počáteční vektor \(y^{(0)}\) jako lineární kombinaci vlastních vektorů:

\[
y^{(0)}=\alpha_1 v_1 + \alpha_2 v_2 + \dots + \alpha_n v_n.
\]

Potom opakovaně počítáme

\[
y^{(k)}=Ay^{(k-1)},
\quad \text{tedy} \quad
y^{(k)}=A^k y^{(0)}.
\]

Protože pro vlastní vektory platí

\[
Av_i=\lambda_i v_i,
\]

dostáváme

\[
y^{(k)}=
\alpha_1 \lambda_1^k v_1 +
\alpha_2 \lambda_2^k v_2 + \dots +
\alpha_n \lambda_n^k v_n.
\]

Pokud je \(|\lambda_1|\) největší, začne dominovat člen s \(\lambda_1^k\).

To znamená, že pro velká \(k\) je vektor \(y^{(k)}\) přibližně rovnoběžný s vlastním vektorem \(v_1\) a zároveň z poměru složek lze odhadnout dominantní vlastní číslo.

---

## 15.4 Odhad dominantního vlastního čísla

Vybereme vhodnou složku \(j\) a použijeme aproximaci

\[
\lambda_1 \approx \frac{y^{(k+1)}_j}{y^{(k)}_j}.
\]

Pro \(k \to \infty\) tento poměr konverguje k dominantnímu vlastnímu číslu.

---

## 15.5 Praktický algoritmus mocninné metody

1. zvolíme počáteční vektor \(y^{(0)}\),
2. počítáme
   \[
   y^{(k+1)} = A y^{(k)},
   \]
3. v každém kroku odhadneme
   \[
   \lambda^{(k)} \approx \frac{y^{(k+1)}_j}{y^{(k)}_j},
   \]
4. pokračujeme, dokud rozdíl dvou po sobě jdoucích aproximací není dost malý.

---

## 15.6 Příklad mocninné metody

Máme matici

\[
A=
\begin{bmatrix}
1&1&0\\
1&1&1\\
0&1&1
\end{bmatrix},
\qquad
y^{(0)}=[1,1,1]^T.
\]

V materiálu vycházejí iterace:

\[
y^{(1)}=[2,3,2]^T,\qquad \lambda_1^{(1)}=3,
\]

\[
y^{(2)}=[5,7,5]^T,\qquad \lambda_1^{(2)}=\frac{7}{3}\approx 2{,}3333,
\]

\[
y^{(3)}=[12,17,12]^T,\qquad \lambda_1^{(3)}=\frac{17}{7}\approx 2{,}4285,
\]

\[
y^{(4)}=[29,41,29]^T,\qquad \lambda_1^{(4)}=\frac{41}{17}\approx 2{,}4117,
\]

\[
y^{(5)}=[70,99,70]^T,\qquad \lambda_1^{(5)}=\frac{99}{41}\approx 2{,}4146.
\]

Je vidět, že aproximace konvergují k dominantnímu vlastnímu číslu.

---

## 15.7 Zastavovací podmínka

Materiál doporučuje zastavení ve tvaru

\[
|\lambda_1^{(k+1)}-\lambda_1^{(k)}|<\delta.
\]

---

## 15.8 Praktické poznámky

### Kterou složku dělit?
Nejlepší aproximaci dostaneme, když používáme složky s největší absolutní hodnotou.

### Proč normovat vektory?
Abychom zabránili přetečení nebo podtečení v počítači, je vhodné v každém kroku vektor normovat. Jeho norma totiž může velmi rychle růst nebo klesat podle velikosti dominantního vlastního čísla.

---

## 15.9 Nevýhody mocninné metody

Materiál uvádí tyto problémy:

- obtížný odhad chyby,
- v praxi často nevíme, zda jsou splněny předpoklady metody,
- velký vliv volby počátečního vektoru \(y^{(0)}\).

### Důležitá poznámka
Pokud počáteční vektor nemá složku ve směru dominantního vlastního vektoru, tedy pokud koeficient \(\alpha_1=0\), metoda dominantní vlastní číslo nenajde.

---

# 16. Metoda Rayleighova podílu

Tato metoda je zlepšením mocninné metody.

---

## 16.1 Předpoklad

Navíc předpokládáme, že matice \(A\) je **reálná symetrická**.

Pak jsou vlastní vektory ortonormální:

\[
v_i^T v_j = 0 \quad \text{pro } i\neq j,
\qquad
v_i^T v_i=1.
\]

---

## 16.2 Rayleighův podíl

Dominantní vlastní číslo aproximujeme výrazem

\[
\lambda_1 \approx \frac{y^{(k)T}Ay^{(k)}}{y^{(k)T}y^{(k)}}.
\]

Protože při iteračním výpočtu platí \(y^{(k+1)}=Ay^{(k)}\), lze také psát

\[
\lambda_1 \approx \frac{y^{(k)T}y^{(k+1)}}{y^{(k)T}y^{(k)}}.
\]

---

## 16.3 Proč je metoda rychlejší

Materiál ukazuje, že chyba v Rayleighově podílu klesá zhruba dvakrát rychleji než u obyčejné mocninné metody.

To znamená, že Rayleighův podíl poskytuje lepší aproximaci dominantního vlastního čísla ze stejného vektoru \(y^{(k)}\).

---

## 16.4 Příklad Rayleighovy metody

Pro stejnou matici

\[
A=
\begin{bmatrix}
1&1&0\\
1&1&1\\
0&1&1
\end{bmatrix},
\qquad
y^{(0)}=[1,1,1]^T
\]

vychází:

\[
y^{(1)}=[2,3,2]^T,
\qquad
\lambda_1^{(1)}=\frac{y^{(0)T}y^{(1)}}{y^{(0)T}y^{(0)}}=\frac73 \approx 2{,}3333,
\]

\[
y^{(2)}=[5,7,5]^T,
\qquad
\lambda_1^{(2)}=\frac{41}{17}\approx 2{,}4117,
\]

\[
y^{(3)}=[12,17,12]^T,
\qquad
\lambda_1^{(3)}=\frac{239}{99}\approx 2{,}41417.
\]

Je vidět, že metoda konverguje rychleji než prostý poměr složek v mocninné metodě.

---

# 17. Porovnání hlavních metod z materiálu

## 17.1 Přehled

| Metoda | Typ úlohy | Hlavní idea | Výhoda | Nevýhoda |
|---|---|---|---|---|
| Charakteristický polynom | úplný problém | řešení \(\det(A-\lambda I)=0\) | jednoduchá teorie | nevhodné pro velké matice |
| LR algoritmus | úplný problém | podobné matice přes LU rozklad | teoreticky přehledný | pomalý, ne vždy realizovatelný |
| QR / ortogonální transformace | úplný problém | podobné matice přes ortogonální transformace | numerická stabilita | složitější konstrukce |
| Jacobiova diagonalizace | úplný problém pro symetrické matice | postupné nulování mimodiagonálních prvků | dává i vlastní vektory | výpočetně náročnější |
| Mocninná metoda | částečný problém | opakované násobení maticí | jednoduchá | dává jen dominantní vl. číslo, citlivá na \(y^{(0)}\) |
| Rayleighův podíl | částečný problém | vylepšení mocninné metody | rychlejší konvergence | vyžaduje symetrii |

---

# 18. Co je důležité si zapamatovat

## 18.1 Úplné minimum z teorie
- vlastní čísla jsou kořeny rovnice
  \[
  \det(A-\lambda I)=0,
  \]
- vlastní vektor je nenulové řešení rovnice
  \[
  (A-\lambda I)v=0,
  \]
- podobné matice mají stejná vlastní čísla,
- u horní trojúhelníkové matice jsou vlastní čísla diagonální prvky,
- u reálné symetrické matice existuje ortogonální diagonalizace.

---

## 18.2 K metodám
- LR algoritmus používá podobnost \(A_{k+1}=L_k^{-1}A_kL_k\),
- QR algoritmus používá podobnost \(A_{k+1}=Q_k^TA_kQ_k\),
- Jacobiova diagonalizace je speciální metoda pro symetrické matice,
- mocninná metoda hledá dominantní vlastní číslo,
- Rayleighův podíl je rychlejší odhad dominantního vlastního čísla pro symetrické matice.

---

# 19. Praktická interpretace obrázků a diagramů v materiálu

V souboru jsou kromě textu hlavně algebraické postupy, ale klíčovou roli hrají také konstrukce ortogonálních transformací. Zejména stránky 5–7 ukazují princip rotací, který je základem Jacobiovy diagonalizace: pomocí rovinné rotace vynulujeme vybraný mimodiagonální prvek a matici postupně přibližujeme k diagonálnímu tvaru. Na stranách 8–11 pak příklady mocninné metody a Rayleighova podílu ilustrují, jak se z iterací vektorů získávají stále přesnější aproximace dominantního vlastního čísla. fileciteturn2file0

---

# 20. Superstručné závěrečné shrnutí

- Úloha na vlastní čísla má tvar
  \[
  Av=\lambda v.
  \]
- Vlastní čísla dostaneme z rovnice
  \[
  \det(A-\lambda I)=0.
  \]
- Vlastní vektory získáme jako nenulová řešení soustavy
  \[
  (A-\lambda I)v=0.
  \]
- Úplný problém = najít všechna vlastní čísla.
- Částečný problém = najít jen některá, typicky dominantní.
- Pro úplný problém se používají podobnostní transformace.
- Pro částečný problém jsou základní metody:
  - mocninná metoda,
  - Rayleighův podíl.
- Pro reálné symetrické matice je velmi důležitá ortogonální diagonalizace a Jacobiova diagonalizace.

