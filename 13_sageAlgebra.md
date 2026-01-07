---
kernelspec:
  name: sagemath 
  display_name:  SageMath
---

(13_sageAlgebra)=
# Linearna Algebra s SageMath

## Vektroji

Vektorje v SageMath lahko ustvarimo na več načinov. Najenostavnejši je z uporabo ukaza `vector(<seznam>)`, kjer je `<seznam>` seznam števil, ki predstavljajo komponente vektorja.

:::{code-cell} python
v=vector([1,2]) # pazite, argument mora biti seznam ali tuple
v
:::

Do koordinat vektorja a lahko dostopamo kot do kateregakoli seznama v SageMath

:::{code-cell} python
print(v[0])
print(v[1])
:::

:::{warning} Pazite!
Indeksi v SageMath (in Pythonu) se začnejo z `0`, tako da je prva komponenta vektorja `v[0]`, druga pa `v[1]`.
:::

:::{code-cell} python
:tags: [raises-exception]
v[2]
:::

Grafični prikaz vektorjev v ravnini lahko dobimo z metodo `plot()`:

:::{code-cell} python
v.plot(figsize=3)
:::

Vektorje lahko seštevamo in odštevamo, prav tako jih lahko množimo s skalarjem:

:::{code-cell} python
v1 = vector([1,2]) #modro
v2 = vector([1,0]) #ni prikazen
v= 2*v2 #zeleno
w = v1 + v #rdeče
plots = v1.plot(color='blue') + v.plot(color='green') + w.plot(color='red')
show(plots, figsize=4)
:::

Lahko tudi izračunamo skalarni produkt dveh vektorjev:

:::{code-cell} python
v1*v2
:::

$$
v_1 \cdot v_2 = (1,2)\cdot(1,0)  = 1\cdot 1 + 2\cdot 0 = 1
$$ 

ali dolžino oz. normo vektorja:

:::{code-cell} python
print("$$ |v_1|= " + latex(v1.norm()) + "$$")
:::

$$
|v_1|= \sqrt{5} 
$$

Zgornje ukaze lahko uporabimo za zapis funkcije v SageMath, ki določi če sta vektorja pravokotna:

:::{code-cell} python
def sta_pravokotna(v,u):  # definira funkcijo z dvema argumentoma u,v
  return v*u==0           # vrne, ali je skalarni produkt argumentov enak nič ali ne
:::

:::{code-cell} python
sta_pravokotna(v1,v2)
:::

:::{code-cell} python
v3=vector([0,1])
sta_pravokotna(v2,v3)
:::

Večina teh ukazov in funkcij deluje tudi v več dimenzijah:

:::{code-cell} python
u1=vector([1,0,0])
u2=vector([0,1,0])
u3=vector([1,2,3])
u1+u2
:::

$$
u_1 + u_2 = (1,0,0) + (0,1,0) = (1+0,0+1,0+0) = (1,1,0)
$$

:::{code-cell} python
print(u2*u3)
print(u3.norm())
:::

$$
u_2 \cdot u_3 = (0,1,0)\cdot(1,2,3)  = 0\cdot 1 + 1\cdot 2 + 0\cdot 3 = 2
$$

$$
|u_3|= \sqrt{1^2 + 2^2 + 3^2} = \sqrt{14}
$$

Tudi risanje!

:::{code-cell} python
u3.plot()
:::

## Vectorski prostori

SageMath razume več standardnih številskih sistemov:

:::{code-cell} python
print(ZZ) #cela števila
print(QQ) #racionalna števila
print(RR) #raalna števila 
print(CC) #kompleksna števila
print(SR) #simbolični kolobar
:::

Vsak od njih vsebuje vedno več splošnih elementov:

:::{code-cell} python
print(3 in ZZ, 1/2 in ZZ)
print(3 in QQ, 1/2 in QQ, pi in QQ)
print(3 in RR, 1/2 in RR, pi in RR, I in RR)
print(3 in CC, 1/2 in CC, pi in CC, I in CC, x in CC)
print(3 in SR, 1/2 in SR, pi in SR, I in SR, x in SR)
:::
 
