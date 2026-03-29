
# Nelineární rovnice a soustavy nelineárních rovnic – podrobný studijní souhrn

Tento souhrn je zpracovaný jako podrobný materiál k učení na test. Shrnuje základní pojmy, principy metod, podmínky konvergence, rychlost konvergence, typické výhody a nevýhody i hlavní vzorce.

Zdrojové materiály:
- `nelinearni_rovnice.pdf`
- `soustavy_nelinearnich_rovnic.pdf`

---

# 1. Nelineární rovnice

## 1.1 Formulace úlohy

Je dána funkce

\[
f : \mathbb{R} \to \mathbb{R}
\]

definovaná na intervalu \(\langle a,b\rangle\). Hledáme číslo \(x \in \langle a,b\rangle\), pro které platí

\[
f(x)=0.
\]

Takové číslo nazýváme:
- **řešení rovnice**
- **kořen rovnice**

V praxi většinou nelze kořen určit přesně analyticky, a proto používáme **numerické metody**, zejména **iterační metody**.

---

## 1.2 Proč používáme numerické metody

Přesné analytické řešení je možné jen u jednoduchých rovnic. U složitějších rovnic je potřeba počítat přibližné řešení.

U iteračních metod nás zajímají hlavně dvě otázky:

1. **Konverguje posloupnost iterací ke hledanému řešení?**
2. **Jak rychle konverguje?**

To je důležité, protože některé metody:
- konvergují **vždy**, ale pomalu,
- jiné konvergují **rychle**, ale jen při dobré počáteční aproximaci.

---

## 1.3 Rozdělení metod

Metody řešení nelineárních rovnic se v materiálu dělí na:

### a) Startovací metody
- jsou zpravidla **vždy konvergentní**
- bývají **pomalejší**
- používají se pro nalezení první rozumné aproximace kořene

Příklad:
- **bisekce**
- **regula falsi**

### b) Zpřesňující metody
- bývají **rychlejší**
- konvergence může silně záviset na:
  - počáteční aproximaci,
  - vlastnostech funkce v okolí kořene

Příklad:
- **Newtonova metoda**
- **metoda sečen**

### c) Speciální metody
- určené pro určité typy problémů, například polynomy

---

## 1.4 Základní věta o existenci řešení

Předpokládejme, že:
1. funkce \(f\) je spojitá na intervalu \(\langle a,b\rangle\),
2. platí
   \[
   f(a)\cdot f(b) < 0.
   \]

Pak v intervalu \(\langle a,b\rangle\) existuje **alespoň jedno řešení** rovnice

\[
f(x)=0.
\]

### Význam věty
Pokud má funkce na krajích intervalu opačné znaménko, musí graf alespoň jednou protínat osu \(x\).

Tato věta je základem například pro **metodu bisekce**.

---

# 2. Metoda bisekce

## 2.1 Princip

Metoda bisekce (metoda půlení intervalu) vychází z předchozí věty. Máme interval \(\langle a,b\rangle\), na jehož krajích má funkce opačné znaménko.

V každém kroku:
1. spočteme střed intervalu
   \[
   s = \frac{a+b}{2},
   \]
2. zjistíme znaménko \(f(s)\),
3. vybereme polovinu intervalu, ve které stále dochází ke změně znaménka.

Takto interval stále zmenšujeme, až je dostatečně krátký.

---

## 2.2 Algoritmus bisekce

1. Zvolíme \(\varepsilon > 0\), počáteční body \(a,b\)
2. Spočteme
   \[
   s=\frac{a+b}{2}
   \]
3. Je-li \(f(s)=0\), pak je řešení \(x=s\)
4. Jinak:
   - pokud \(f(a)\cdot f(s)<0\), položíme \(b=s\)
   - jinak položíme \(a=s\)
5. Pokud
   \[
   b-a \ge \varepsilon,
   \]
   pokračujeme dalším krokem
6. Jinak ukončíme výpočet a za řešení bereme střed posledního intervalu

---