$$ 3 \in \mathbb{Z}, \quad \frac{1}{2} \notin \mathbb{Z} $$
$$ 3 \in \mathbb{Q}, \quad \frac{1}{2} \in \mathbb{Q}, \quad \pi \notin \mathbb{Q} $$
$$ 3 \in \mathbb{R}, \quad \frac{1}{2} \in \mathbb{R}, \quad \pi \in \mathbb{R}, \quad i \notin \mathbb{R} $$
$$ 3 \in \mathbb{C}, \quad \frac{1}{2} \in \mathbb{C}, \quad \pi \in \mathbb{C}, \quad i \in \mathbb{C}, \quad x \notin \mathbb{C} $$
$$ 3 \in SR, \quad \frac{1}{2} \in SR, \quad \pi \in SR, \quad i \in SR, \quad x \in SR $$

Ustvarimo lahko vektorske prostore nad katerim koli poljem: $\mathbb{Q}$, $\mathbb{R}$ ali $\mathbb{C}$, vendar, kot smo že videli, SageMath najbolje deluje z racionalnimi števili.

Za ustvarjanje vektorskega prostora uporabimo ukaz `VectorSpace(<polje>, <dimenzija>)`, kjer je `<polje>` polje nad katerim definiramo vektorski prostor, `<dimenzija>` pa dimenzija vektorskega prostora.

:::{code-cell} python
V = VectorSpace(QQ, 3) #vektorski prostor dimenzije 3 nad racionalnimi števili
v = V([1,2,3]) # (1,2,3) kot vector v prostoru V
:::

::::{warning} Pazite!
Včasih SageMath ugiba, kaj smo mislili:

:::{code-cell} python
w = vector(RR, [1,2,3]) #w kot vector nad RR
print(w == v)
print(w in V)
:::

včasih pa ne:

:::{code-cell} python
w=vector(CC,[1,2,3]) #w kot vector nad CC
print(w==v)
print(w in V)
:::

::::

Izračunamo lahko osnovo za vektorski prostor:

:::{code-cell} python
V.basis()
:::

Izračunamo lahko podprostor prostora $V$, ki ga generira množica vektorjev:

:::{code-cell} python
u1= V([1,0,0]); u2= V([1,1,0]); 
W=V.span([u1,u2])
W
:::

:::{code-cell} python
u3=V([0,3,0]) # vektor  (1,2,3) v V
u4=V([0,0,1]) # vektor  (0,0,1) v V
(u3 in W, u4 in W) # preveri, ali sta vektorja v podprostoru W
:::

:::{exercise}
:label: ex-vektorij
1. Napišite funkcijo, ki kot argumenta prejme dva vektorja in vrne kot med njima.
2. Napišite funkcijo, ki določa, ali je seznam vektorjev  linearno neodvisen nad racionalnimi števili.
  **Namig**: seznam vektorjev je linearno neodvisna natanko takrat, ko je njegova velikost enaka dimenziji podprostora, ki ga generirara.
:::



::::{solution} ex-vektorij
:class: tip dropdown
1. Če je $\theta$ kot med vektorjema $u$ in $v$, potem velja $$ u \cdot v = |u| \cdot |v| \cos(\theta),$$ ali enakovredno $$ \theta = \arccos\left(\frac{u \cdot v}{|u| \cdot |v|}\right)$$

:::{code-cell} python
def kot_med_vektorjem(u,v):
  # potrebujemo metodo simplify(), da dobimo dejanski kot
  return arccos((u*v)/(u.norm()*v.norm())).simplify() 
:::

Poskusimo funkcijo:

:::{code-cell} python
v=vector([1,0]); u=vector([1,1])
kot_med_vektorjem(u,v)
:::

---

2. Slediti moramo le namigu:

:::{code-cell} python
def so_linearno_neodvisni(sezVekt):
  dim=len(sezVekt[0]) #Ugotovimo dimenzijo vektorjev  
  V=VectorSpace(QQ,dim) # Ustvarimo vektorski prostor
  W=V.span(sezVekt) #Ustvarimo podprostor 
  return W.dimension()==len(sezVekt) # Preverite, ali je dimenzija enaka dolžini liste
:::

Poskusimo:

:::{code-cell} python
u1=vector(QQ, [1,0]); u2=vector(QQ, [1,1]); u3=vector(QQ, [0,1])
print(so_linearno_neodvisni([u1,u2]))
print(so_linearno_neodvisni([u1,u2,u3]))
:::

::::

## Matrike: izdelava in osnovne operacije

Matrike v SageMath lahko ustvarimo na več načinov. Najenostavnejši je z uporabo ukaza `matrix(<seznam seznamov>)`, kjer je `<seznam seznamov>` seznam vrstic matrike, vsaka vrstica pa je predstavljena kot seznam števil.

:::{code-cell} python
matrix([[1,2],[3,4]])
:::

Lahko tudi najprej določimo dimenzije in nato podamo vse vnose na seznamu.

:::{code-cell} python
M= matrix(4,2, [1,2,3,4,5,6,7,8]) # argumenti so st_vrstic, 
M                                 # st_stolpcev, seznam vnosov
:::

Če je matrika, ki jo želimo ustvariti, kvadratna, lahko v argumentih izpustimo število stolpcev:

:::{code-cell} python
matrix(2,[1,2,3,4])
:::

Privzeto SageMath konstruira matriko nad najmanjšim vesoljem, ki vsebuje koordinate:

:::{code-cell} python
print(parent(matrix(2,[1,2,3,4])))
print(parent(matrix(2,[1,2/1,3,4])))
print(parent(matrix(2,[x,x^2,x-1,x^3])))
:::

Lahko pa tudi določimo polje, nad katerim želimo delati:

:::{code-cell} python
matrix(QQ,2,[1.1,1.2,1.3,1.4])
:::

Nekatere standardne matrike imajo svoj ukaz:

:::{code-cell} python
identity_matrix(3) # enotska matrika velikosti 3x3
:::

Matrike, katerih vsi vnosi so enaki $0$:

:::{code-cell} python
print("Vse ničle:")
print(zero_matrix(3,2),"\n")
print("Vse ničle,kvadratna:")
print(zero_matrix(2), "\n")
:::

ali vsi vnosi enaki $1$:

:::{code-cell} python
print("Vse 1:")
print(ones_matrix(3,2),"\n")
print("Vse 1, kvadratna:")
print(ones_matrix(3), "\n")
:::

:::{exercise}
:label: ex-matrikeIzdelava
1. V programu SageMath sestavite naslednjo matriko nad racionalnimi števili:
$$\left(\begin{array}{rrr}
5 & 3 & 2 \\
4 & 7 & 10 \\
2 & 11 & 1
\end{array}\right)$$

2. Sestavite identitetno matriko 10x10.
3. Sestavite ničelno matriko 20x10.
4. Napišite matriko velikosti 10 x 10, katere vsi vnosi so $\sqrt{2}$
:::


::::{solution} ex-matrikeIzdelava
:class: tip dropdown

1. 
:::{code-cell} python
matrix(QQ,3, [5,3,2,4,7,10,2,11,1])
:::

---

2. 
:::{code-cell} python
identity_matrix(10)
:::

---

3.
:::{code-cell} python
zero_matrix(20,10)    
:::

---

4.
:::{code-cell} python
M= sqrt(2)*ones_matrix(10,10)
latex(M)
:::
$$ \left(\begin{array}{rrrrrrrrrr}
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} \\
\sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2} & \sqrt{2}
\end{array}\right) $$

::::

---

Matrike lahko seštevamo in odštevamo, prav tako jih lahko množimo s skalarjem:

:::{code-cell} python
A=matrix(2,[1,1,0,1])
B=matrix(2,[1,0,1,1])
print(A, "\n") # znak "\n" je prelom vrstice
print(B) 
:::

:::{code-cell} python
print(A+B, "\n")
print(A-B, "\n")
print(A*B, "\n")
print(A^3)
:::

Če je $A$ kvadratna matrika, lahko izračunamo tudi njeno inverzno matriko $A^{-1}$ z ukazom `A.inverse()`, ali z ukazom `A^(-1)`:

:::{code-cell} python
print(A.inverse(), "\n")
A.inverse()==A^(-1)
:::

**Pogost primer uporabe:** Pišemo dokument v LaTeXu in moramo izračunati inverzno velike matrike, npr.

$$
\left(\begin{array}{rrrrr}
1 & 1 & 1 & 1 & 1 \\
2 & 3 & 4 & 5 & 6 \\
3 & 4 & 7 & 8 & 9 \\
4 & 5 & 6 & 10 & 11 \\
5 & 6 & 7 & 8 & 12
\end{array}\right)
$$