## 2.3 Vlastnosti metody bisekce

### Výhody
- **vždy konverguje**, pokud jsou splněny podmínky
- je velmi jednoduchá
- lze předem odhadnout potřebný počet iterací

### Nevýhody
- konverguje **pomalu**
- nehodí se pro komplexní kořeny
- potřebuje interval, kde je změna znaménka

---

## 2.4 Rychlost bisekce

Bisekce patří mezi pomalé startovací metody.

Z materiálu plyne, že pro zpřesnění o jedno desetinné místo je třeba přibližně **3,3 iterace**.

To znamená:
- metoda je spolehlivá,
- ale na vysokou přesnost potřebuje hodně kroků.

---

# 3. Metoda prosté iterace

## 3.1 Základní myšlenka

Rovnici

\[
f(x)=0
\]

převedeme na ekvivalentní tvar

\[
x=\varphi(x).
\]

Pak sestrojíme iterační proces:

\[
x_{k+1}=\varphi(x_k).
\]

Cílem je, aby posloupnost \((x_k)\) konvergovala ke kořeni.

---

## 3.2 Geometrický význam

Řešení rovnice \(x=\varphi(x)\) odpovídá průsečíku grafů:
- \(y=x\)
- \(y=\varphi(x)\)

Každá iterace se tedy dá geometricky chápat jako přechod mezi těmito dvěma grafy.

---

## 3.3 Algoritmus

1. Zvolíme počáteční aproximaci \(x_0 \in \langle a,b\rangle\) a \(\varepsilon>0\)
2. Počítáme:
   \[
   x_{k+1}=\varphi(x_k)
   \]
3. Pokud
   \[
   |x_{k+1}-x_k|<\varepsilon,
   \]
   skončíme a za výsledek bereme \(x_{k+1}\)
4. Jinak pokračujeme

---

## 3.4 Hlavní problém metody

Největší problém není samotný výpočet, ale **nalezení vhodné funkce \(\varphi\)**.

Stejnou rovnici lze totiž přepsat na tvar \(x=\varphi(x)\) mnoha různými způsoby:
- některé povedou ke konvergenci,
- jiné povedou k divergenci,
- některé konvergují pomalu,
- jiné velmi rychle.

Takže úspěch metody závisí hlavně na správném výběru \(\varphi\).

---

## 3.5 Postačující podmínky konvergence

Nechť \(\varphi\) je spojitá na intervalu \(I=\langle a,b\rangle\) a platí:

### (a) Zobrazení intervalu do sebe
\[
\forall x \in I:\ \varphi(x)\in I
\]

To znamená, že iterace „neutíkají“ mimo interval.

### (b) Kontrakce
Existuje \(q \in (0,1)\) tak, že

\[
|\varphi(x)-\varphi(y)| \le q|x-y|
\quad \forall x,y\in I.
\]

Pak platí:
1. v intervalu \(I\) existuje právě jedno řešení rovnice \(x=\varphi(x)\),
2. pro libovolné \(x_0\in I\) posloupnost iterací konverguje k tomuto řešení.

---

## 3.6 Podmínka pomocí derivace

Je-li \(\varphi\) diferencovatelná, lze kontrakční podmínku nahradit jednodušší podmínkou:

\[
\exists q\in(0,1):\ |\varphi'(x)|\le q \quad \forall x\in I.
\]

To je v praxi často nejpoužívanější test konvergence.

### Interpretace
- když je graf \(y=\varphi(x)\) v okolí řešení dost „plochý“, metoda konverguje,
- když je příliš strmý, metoda může divergovat.

---

## 3.7 Rychlost konvergence a vliv derivace

V materiálu je zdůrazněno, že metoda konverguje rychleji tehdy, když je graf \(\varphi\) v okolí řešení co nejvíce vodorovný.

Rozhodující roli hraje hodnota:
\[
|\varphi'(x)|.
\]