Nekaj minut lahko porabimo za ročni izračun njeno inverzno (in tvegate, da bomo naredili neumne napake), ali nekaj sekund za vnos matrike v SageMath.

:::{code-cell} python
A=matrix(ZZ,5, [1,1,1,1,1,2,3,4,5,6,3,4,7,8,9,4,5,6,10,11,5,6,7,8,12])
A^(-1)
:::

Pridobimo lahko celo različico LaTeXa in jo vrnemo v naš dokument:

:::{code-cell} python
latex(A^(-1))
:::

$$ 
\left(\begin{array}{rrrrr}
\frac{5}{6} & -\frac{13}{6} & \frac{1}{2} & \frac{1}{3} & \frac{1}{3} \\
\frac{2}{3} & \frac{8}{3} & -1 & -\frac{1}{3} & -\frac{1}{3} \\
\frac{1}{6} & -\frac{1}{6} & \frac{1}{2} & -\frac{1}{3} & 0 \\
\frac{1}{3} & 0 & 0 & \frac{1}{3} & -\frac{1}{3} \\
-1 & -\frac{1}{3} & 0 & 0 & \frac{1}{3}
\end{array}\right)
$$

Seveda, ko smo se naučili, okolja `array` ni najboljše za matrike, vendar ni težko prilagoditi izhod LaTeXa za okolje `bmatrix`,`pmatrix` ali kateregakoli drugega, ki ga želite uporabiti.

S metodo `is_invertible()` lahko preverimo, ali je matrika obrnljiva:

:::{code-cell} python
A.is_invertible()
:::

...vendar je rezultat odvisen od tega, kje je matrika definirana.

:::{code-cell} python
A.parent()
:::

:::{code-cell} python
B=matrix(QQ,5, [1,1,1,1,1,2,3,4,5,6,3,4,7,8,9,4,5,6,10,11,5,6,7,8,12])
print(A==B)
print(B.parent())
print(A.is_invertible())
print(B.is_invertible())
:::

Z metodama `det()` in `trace()` izračunamo determinanto oziroma sled matrike.

:::{code-cell} python
print("Determinanta A:", A.det())
print("Sled A:", A.trace())
:::

$$ A = \left(\begin{array}{rrrrr}
1 & 1 & 1 & 1 & 1 \\
2 & 3 & 4 & 5 & 6 \\
3 & 4 & 7 & 8 & 9 \\
4 & 5 & 6 & 10 & 11 \\
5 & 6 & 7 & 8 & 12
\end{array}\right) $$

$$ \det(A) = 1$$

$$ \operatorname{tr}(A) = 1 + 3 + 7 + 10 + 12 = 33
$$

:::{exercise}
:label: ex-matrikeOperacije

1. Naj bosta $A$ in $B$ matriki 
  $$ A = \left(\begin{array}{rr}
  1 & 3 \\
  7 & 8
  \end{array}\right)
  \qquad
  B= \left(\begin{array}{rr}
  4 & 8 \\
  9 & 15
  \end{array}\right).$$
  Poiščite 
   $A+B$, 
   $AB$, 
   $B^{-1}$, in 
   $B^{-1} A B$

in rezultate zapišite v LaTeX.

2. Ugotovite katere od naslednjih matrik so obrnljive nad $\mathbb{Z}$? Kaj pa $\mathbb{Q}$?
$$
A=\left(\begin{array}{rr} 2 & 8 \\ 4 & 16 \end{array}\right) \qquad
B=\left(\begin{array}{rr} 2 & 7 \\ 13 & 24 \end{array}\right) 
$$
$$
C=\left(\begin{array}{rr} 1 & 4 \\ 2 & 7 \end{array}\right) \qquad
D=\left(\begin{array}{rr} 4 & 6 \\ 8 & -2 \end{array}\right) 
$$

:::



::::{solution} ex-matrikeOperacije
:class: tip dropdown
1. Definiramo matrike in izračunamo zahtevane operacije:
:::{code-cell} python
A=matrix( [[1,3],[7,8]] )
B=matrix( [[4,8],[9,15]] )
print(A+B, "\n")
print(A*B,"\n")
print(B.inverse(),"\n")
print(B^(-1)*A*B,"\n")
:::

$$ A + B = 
\left(\begin{array}{rr}
5 & 11 \\
16 & 23
\end{array}\right) 
$$

$$ AB =
\left(\begin{array}{rr}
31 & 53 \\
100 & 176
\end{array}\right)
$$

$$ B^{-1} =
\left(\begin{array}{rr}
-\frac{5}{4} & \frac{2}{3} \\
\frac{3}{4} & -\frac{1}{3}
\end{array}\right) 
$$

$$ B^{-1} A B =
\left(\begin{array}{rr}
\frac{335}{12} & \frac{613}{12} \\
-\frac{121}{12} & -\frac{227}{12}
\end{array}\right) 
$$

---

2. Definiramo matrike nad $\mathbb{Z}$:

:::{code-cell} python
A=matrix(ZZ, [ [2,8], [4,16] ] )
B=matrix(ZZ, [ [2,7], [13,24] ] )
C=matrix(ZZ, [ [1,4], [2,7] ] )
D=matrix(ZZ, [ [4,6], [8,-2] ] )
:::

Z uporabo cikla `for` preverimo obrnljivost matrik nad $\mathbb{Z}$ in $\mathbb{Q}$:

:::{code-cell} python
for M in [A,B,C,D]: 
  if M.det() == 0:
    print(M, "\n ni obrnljiva nad QQ\n")
  elif M.is_invertible():
    print(str(M)+"\n"+"je obrnljiva nad ZZ in njena inverzna je \n"+str(M.inverse())+"\n")
  else:
    print(str(M)+"\n"+"Ni obrnljiva nad ZZ, pa je nad QQ.\nNjena inverzna je \n"+str(M.inverse())+"\n")
:::
::::


## Upravljanje vnosov matrik in reševanje sistemov linearnih enačb


SageMath ima različne metode za dostop do vnosov matrike. 

:::{code-cell} python
M = matrix(QQ, [[1,2,3],[4,5,6],[7,8,9]])
M
:::

$$
M = \left(\begin{array}{rrr}
1 & 2 & 3 \\
4 & 5 & 6 \\
7 & 8 & 9
\end{array}\right)
$$

Metodi `nrows()` in `ncols()` vrneta število vrstic oziroma stolpcev matrike:

:::{code-cell} python
print(M.nrows())
print(M.ncols())
:::

Z metodama `rows()` in `columns()` dobimo seznam vrstic oziroma stolpcev matrike:

:::{code-cell} python
M.rows()
:::

:::{code-cell} python
M.columns()
:::

Metodi `row(i)` in `column(i)` vrneta $i$-to vrstico oziroma stolpec. `M.row(i)` je enako `M.rows()[i]`.

:::{code-cell} python
M.row(1) == M.rows()[1]
:::

Metoda `diagonal()` vrne seznam z vnosi na diagonali. To deluje tudi pri matrikah, ki niso kvadratne.

:::{code-cell} python
M.diagonal()
:::

Ta metoda deluje tudi pri matrikah, ki niso kvadratne:

:::{code-cell} python
N=matrix(QQ, [[1,2,3],[4,5,6]])
N.diagonal()
:::

SageMath nam omogoča tudi izdelavo novih matrik iz vrstičnih in/ali stolpčnih vektorjev.

:::{code-cell} python
print(M.matrix_from_columns([0,2]), "\n")
print(M.matrix_from_rows([0,1]), "\n")
print(M.matrix_from_rows_and_columns([0,2],[0,2]))
:::

Metoda `matrix_from_rows_and_columns()` vrne matriko, katere vnosi so v izbranih vrsticah **in** izbranih stolpcih.

---

Uporabimo lahko tudi imenovane osnove operacije v matrikah. Npr. z metodo `rescale_row(i, k)` pomnožimo $i$-to vrstico z $k$:

:::{code-cell} python
M.rescale_row(1,-1/4) # ne pozabite, da indeksi začnejo z 0
M
:::

Podobno, z metodo `rescale_column(j, k)` pomnožimo $j$-ti stolpec z $k$:

:::{code-cell} python
M.rescale_col(2,-1/3); M
:::

Upoštevajte, da te metode **spreminjajo matriko na mestu**. Vse, kar smo storili, lahko prekličemo.

:::{code-cell} python
M.rescale_row(1,-4)
M.rescale_col(2,-3)
M 
:::


Večkratnik vrstice ali stolpca lahko dodamo drugi vrstici ali stolpcu z uporabo metode `add_multiple_of_row()`. 
Naslednji ukaz vzame $-4$ krat vrstico `0` in jo doda vrstici `1`.