Čím menší je \(|\varphi'|\), tím rychlejší bývá konvergence.

---

## 3.8 Odhad chyby u prosté iterace

Mějme konvergentní iterační proces
\[
x_k=\varphi(x_{k-1})
\]
a nechť \(\alpha\) je přesné řešení.

Pokud je splněna kontrakční podmínka s konstantou \(q\), pak lze odvodit odhad:

\[
|x_k-\alpha| \le \frac{q}{1-q}|x_{k-1}-x_k|.
\]

Použijeme-li zastavovací podmínku
\[
|x_k-x_{k-1}|<\varepsilon,
\]
potom:

\[
|x_k-\alpha|\le \frac{q}{1-q}\varepsilon.
\]

### Důležitá poznámka
Rozdíl dvou po sobě jdoucích iterací **obecně není přímo chyba řešení**. Je pouze vodítkem a za určitých podmínek umožňuje chybu odhadnout.

---

## 3.9 Rychlost konvergence – definice

Říkáme, že posloupnost \(x_k\) konverguje k \(\alpha\) rychlostí řádu \(r\), jestliže platí

\[
|x_{k+1}-\alpha|
=
c|x_k-\alpha|^r + O(|x_k-\alpha|^{r+1}).
\]

V materiálu se rozlišuje hlavně:

- **řád 1** – lineární konvergence
- **řád 2** – kvadratická konvergence

---

## 3.10 Rychlost prosté iterace

Z Taylorova rozvoje plyne:

### Pokud \(\varphi'(\alpha)\neq 0\)
pak má metoda **konvergenci řádu 1**, tedy lineární.

### Pokud \(\varphi'(\alpha)=0\) a \(\varphi''(\alpha)\neq 0\)
pak má metoda **konvergenci řádu 2**, tedy kvadratickou.

To je velmi důležité:
- běžná prostá iterace je obvykle lineární,
- ve speciálních případech může být i kvadratická.

---

## 3.11 Praktická poznámka pro algebraické rovnice

Je-li řešena algebraická rovnice
\[
a_nx^n+a_{n-1}x^{n-1}+\dots+a_1x+a_0=0
\]
a hledané řešení má absolutní hodnotu větší než 1, bývá vhodné vyjádřit \(x\) z nejvyšší mocniny.

To je praktické doporučení pro volbu vhodné funkce \(\varphi\).

---

# 4. Regula falsi

## 4.1 Princip

Metoda regula falsi je další startovací metoda.

Geometrický význam:
- místo skutečné křivky \(y=f(x)\) použijeme **sečnu** vedenou body
  \[
  [a,f(a)],\quad [b,f(b)].
  \]
- průsečík této sečny s osou \(x\) označíme \(s\),
- podle znaménka \(f(s)\) nahradíme buď \(a\), nebo \(b\).

---

## 4.2 Vzorec

Průsečík sečny s osou \(x\) je:

\[
s = a - \frac{f(a)}{f(b)-f(a)}(b-a).
\]

---

## 4.3 Algoritmus

1. Zvolíme \(\delta>0\), \(a\), \(b\)
2. Spočteme
   \[
   s = a - \frac{f(a)}{f(b)-f(a)}(b-a)
   \]
3. Pokud
   \[
   |f(s)|<\delta,
   \]
   ukončíme výpočet
4. Jinak:
   - pokud \(f(a)\cdot f(s)<0\), položíme \(b=s\)
   - jinak položíme \(a=s\)
5. Opakujeme

---

## 4.4 Důležitá poznámka

Číslo \(\delta\) **nepředstavuje přesnost řešení**. Slouží pouze jako podmínka pro zastavení výpočtu.

---

## 4.5 Výhody a nevýhody

### Výhody
- využívá více informací než bisekce
- bývá rychlejší než bisekce

### Nevýhody
- stále jde o startovací metodu
- nemusí být tak rychlá jako Newtonova metoda

---

# 5. Newtonova metoda

## 5.1 Myšlenka metody

Newtonova metoda je typická **zpřesňující metoda**.

Předpokládáme:
- že hledaný kořen je v intervalu jediný,
- že je to **jednoduchý kořen**,
- že máme počáteční aproximaci \(x_0\), která je dost blízko řešení.

Funkci \(f\) v okolí \(x_k\) nahradíme její lineární aproximací – tečnou.

---

## 5.2 Odvození

Taylorův rozvoj funkce v bodě \(x_k\):

\[
f(x)=f(x_k)+f'(x_k)(x-x_k)+\frac12 f''(\xi)(x-x_k)^2.
\]

Rovnici \(f(x)=0\) aproximujeme lineární rovnicí:

\[
f(x_k)+f'(x_k)(x-x_k)=0.
\]

Její řešení je

\[
x_{k+1}=x_k-\frac{f(x_k)}{f'(x_k)}.
\]

To je iterační vzorec Newtonovy metody.

---

## 5.3 Iterační vzorec

\[
x_{k+1}=x_k-\frac{f(x_k)}{f'(x_k)}.
\]

---

## 5.4 Geometrický význam

V bodě \((x_k,f(x_k))\) sestrojíme tečnu ke grafu funkce \(y=f(x)\).

Další iterace \(x_{k+1}\) je průsečík této tečny s osou \(x\).

Proto se Newtonově metodě někdy říká:
- metoda tečen,
- metoda linearizace.

---

## 5.5 Zastavovací podmínky

V materiálu jsou uvedeny dvě možné podmínky:

1. podle změny iterací
   \[
   |x_{k+1}-x_k|<\varepsilon
   \]

2. podle velikosti funkční hodnoty
   \[
   |f(x_k)|<\delta
   \]

---

## 5.6 Vztah k prosté iteraci

Newtonovu metodu lze chápat jako speciální případ prosté iterace, kde

\[
\varphi(x)=x-\frac{f(x)}{f'(x)}.
\]

---

## 5.7 Rychlost konvergence Newtonovy metody

Z odvození v materiálu plyne:

- \(\varphi'(\alpha)=0\),
- obecně \(\varphi''(\alpha)\neq 0\),

a proto má Newtonova metoda **konvergenci řádu 2**, tedy **kvadratickou konvergenci**.

### Praktický význam
Je-li počáteční aproximace dost dobrá a kořen je jednoduchý, metoda bývá velmi rychlá.

---

## 5.8 Výhody Newtonovy metody

- velmi rychlá konvergence
- v praxi často stačí málo iterací
- vhodná pro zpřesnění již nalezeného přibližného řešení

---

## 5.9 Nevýhody Newtonovy metody

- funkce musí být diferencovatelná
- derivace se objevuje přímo ve vzorci
- v každém kroku musíme počítat nejen \(f(x_k)\), ale i \(f'(x_k)\)
- metoda může selhat při nevhodné počáteční aproximaci

---

## 5.10 Problém vícenásobných kořenů

Newtonova metoda je rychlá hlavně pro **jednoduché kořeny**.

Když má kořen vyšší násobnost:
- v okolí kořene bývá \(f'(x)\) malé nebo nulové,
- ve vzorci se dělí malým číslem,
- metoda se zpomaluje.

Typický geometrický obraz:
- graf funkce se osy \(x\) jen dotýká,
- místo ostrého průchodu přes osu je v kořeni „zploštělý“.

---

## 5.11 Jak řešit vícenásobný kořen

Je-li \(\hat{x}\) \(n\)-násobným kořenem rovnice \(f(x)=0\), pak je \(\hat{x}\) také \((n-1)\)-násobným kořenem rovnice \(f'(x)=0\), a tedy jednoduchým kořenem rovnice

\[
\frac{f(x)}{f'(x)}=0.
\]

To je uvedeno jako elegantní cesta, jak problém s násobným kořenem obejít.

---

## 5.12 Newtonova metoda v komplexním oboru

V materiálu je poznámka, že Newtonovu metodu lze použít i v oboru komplexních čísel.

Například pro rovnici
\[
z^3-1=0
\]
vzniká v závislosti na počáteční aproximaci fraktálová struktura.

To ukazuje, že Newtonova metoda má širší použití než jen v \(\mathbb{R}\).

---

# 6. Modifikovaná Newtonova metoda

## 6.1 Motivace

Nevýhodou Newtonovy metody je nutnost počítat derivaci v každém kroku.

Pokud se derivace \(f'(x)\) v okolí kořene příliš nemění, lze ji aproximovat konstantou:
\[
f'(x_k)\approx f'(x_0).
\]

Pak dostaneme modifikovanou Newtonovu metodu:

\[
x_{k+1}=x_k-\frac{f(x_k)}{f'(x_0)}.
\]

---

## 6.2 Geometrický význam

Místo tečen v jednotlivých bodech používáme přímky rovnoběžné s tečnou sestrojenou v počátečním bodě \((x_0,f(x_0))\).

---

## 6.3 Výhody
- derivaci počítáme jen jednou
- vhodné, když je derivace složitá

## 6.4 Nevýhody
- zpravidla pomalejší než klasická Newtonova metoda
- potřebujeme, aby se derivace v okolí kořene příliš neměnila

---

# 7. Metoda sečen

## 7.1 Motivace

Chceme-li upravit Newtonovu metodu pro situace, kdy funkce není diferencovatelná nebo nechceme derivaci počítat, nahradíme derivaci diferenčním podílem:

\[
f'(x_k)\approx \frac{f(x_k)-f(x_{k-1})}{x_k-x_{k-1}}.
\]

Tím získáme **metodu sečen**.

---

## 7.2 Iterační vzorec

Po dosazení do Newtonova vzorce dostaneme:

\[
x_{k+1}
=
x_k
-
f(x_k)\frac{x_k-x_{k-1}}{f(x_k)-f(x_{k-1})}.
\]

---

## 7.3 Geometrický význam

Mějme dvě aproximace \(x_{k-1}\) a \(x_k\).

Místo tečny použijeme **sečnu** vedenou body:
\[
[x_{k-1},f(x_{k-1})],\quad [x_k,f(x_k)].
\]

Další iterace \(x_{k+1}\) je průsečík této sečny s osou \(x\).

---

## 7.4 Vlastnosti

### Výhody
- nepotřebujeme derivaci
- v každém kroku počítáme jen jednu novou funkční hodnotu
- může být časově výhodná

### Nevýhody
- potřebujeme dvě počáteční aproximace
- obecně bývá méně stabilní než Newtonova metoda

---

## 7.5 Vztah k regula falsi

Metoda sečen má podobný algoritmus jako regula falsi, ale:
- u regula falsi se udržuje interval se změnou znaménka,
- u metody sečen podmínku
  \[
  f(x_{k-1})f(x_k)<0
  \]
  nepožadujeme.

---

# 8. Mullerova metoda

## 8.1 Princip

Mějme tři aproximace:
\[
x_{k-2},\ x_{k-1},\ x_k.
\]

Křivku \(y=f(x)\) nahradíme **parabolou**, která prochází body:
\[
[x_{k-2},f(x_{k-2})],\quad [x_{k-1},f(x_{k-1})],\quad [x_k,f(x_k)].
\]

Další iteraci \(x_{k+1}\) získáme jako průsečík paraboly s osou \(x\), a to ten, který je blíže k \(x_k\).

---

## 8.2 Význam
- jde o tříkrokovou interpolační metodu
- může pracovat i s komplexními kořeny

---

## 8.3 Praktická poznámka
V materiálu je Mullerova metoda zmíněna hlavně orientačně jako další možnost vedle metody sečen.

---

# 9. Praktické prostředky v MATLABu

Na konci materiálu jsou uvedeny prostředky MATLABu:

- `fzero` – pro obecnou nelineární rovnici
- `roots` – pro kořeny polynomu

---

# 10. Soustavy nelineárních rovnic

---

## 10.1 Formulace úlohy

Máme funkce

\[
F_i:\mathbb{R}^n\to\mathbb{R},\quad i=1,\dots,n
\]

a hledáme vektor

\[
x=(x_1,x_2,\dots,x_n)^T
\]

tak, aby platilo

\[
F_1(x_1,\dots,x_n)=0
\]
\[
F_2(x_1,\dots,x_n)=0
\]
\[
\vdots
\]
\[
F_n(x_1,\dots,x_n)=0.
\]

Vektorově zapisujeme:

\[
F(x)=0,
\quad
F=(F_1,F_2,\dots,F_n)^T.
\]

---

## 10.2 Geometrická interpretace

U dvou rovnic o dvou neznámých hledáme průsečíky dvou křivek.

Počet řešení se může měnit podle parametrů:
- žádné řešení,
- jedno řešení,
- více řešení.

Proto je u soustav důležité i kvalitativně chápat tvar jednotlivých rovnic.

---

# 11. Prostá iterace pro soustavy

## 11.1 Přepis soustavy

Soustavu

\[
F(x)=0
\]

nahradíme soustavou

\[
x=\Phi(x).
\]

Stejně jako v jednorozměrném případě existuje více možností, jak tuto úpravu provést.

---

## 11.2 Iterační vztah

\[
x_{k+1}=\Phi(x_k).
\]

---

## 11.3 Algoritmus

1. Zvolíme počáteční aproximaci \(x_0\in I\) a \(\varepsilon>0\)
2. Počítáme
   \[
   x_{k+1}=\Phi(x_k)
   \]
3. Pokud
   \[
   \|x_{k+1}-x_k\|<\varepsilon,
   \]
   skončíme
4. Jinak pokračujeme

---

## 11.4 Postačující podmínky konvergence

Nechť \(\Phi\) je spojitá na oblasti \(I\) a platí:

### (a) Zobrazení oblasti do sebe
\[
\forall x\in I:\ \Phi(x)\in I
\]

### (b) Kontrakce
Existuje \(q\in(0,1)\) tak, že
\[
\|\Phi(x)-\Phi(y)\|\le q\|x-y\|
\quad \forall x,y\in I.
\]

Pak:
1. v oblasti \(I\) existuje právě jedno řešení soustavy \(x=\Phi(x)\),
2. pro libovolné \(x_0\in I\) iterační posloupnost konverguje k tomuto řešení.

---

## 11.5 Podmínka pomocí Jacobiho matice

Je-li \(\Phi\) diferencovatelná, lze kontrakční podmínku nahradit:

\[
\exists q\in(0,1):\ \|\Phi'(x)\|\le q
\quad \forall x\in I,
\]

kde \(\Phi'(x)\) je **Jacobiho matice**

\[
\Phi'(x)=
\left[
\frac{\partial \Phi_i(x_1,\dots,x_n)}{\partial x_j}
\right].
\]

---

## 11.6 Výhody a nevýhody prosté iterace pro soustavy

### Výhoda
- samotný výpočet podle rekurentní formule je jednoduchý

### Nevýhoda
- obecně je velmi obtížné najít takovou \(\Phi\), aby byla zaručena konvergence

To je stejný problém jako u jednorozměrné prosté iterace, ale v soustavách bývá ještě výraznější.

---

# 12. Newtonova metoda pro soustavy

## 12.1 Myšlenka

Odvození je analogické jako u jedné proměnné. Funkci \(F(x)\) nahradíme v okolí bodu \(x_k\) lineární aproximací.

Použijeme Taylorův rozvoj:

\[
F(x)
=
F(x_k)
+
F'(x_k)(x-x_k)
+
\frac12 F''(\xi)(x-x_k)^2.
\]

Soustavu \(F(x)=0\) aproximujeme lineární soustavou:

\[
F(x_k)+F'(x_k)(x-x_k)=0.
\]

---

## 12.2 Odvození iterace

Označíme
\[
h_k=x_{k+1}-x_k.
\]

Pak dostaneme lineární soustavu

\[
F'(x_k)h_k=-F(x_k).
\]

Jakmile spočteme \(h_k\), položíme

\[
x_{k+1}=x_k+h_k.
\]

To je praktický tvar Newtonovy metody pro soustavy.

---

## 12.3 Jacobiho matice

Matice
\[
F'(x_k)
\]
je **Jacobiho matice** funkce \(F\) v bodě \(x_k\).

Pro dvě rovnice o dvou neznámých má tvar:

\[
F'(x,y)=
\begin{bmatrix}
\frac{\partial F_1}{\partial x} & \frac{\partial F_1}{\partial y} \\
\frac{\partial F_2}{\partial x} & \frac{\partial F_2}{\partial y}
\end{bmatrix}.
\]

Aby metoda fungovala, musí být tato matice **regulární**, tedy musí existovat její inverze.

---

## 12.4 Iterační tvar

Formálně lze Newtonovu metodu pro soustavy zapsat i takto:

\[
x_{k+1}
=
x_k
-
[F'(x_k)]^{-1}F(x_k).
\]

V praxi se však obvykle inverzní matice přímo nepočítá.

Místo toho se řeší lineární soustava:

\[
F'(x_k)h_k=-F(x_k).
\]

To je numericky výhodnější.

---

## 12.5 Praktický význam

V každé iteraci je potřeba:
1. spočítat hodnotu \(F(x_k)\),
2. sestavit Jacobiho matici \(F'(x_k)\),
3. vyřešit lineární soustavu pro \(h_k\),
4. aktualizovat bod:
   \[
   x_{k+1}=x_k+h_k.
   \]

---

## 12.6 Výhody a nevýhody

### Výhody
- velmi rychlá konvergence v okolí řešení
- systematická a silná metoda
- vhodná i pro více dimenzí

### Nevýhody
- potřebujeme parciální derivace
- je nutné sestavovat Jacobiho matici
- v každé iteraci musíme řešit lineární soustavu
- metoda je citlivá na počáteční aproximaci

---

# 13. Co je důležité k testu

## 13.1 Umět formulovat problém
- co je kořen rovnice,
- co je řešení soustavy,
- co znamená numerické a iterační řešení.

## 13.2 Znát rozdělení metod
- startovací,
- zpřesňující,
- speciální.

## 13.3 Umět vysvětlit jednotlivé metody
U každé hlavně:
- princip,
- vzorec,
- výhody,
- nevýhody,
- kdy je vhodná.

## 13.4 Znát podmínky konvergence prosté iterace
- zobrazení intervalu/oblasti do sebe,
- kontrakce,
- popř. podmínka pomocí derivace nebo Jacobiho matice.

## 13.5 Znát Newtonovu metodu
- odvození z Taylorova rozvoje,
- geometrický význam,
- vzorec v 1D i pro soustavy,
- proč bývá rychlá,
- kdy může selhat.

## 13.6 Umět porovnat metody
Například:
- **bisekce**: jistá, ale pomalá
- **prostá iterace**: jednoduchá, ale závisí na \(\varphi\)
- **regula falsi**: lepší než bisekce, ale stále startovací
- **Newton**: rychlý, ale vyžaduje derivace
- **sečny**: bez derivace, ale potřebují dvě počáteční hodnoty

---

# 14. Superstručné závěrečné shrnutí

## Jedna rovnice
Hledáme
\[
f(x)=0.
\]

Používané metody:
- bisekce
- prostá iterace
- regula falsi
- Newtonova metoda
- metoda sečen
- Mullerova metoda

## Soustava rovnic
Hledáme
\[
F(x)=0.
\]

Používané metody:
- prostá iterace
- Newtonova metoda pro soustavy

## Hlavní myšlenka
- startovací metody jsou spolehlivé, ale pomalejší,
- zpřesňující metody jsou rychlé, ale citlivější,
- Newtonova metoda je klíčová a velmi důležitá,
- prostá iterace stojí za většinou dalších metod jako obecný princip.