:::{code-cell} python
M.add_multiple_of_row(1,0,-4); M
:::

:::{code-cell} python
M.add_multiple_of_row(1,0,4); M #prekličemo
:::

Seveda lahko to storimo tudi s stolpci:

:::{code-cell} python
M.add_multiple_of_column(0,2,-3); M 
:::

:::{code-cell} python
M.add_multiple_of_column(0,2,3); M  #prekličemo
:::

Zamenjamo lahko dve vrstici z metodo `swap_rows(i,j)`:

:::{code-cell} python
M.swap_rows(1,0); M
:::

podobno, z metodo `swap_columns(i,j)` zamenjamo dva stolpca:

:::{code-cell} python
M.swap_columns(0,2); M
:::

:::{code-cell} python
M.swap_rows(1,0) #prekličemo
M.swap_columns(0,2); M
:::

Če želimo dobiti ešelonsko obliko matrike uporabimo metodo `echelon_form()` ali metodo `echelonize()`. Razlika je v tem, da prva vrne matriko, druga pa to naredi na mestu.

:::{code-cell} python
M.echelon_form()
:::

:::{code-cell} python
M
:::

:::{code-cell} python
M.echelonize(); M
:::

Lahko uporabimo ta način za reševanje sistemov linearnih enačb. Predpostavimo, da imamo sistem

$$ \begin{aligned}
  2x_1 +  4x_2  + 6x_3 +2 x_4 +4 x_5 &= 56 \\
  x_1 + 2 x_2  + 3 x_3 +  x_4 + x_5 &= 23\\
  2x_1 + 4 x_2  + 8x_3  &= 34\\
  3x_1 + 6  x_2  + 7 x_3 + 5 x_4 + 9 x_5 &= 101
\end{aligned}$$

Matrika, ki je povezana s tem sistemom, je
$$ \left(\begin{array}{rrrrr} 2 & 4 & 6 & 2 & 4 \\ 1 & 2 & 3 & 1 & 1 \\ 2 & 4 & 8 & 0 & 0 \\ 3 & 6 & 7 & 5 & 9 \end{array}\right) $$

:::{code-cell} python
M = matrix(QQ, [[2,4,6,2,4],[1,2,3,1,1],[2,4,8,0,0],[3,6,7,5,9]]); M
:::

Iščemo rešitve sistema $Mx=b$, kjer je $x$ (stolpčni) vektor $(x_1, x_2, x_3, x_4, x_5)$ in $b$ (stolpčni) vektor $(56,23,34,101)$.

Z metodo `aug()` lahko ustvarimo povečano matriko $M|b$:

:::{code-cell} python
b = vector(QQ, [56, 23, 34, 101])
M_aug=M.augment(b); M_aug
:::

Zdaj lahko uporabimo metodo `echelon_form()` na povečani matriki, da dobimo ešelonsko obliko:


:::{code-cell} python
M_aug.echelon_form()
:::

To pomeni, da je naš prvotni sistem enačb enak
$$ \begin{aligned}
  x_1 +  2x_2  +4 x_4 &= 21 \\
   x_3 -  x_4 &= -1\\
  x_5  &= 5\\
\end{aligned}$$

To pomeni, da imamo dve prosti spremenljivki (recimo $x_2$ v $x_4$) in da so zato množica rešitev vsi vektorji oblike $t(-4,0,1,1,0)+s(-2,1,0,0,0,0)+(21,0,-1,0,5)$, kjer sta $t$ in $s$ poljubni števili.

Lahko preverimo to eksperimentalno. Iz našega znanja o linearni algebri je razvidno, da je dovolj preveriti $(s,t) = (1,0)$ in $(s,t)=(0,1)$.

:::{code-cell} python
s=1; t=0
x=s*vector(QQ,[-4,0,1,1,0])+t*vector(QQ,[-2,1,0,0,0])+vector(QQ,[21,0,-1,0,5])
M*x
:::

:::{code-cell} python
s=0; t=1
x=s*vector(QQ,[-4,0,1,1,0])+t*vector(QQ,[-2,1,0,0,0])+vector(QQ,[21,0,-1,0,5])
M*x
:::

:::{exercise}
:label: ex-matrikeEnacbe

1. Naj bo $A$ matrika $$ \left(\begin{array}{rrr} 3 & 17 & 23 \\ \frac{1}{32} & 2 & 17 \\ 16 & -23 & 27 \end{array}\right). $$
Uporabite osnovne operacije, opisane v tem poglavju, da pretvorite $A$ v ešelonsko obliko. Preverite, ali je vaš rezultat pravilen, tako da izračunate ešelonsko obliko s pomočjo SageMath-a. 

<!-- 2. Z uporaba ukazov iz tega poglavja pretvorite matriko na levi v matriko na desni.


$$\begin{aligned}
\left(\begin{array}{rrrr} -1 & -2 & 1 & -13 \\ -3 & -1 & 1 & 1 \\ 1 & 1 & -1 & 1 \\ -2 & -1 & -9 & 1 \end{array}\right) 
&\qquad
\left(\begin{array}{rrrr} 1 & 0 & 0 & 100 \\ 0 & 1 & 0 & 12 \\ 0 & 0 & 1 & 111 \\ 0 & 0 & 0 & 202 \end{array}\right) \\
 \left(\begin{array}{rrrrr} -7 & -1 & 1 & 4 & 0 \\ -8 & -2 & 4 & 2 & 6 \\ 1 & 1 & -3 & 3 & 0 \\ 0 & 8 & 13 & -2 & 0 \\ 1 & 4 & 0 & -1 & 4 \end{array}\right)
&\qquad
\left(\begin{array}{rrrrr} -7 & -8 & 1 & 0 & 1 \\ -1 & -2 & 1 & 8 & 4 \\ 1 & 4 & -3 & 13 & 0 \\ 4 & 2 & 3 & -2 & -1 \\ 0 & 6 & 0 & 0 & 4 \end{array}\right)\\
\left(\begin{array}{rrr} 0 & -1 & 1 \\ -2 & 1 & -1 \\ 1 & 0 & 1 \end{array}\right) 
&\qquad
\left(\begin{array}{rrrr} 0 & -1 & 1 & 4 \\ -2 & 1 & -1 & -1 \\ 1 & 0 & 1 & 1 \end{array}\right)
\end{aligned}$$ -->


2. Poiščite rešitve naslednjega sistema enačb
$$ \begin{aligned}
x_1 + 2x_2 + x_4 &= 7\\
x_1 +x_2 +x_2 -x_4 &= 3\\
3x_1+x_2+5x_3-7x_4&=1
\end{aligned}$$

:::



::::{solution} ex-matrikeEnacbe
:class: tip dropdown
1. Uporabimo osnovne operacije za pretvorbo matrike v ešelonsko obliko:

:::{code-cell} python
A = matrix(QQ, [[3,17,23],[1/32,2,17],[16,-23,27]]); print(A, "\n")
A.rescale_row(1,32); print(A, "\n")
A.swap_rows(0,1); print(A, "\n")
A.add_multiple_of_row(1,0,-3); print(A, "\n")
A.add_multiple_of_row(2,0,-16); print(A, "\n")
A.rescale_row(1,-1/175); print(A, "\n")
A.add_multiple_of_row(0,1,-64); print(A, "\n")
A.add_multiple_of_row(2,1,1047); print(A, "\n")
A.rescale_row(2,175/166148); print(A, "\n")
A.add_multiple_of_row(0,2,7776/175); print(A, "\n")
A.add_multiple_of_row(1,2,-1609/175); print(A, "\n")
:::

:::{code-cell} python
A = matrix(QQ, [[3,17,23],[1/32,2,17],[16,-23,27]]); # definicija
A.echelon_form() #preverimo z metodo
:::

2. Najprej sestavimo matriko in vektor desne strani:
:::{code-cell} python
M=matrix(QQ, [[1,2,0,1],[1,1,1,-1],[3,1,5,-7]])
b=vector(QQ,[7,3,1])
:::
Nato ustvarimo povečano matriko in izračunamo njeno ešelonsko obliko:
:::{code-cell} python
M_aug=M.augment(b)
M_aug.echelon_form()
:::

Iz ešelonske oblike vidimo, da je rešitev sistema ima dva prosti spremenljivki, recimo, $x_3 =t$ in $x_4 =s$. Zato je splošna rešitev
$$ (x_1,x_2,x_3,x_4) = t(-2,1,1,0) + s(1,2,0,1) + (1,2,0,0) $$

::::