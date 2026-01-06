---
kernelspec:
  name: sagemath 
  display_name:  SageMath
---

(12_sageUvod)=
# Uvod v SageMath

## Kaj je SageMath?

[SageMath](https://www.sagemath.org/) (na kratko Sage) je **brezplačen** odprtokodni programski sistem za matematiko.Lahko si ga predstavljate kot Phyton na matematičnih steroidih.
Poslanstvo sistema SageMath je ustvariti učinkovito brezplačno odprtokodno alternativo sistemom Magma, Maple, Mathematica in Matlab.


:::{seealso} Glej tudi
SageMath se pogosto uporablja in na spletu je na voljo veliko gradiva. Navajam nekaj najuporabnejših virov.

- SageMath Documentation: [https://doc.sagemath.org/](https://doc.sagemath.org/)
- SageMath Reference Manual: [https://doc.sagemath.org/html/en/reference/index.html](https://doc.sagemath.org/html/en/reference/index.html)
- A tour of SageMath: [https://doc.sagemath.org/html/en/a_tour_of_sage/](https://doc.sagemath.org/html/en/a_tour_of_sage/)
- Introductory SageMath tutorial: [https://doc.sagemath.org/html/en/prep/Intro-Tutorial.html](https://doc.sagemath.org/html/en/prep/Intro-Tutorial.html)
- SageMath tutorial: [https://doc.sagemath.org/html/en/tutorial/index.html](https://doc.sagemath.org/html/en/tutorial/index.html)
- SageMath thematic tutorial: [https://doc.sagemath.org/html/en/thematic_tutorials/index.html](https://doc.sagemath.org/html/en/thematic_tutorials/index.html)
- SageMath repository of interacts (interaktivni programčki): [https://wiki.sagemath.org/interact](https://wiki.sagemath.org/interact)
- SageMath quickref cards (reference za pomoč): [https://wiki.sagemath.org/quickref](https://wiki.sagemath.org/quickref)
:::

## Kako uporabljamo SageMath?

SageMath lahko uporabljate na več načinov, vsak od njih ponuja različno raven nadzora in različne funkcije. Glavni načini uporabe so:
- **SageCell** [https://sagecell.sagemath.org/](https://sagecell.sagemath.org/) Zelo uporabno za enostavne in hitre naloge.
- **Lokalna namestitev**. Ni priporočljivo za začetnike. Če nimate izkušenj z nameščanjem programske opreme, je to lahko nekoliko zapleteno. Poleg tega skoraj nikoli ni potrebna. Edini dober razlog za lokalno namestitev programa SageMath je, da nimate dostopa do interneta.
- **Interaktivni programčki**. Podobno kot apleti GeoGebre. Za uporabo interaktivnih programčkov ni treba imeti predznanja. Za njihovo ustvarjanje pa potrebujete napredno poznavanje programa SageMath, ki presega vsebine tega predmeta.
- **CoCalc.com** [https://cocalc.com/](https://cocalc.com/). S preprostimi besedami, CoCal je za SageMath, kar je Overleaf za LaTeX.


## SageMath na CoCalcu

Obstajajo različne načine za uporabo SageMath, najpogosteje so:

- Na ukazni vrstici (terminalu). Ta način je primeren za napredne uporabnike in ni priporočljiv za začetnike. V tem primeru, SageMath deluje podobno kot običajen programski jezik, ukaze napišemo v terminal in dobimo rezultate. Ukazna vrstica običajno izgleda kot [Sliko %s](#fig-terminal).

:::{figure} sagemath/terminal.png
:label: fig-terminal
:alt: Ukazna vrstica SageMath
:width: 400px
Ukazna vrstica SageMath
:::

- Scripting: Kodo napišemo v besedilno datoteko in jo nato zaženete v ukazni vrstici. Ta način je prav tako primeren za napredne uporabnike in ni priporočljiv za začetnike, saj zahteva poznavanje osnov programiranja.

- **Interaktivno v zvezku (Jupyter Notebook)**. Ta način je najbolj primeren za začetnike in je tisti, ki ga bomo uporabljali v tem predmetu. SageMath lahko uporabljamo v zvezkih Jupyter, ki omogočajo kombiniranje besedila, matematičnih izrazov in kode v enem dokumentu. Zvezki so zelo uporabni za učenje, raziskovanje in dokumentiranje matematičnih izračunov. V tem predmetu bomo uporabljali CoCalc, spletno platformo, ki omogoča uporabo SageMath v zvezkih Jupyter brez potrebe po lokalni namestitvi.

:::{exercise}
:label: ex-racunCocalc
Pojdi na [https://cocalc.com/](CoCal.com) and ustvarite račun.
:::

:::{exercise}
:label: ex-ustvariDatoteko
Ustvarite nov Jupyter zvezek na CoCal-u z jedrom SageMath
:::



::::{solution} ex-ustvariDatoteko
:class: tip dropdown

1. Na CoCal-u ustvarite nov datoteko.
:::{image} ./sagemath/jupyter1.png
:width: 400px
:align: center
:::

2. Poimenujete ga in izberite "Jupyter Notebook" (pazite, da izberite "Jupyter Notebook" in ne "SageMath Notebook").
:::{image} ./sagemath/jupyter2.png
:width: 400px
:align: center
:::


3. Izberite kernel SageMath 10.4 (ali najnovejšo različico).
:::{image} ./sagemath/jupyter3.png
:width: 400px
:align: center
::::

V beležnici Jupyter imamo dve vrsti celic: *Code* (koda) in *Text* (besedilo) (glej [Sliko %s](#fig-celice)).

:::{figure} sagemath/jupyter4.png
:label: fig-celice
:alt: Celice v Jupyter
:width: 400px
Celice v Jupyter
:::


V celici z besedilo lahko uporabite _Markdown_ ali standardne besedilo. Priporočamo, da uporabite _Markdown_, saj omogoča boljšo oblikovanje besedila in vključevanje matematičnih izrazov.

:::{seealso} Glej tudi
Markdown je preprost jezik za označevanje besedila, ki omogoča enostavno oblikovanje besedila. Pristop je podoben LaTeX-u, vendar je veliko enostavnejši za uporabo, na žalost, pa tudi manj zmogljiv.

Osnovne značilnosti Markdowna vključujejo:

- Naslovi: Uporabite `# Naslov` za naslove. Več `#` pomeni nižjo raven naslova.
- Krepko in ležeče besedilo: Uporabite `**krepko**` za **krepko** besedilo in `_ležeče_` za _ležeče besedilo_.
- Seznami: Uporabite `-` ali `*` za neurejene sezname in številke za urejene sezname.
- Povezave: Uporabite `[besedilo](URL)` za ustvarjanje povezav.
- V Jupyter zvezkih lahko vključite tudi matematični izraze z uporabo LaTeX sintakse, na primer `$x^2 + y^2 = z^2$` za inline izraze in `$$E = mc^2$$` za prikazne izraze.


Za več informacij o Markdownu si oglejte naslednje vire: [Markdown osnovna sintaksa](https://www.markdownguide.org/basic-syntax/)

Ta učbenik je napisan v Myst Markdown, ki je razširitev Markdowna.
:::



V celici z kodo vnesemo ukaze SageMath. Za izvedbo kode pritisnite {kbd}`Shift` + {kbd}`Enter` ali kliknite na gumb "Run" v orodni vrstici. Rezultati se bodo prikazali neposredno pod celico z kodo.

## SageMath kot kalkulator

SageMath lahko uporabljamo kot kalkulator za osnovne aritmetične operacije, kot so seštevanje, odštevanje, množenje in deljenje. Poleg tega lahko uporabljamo tudi bolj zapletene matematične funkcije in operacije.

Z nekaj manjšimi izjemami Sage uporablja programski jezik Python, zato so osnovne aritmetične operacije in druge osnove programiranja v SageMath zelo podobne tistim v Pythonu.


Poglejte naslednje primere. Še bolj pa jih preizkusite sami v svojem CoCalc zvezku!

:::{code-cell} python
1+1
:::

:::{code-cell} python
( 1 + 2 * (3 + 5) ) * 2
:::

Simbol * pomeni množenje, ki se ne sme izpustiti, tudi v izrazih, kot je $2x$: `2*x`. Za združevanje simbolov uporabljamo oklepaj `(` `)` nikoli `[` `]` ali `{` `}`.

:::{code-cell} python
2**3 # ** pomeni potenciranje, kot v Pythonu
:::

:::{code-cell} python
2^3 # ampak ^ pomeni tudi potenciranje, za razliko od Pythona
:::

:::{code-cell} python
-3^2 # pazite! 
:::

Pri vzeto SageMath poskuša privzeto vrniti izraz, ki je čim bolj natančen. To je `10/3` vrne racionalno število $10/3$ (in ne decimalno približek, kot je $3,33333$). Če želimo številčni približek, lahko enemu od števil preprosto dodamo decimalno piko.

:::{code-cell} python
20.0 / 6
:::

Kvadratne korene lahko izračunamo z ukazom `sqrt()`. Upoštevajte, da če je argument celo število, SageMath interpretira rezultat kot simbolno število.

:::{code-cell} python
sqrt(2)
:::

:::{code-cell} python
sqrt(8)
:::

Seveda, lahko dobimo številčni približek z ukazom `sqrt(8.0)`. Na splošno lahko dobimo numerične približke izrazov z (enakovrednimi) ukazi `n()`, `N()`, `numerical_approx()`. Vsi zgornji ukazi imajo neobvezen argument `digits` za določitev natančnosti približke.

:::{code-cell} python
n(sqrt(8), digits=50)
:::

V [Tabeli %s](#tab-operacije) so povzete osnovne aritmetične operacije v SageMath-u.

:::{list-table} Osnovne aritmetične operacije v SageMath-u
:header-rows: 0
:label: tab-operacije

* - Seštevanje ($a+b$)
  - `a+b` 
* - Odštevanje ($a-b$)
  - `a-b`
* - Množenje ($ab$)
  - `a*b` 
* - Deljenje ($\frac{a}{b}$)
  - `a/b`
* - Potenciranje ($a^b$)
  - `a**b` ali `a^b` 
* - Kvadratni koren ($\sqrt{a}$)
  - `sqrt(a)`
* - Splošni koren ($\sqrt[n]{a}$)
  - `a^(1/n)`
:::

:::{exercise}
:label: ex-racunSageMath
Z uporabo SageMath-a rešite naslednje naloge, napišite rešitve v ločene celice besedila z uporabo LaTeX-a.

1. Deli $28$ z $2$ povišanim na $5$. potenco, kot racionalno število, nato pa dobi njegov desetiški približek točke, kjer so vse cifre pomembne.
1. Izračunajte decimalni približek števila $\sqrt[3]{2}$.
1. S programom SageMath izračunajte $(-9)^{1/2}$. Opišite rezultat.
:::

::::{solution} ex-racunSageMath
:class: tip dropdown

:::{code-cell} python
28/(2**5)
:::

:::{code-cell} python
n(28/(2**5), digits=3)
:::

Ker je $$\frac{28}{32} = 0.875,$$ je njegov decimalni približek z vsemi pomembnimi ciframi $0.875$.

---

:::{code-cell} python
n(2^(1/3), digits=10)
:::

Torej je decimalni približek števila $\sqrt[3]{2}$ približno $1.259921049$.

---

:::{code-cell} python
(-9)^(1/2)  
:::

Rezultat je $3i$, kjer je $i$ imaginarna enota, saj je $i^2 = -1$. Torej je $(-9)^{1/2} = 3i$.

V SageMath-u je imaginarna enota predstavljena z `I`.
::::

## Operacije s celimi števili
S simboli `//` in `%` dobimo (celoštevilski) kvocient oziroma ostanek dveh celih števil

$$ 20 = 6 \cdot 3 + 2$$


:::{code-cell} python
20 // 6 # celoštevilski kvocient
:::

:::{code-cell} python
20 % 6  # ostanek
:::

:::{code-cell} python
divmod(20,6) # vrne kvocient in ostanek hkrati kot tuple
:::

Izračunamo lahko tudi fakultete in binomske koeficiente:

$$3!=6$$

:::{code-cell} python
factorial(3)
:::



$$ \binom{4}{2} = \frac{4!}{(4-2)! 2!} = 6 $$

:::{code-cell} python
binomial(4,2)
:::


Število lahko faktoriziramo kot produkt praštevil:

:::{code-cell} python
factor(factorial(7))
:::

Lahko uporabimo naslednji način tudi


:::{code-cell} python
(factorial(7)).factor()
:::


Če želimo vedeti, ali je število praštevilo, lahko uporabimo ukaz `is_prime()`:

:::{code-cell} python
is_prime(29)
:::

:::{code-cell} python
is_prime(65537)
:::

Delitelje števila lahko dobimo z ukazom:

:::{code-cell} python
12.divisors()
:::

ali

:::{code-cell} python
divisors(12)
:::

Če samo želimo delitelje, ki so praštevila, uporabimo ukaz `prime_divisors()`:

:::{code-cell} python
120.prime_divisors()
:::

ali

:::{code-cell} python
120.prime_factors()
:::

Izračunamo lahko _največji skupni deliteljev_ in _najmanjši skupni večkratnik_ dveh celih števil z ukazoma `gcd()` in `lcm()`:

:::{code-cell} python
gcd(120,48)
:::

$$\operatorname{D}(120,48) = 24$$

:::{code-cell} python
lcm(9,15)
:::

$$\operatorname{v}(9,15) = 45$$


:::{exercise}
:label: ex-celaStevilaSageMath
Z uporabo SageMath-a rešite naslednje naloge, napišite rešitve v ločene celice besedila z uporabo LaTeX-a.

1. Poiščite ročno kvocient in ostanek pri deljenju $956$ z $98$. Potem pa uporabite SageMath, da preverite svoj rezultat.
2. Z uporabo SageMath ugotovite, ali 3 deli 234878.
3. Izračunajte seznam deliteljev za vsako od ccelih števil $134$, $491$, $422$, $1002$.
4. Katera od zgornjih števil so praštevila?
5. Izračunajte $\operatorname{D}(a, b)$ in $\operatorname{v}(a, b)$, in $ab$ za pare celih števil: $(2,5)$, $(4,10)$, $(18,51)$. Kakšen je odnos med temi tremi vrednostmi?
:::


::::{solution} ex-celaStevilaSageMath
:class: tip dropdown

1. Ročno deljenje $956$ z $98$ daje kvocient $9$ in ostanek $74$, saj je $956 = 98 \cdot 9 + 74$. 

:::{code-cell} python
divmod(956,98)
:::

2. Dovolj je če uporabimo operator `%` in preverimo, če je ostanek enak 0.

:::{code-cell} python
234878 % 3 == 0
:::

3. Seznam deliteljev za vsako od celih števil:

:::{code-cell} python
134.divisors()
:::

:::{code-cell} python
491.divisors()
:::

:::{code-cell} python
422.divisors()  
:::

:::{code-cell} python
1002.divisors()
:::

4. Edino praštevilo med zgornjimi je $491$.

:::{code-cell} python
is_prime(134), is_prime(491), is_prime(422), is_prime(1002)
:::

5. Izračunamo $\operatorname{D}(a, b)$, $\operatorname{v}(a, b)$ in $ab$ za dane pare celih števil:

:::{code-cell} python
pairs = [(2,5), (4,10), (18,51)]
results = []
for a, b in pairs:
    d = gcd(a, b)
    v = lcm(a, b)
    ab = a * b
    results.append((a, b, d, v, ab))
results 
:::

Opazimo, da za vsak par celih števil velja:
$$ ab = \operatorname{D}(a, b) \cdot \operatorname{v}(a, b) $$  
::::

:::{exercise}
:label: ex-fermat
Fermatovo število je število v obliki $2^{2^n} + 1$, kjer je $n$ naravno število. Imenovani so po francoskem matematiku Pierru de Fermatu, ki je leta 1604 domneval, da so vsa števila te oblike praštevila.

Z uporabo SageMath dokaz ali ovrzi Fermatovo domnevo.
:::



::::{solution} ex-fermat
:class: tip dropdown

Fermatova števila za majhne vrednosti $n$ so:

:::{code-cell} python
fermat_numbers = [2^(2^n) + 1 for n in range(10)]
fermat_numbers
:::

Lahko preverimo, ali so ta števila praštevila:

:::{code-cell} python
[is_prime(f) for f in fermat_numbers]
:::

::::


## Matematične konstante in funkcije

SageMath vključuje številne matematične konstante in funkcije, ki jih lahko uporabimo v svojih izračunih. Nekatere izmed najbolj znanih konstant so:

- $\pi$: `pi`
- $e$: `e`
- $\phi$ (zlati rez): `golden_ratio`
- $i$ (imaginarna enota): `I`

Pogoste funkcije so tudi uklučene, na primer:

- Trigonometrične funkcije: `sin()`, `cos()`, itd.
- Eksponentna funkcija: `exp()`
- Logaritemska funkcija: `log()`

:::{code-cell} python
sin(pi)
:::

:::{code-cell} python
cos(pi/4)
:::

Sage ima poseben ukaz `latex()` za prikaz matematičnih izrazov v LaTeX obliki. Na primer:

:::{code-cell} python
latex(cos(pi/4))
:::

Če želimo da izhod je predstavljen v LaTeX-u, uporabimo čarobni ukaz `%display latex`. Če želimo, da se izhod prikaže kot običajen besedilni izhod, uporabimo čarobni ukaz `%display text`.

Poglejmo še primere:

:::{code-cell} python
ln(e)
:::
 
V sage `log()` pomeni naraven lograritem, torej logaritem pri osnovni $e$:

:::{code-cell} python
log(e) == ln(e)
:::

Če želimo logaritem pri drugi osnovi, na primer $10$, uporabimo drugi argument:

:::{code-cell} python
log(1000, 10)
::: 

Nekateri viri namesto $e$ raje pišejo $\exp$ in SageMath meni, da je to v redu.

:::{code-cell} python
exp(3) - e^3
:::


V SageMath lahko delamo tudi z kompleksnimi števili. Imaginarno število $i$ je označeno z `i` in z `I`. Ker pa se `i` pogosto uporablja pri programiranju, je dobra praksa, da se označi z `I`.

:::{code-cell} python
arg(1+I)
:::

:::{code-cell} python
latex(1+i)
:::

Ukaza `max()` in `min()` vrneta največje in najmanjše število v seznamu števil.

:::{code-cell} python
max([1,2,3])
:::

Seznam lahko damo z oklepaji `[` `]` ali brez njih.

:::{code-cell} python
min(1,2,3)
::: 

Z ukazom `floor()` dobimo največje celo število, ki ni večje od danega števila, z ukazom `ceil()` pa najmanjše celo število, ki ni manjše od danega števila.

:::{code-cell} python
floor(2.1)
:::

:::{code-cell} python
ceil(2.1)
:::

*Pazite*: 

:::{code-cell} python
floor(1/(2.1-2))
:::

Ampak 

$$
\left\lfloor \frac{1}{2.1-2} \right\rfloor = \left\lfloor \frac{1}{0.1} \right\rfloor = 10
$$

Kaj se je zgodilo? 

Računalniki shranjujejo realna števila v binarni obliki, mi pa smo navajeni uporabljati desetiško predstavitev. Število $2.1$ v desetiškem zapisu je precej preprosto in kratko, vendar je po pretvorbi v binarni zapis $10.0\overline{0011} = 10.0001100110011 \dots$

Ker računalniki ne morejo shraniti neskončnega števila številk, se to število nekje zaokroži, kar povzroči manjšo napako, ki smo jo videli.
V SageMathu pa so racionalna števila (ulomki) natančna, zato te napake pri zaokroževanju nikoli ne bomo videli.

:::{code-cell} python
floor(1/ ( (21/10) - 2) )
:::

:::{exercise}
:label: ex-matemKonstSageMath

1. Izračunajte celi del (oz. najbližje celo število) za število $e^{\pi}$.
2. Izračunajte logaritma z osnovo $e$ števila $1/1000000$, izračunajte logaritma z osnovo $10$ števila $1/1000000$, nato izračunajte razmerje. Kakšen naj bo odgovor?
3. Izračunajte logaritma z osnovo 2 števila 64.
4. Primerjaj $e^{i \pi}$ z njegovim numeričnim približkom z uporabo `pi.n()`.
5. Izračunajte $\sin(\pi/2)$, $\cot(0)$ in $\csc(\pi/16)$.

Rešitve napišite v ločeno celico besedila z uporabo LaTeXa.
:::


::::{solution} ex-matemKonstSageMath
:class: tip dropdown

1. Celi del števila $e^{\pi}$ je:
:::{code-cell} python
floor(e^pi)
:::

---

2. Logaritma z osnovo $e$ in $10$ števila $1/1000000$ ter njuno razmerje:
:::{code-cell} python
log(1/1000000)
:::

logaritma z osnovo $10$:
:::{code-cell} python
log(1/1000000, 10)
:::

Razmerje:

$$
\ln\left(\frac{1}{1000000}\right) \bigg/ \log_{10}\left(\frac{1}{1000000}\right) = \ln(10)
$$

---

3. Logaritem z osnovo 2 števila 64 je:
:::{code-cell} python
log(64, 2)  
:::

---

4. Primerjava $e^{i \pi}$ z njegovim numeričnim približkom:


:::{code-cell} python
e^(I * pi.n())
:::

:::{code-cell} python
e^(I * pi)
:::

$$e^{i \pi} = -1$$
velja in je znana kot Eulerjeva identiteta. Numerični približek je zelo blizu $-1$, vendar ni natančno enak zaradi omejene natančnosti numeričnih izračunov.

::::

## Pripisovanje, enakost, enačbe in neenačbe.

SageMath uporablja simbol `=` za **pripisovanje vrednosti spremenljivkam**. 

:::{code-cell} python
a = 5
a 
:::

Za primerjavo uporablja `==`, `!=`, `<`, `>`, `<=`, `>=`.

:::{code-cell} python
2==2
:::

:::{code-cell} python
2!=2
:::

:::{code-cell} python
2 < 2
:::

:::{code-cell} python
a <= 5
:::

Seveda, lahko uporabimo `=` za shraniti rezultat izračuna v spremenljivko:

:::{code-cell} python 
b = 2 + 3 * 4
b
:::

:::{warning}
**Pazite**: `=` ni enako kot `==`. Prvi je za pripisovanje, drugi pa za primerjavo. Pogosta napaka je uporaba izraza `a = b` za primerjavo `a` in `b`, kar v resnici pomeni, da se vrednost `b` pripiše `a`.
:::

Rezultat izračuna se ne natisne samodejno, ko je pripisan spremenljivki. Če želite videti vrednost spremenljivke, jo morate izrecno navesti v celici ali uporabiti ukaz `print()`. Poglejte primeri:

:::{code-cell} python
y = 1 + 2; print(y)
y = 3 * y + 1; print(y)
y = 3 * y + 1; print(y)
y = 3 * y + 1; print(y)
:::

Znak `;` je uporabno za ločevanje več ukazov v eni celici.

Načeloma nam nič ne preprečuje, da bi ponovno definirali obstoječe spremenljivke.

:::{code-cell} python
pi=-I/2
:::

:::{code-cell} python
exp(2*pi*I)
:::

Z ukazom `restore()` lahko obnovimo privzeto vrednost spremenljivke.

:::{code-cell} python
restore()
:::

:::{code-cell} python
y+pi
:::

Ukaz `reset()` pa ponastavi celoten delovni prostor in izbriše vse spremenljivke.

:::{code-cell} python
reset()
::: 

:::{code-cell} python
:tags: [raises-exception]
y
:::

Opazite tudi, da SageMath včasih razlikuje med simbolnimi izračuni in števili:

:::{code-cell} python
e^(2*pi*I)
:::

:::{code-cell} python
e^(2*pi*I) == 1
:::

SageMath zgornjega izraza ne razume ko primerjavo, temveč kot enačbo. V tem primeru, ne moremo jo rešiti, ampak lahko preverimo, ali je enačba resnična z uporabo ukaza `bool()`:

:::{code-cell} python
bool(e^(2*pi*I) == 1)
::: 

Enačbe in neenakosti lahko rešujemo z ukazoma `solve()`:

:::{code-cell} python
solve(3*x - 2 == 5,x)
:::

Črka `x` v SageMath-u predstavlja simbolično spremenljivko in lahko jo uporabimo v enačbah in izrazih:

:::{code-cell} python
solve( 2*x - 5 >= 17,x)
:::

:::{code-cell} python
solve( x^2 + x == 6, x)
:::

:::{code-cell} python
solve(2*x^2 - x + 1 == 0, x)
:::

Ukaz `solve()` poskuša rešiti enačbe brez numeričnih približkov, če je le mogoče. Ko tega ni možno, bo vrnil rešitev v simbolni obliki.

:::{code-cell} python
solve(sin(x)==x,x)
:::

Za iskanje numeričnega približka rešitev lahko uporabimo ukaz `find_root()`; ta ukaz zahteva začetni interval, v katerem iščemo rešitev.

:::{code-cell} python
find_root(sin(x) == x, -pi/2 , pi/2)
:::

Ob začetku seje SageMath eno simbolno spremenljivko, in sicer `x`, ki se lahko uporablja v enačbah in izrazih. Če želimo uporabiti druge spremenljivke, jih moramo najprej definirati z ukazom `var()`:

:::{code-cell} python
y = var("y")
:::

Lahko pa definiramo več spremenljivk hkrati:

:::{code-cell} python
phi, theta, rho = var("phi theta rho")
:::



Imena spremenljivk lahko vsebujejo črke, številke in podčrtaje, vendar se ne smejo začeti s številko in presledkov ne smejo vsebovati. Npr. `x_1`, `var123`, in `my_variable` so veljavna imena spremenljivk, medtem ko `1var`, `my variable`, in `var-2` niso veljavna imena spremenljivk.

:::{code-cell} python
x1, x2 = var("x1 x2")
:::

Poskus uporabe neveljavnega imena spremenljivke bo povzročil napako `NameError`:

:::{code-cell} python
:tags: [raises-exception]
u
:::

Simbolno spremenljivko lahko izbrišemo s ukazom `restore()`:

:::{code-cell} python
restore('phi')
:::

:::{code-cell} python
:tags: [raises-exception]
phi
:::

Majhne sisteme linearnih enačb lahko rešimo z ukazom `solve()`, dokler so spremenljivke definirane.

:::{code-cell} python
x, y, z = var("x y z")
:::

:::{code-cell} python
solve( [3*x - y == 2,-2*x -y == 1 ], x,y)
:::

:::{code-cell} python
solve( [ 2*x - y == -1 , 2*x - y == 2],x,y)
:::

:::{code-cell} python
solve( [ 2*x + y == -1 ,-4*x - 2*y == 2],x,y)
:::

Vrednost `r1` označuje, da obstaja prosta spremenljivka, ki določa množico rešitev.
Če je več prostih spremenljivk, bo rezultat vseboval več parametrov `r1`, `r2`, itd.

:::{code-cell} python
solve([ 2*x + 3*y + 5*z == 1, 4*x + 6*y + 10*z == 2, 6*x + 9*y + 15*z == 3], x,y,z)
:::

Ukaz `solve()` je lahko pri velikih enačb zelo počasen. V takih primerih je bolje uporabiti matrike (poglej [](./13_sageAlgebra.md))

Reševanje neenakosti z več spremenljivkami je možno, ampak lahko rezultati postanejo zelo zapleteni in težko berljivi. 

:::{code-cell} python
solve([ x-y >=2, x+y <=3], x,y)
:::

:::{exercise}
:label: ex-enacbe
1. Poiščite vse rešitve enačbe $x^{3} - x = 7x^{2}-7$
2. Poišči celotno množico rešitev za neenačbo $|t-7| \geq 3$
3. Poiščite vsa $x$ in $y$, ki izpolnjujejo tako $2𝑥+ 𝑦= 17$ kot $𝑥-3𝑦=-16$.
4. S funkcijo `find_root()` poiščite rešitev enačbe $e^{x} = \cos(𝑥)$ na intervalu $[-\pi/2,0]$.
5. Zgornji ukaz spremenite tako, da `find_root()` najde drugo rešitev na istem intervalu.
:::



::::{solution} ex-enacbe
:class: tip dropdown
1. Rešitve enačbe $x^{3} - x = 7x^{2}-7$ so $x = 7$, $x = -1$ in $x = 1$:

:::{code-cell} python
solve( x^3 - x == 7*x^2 - 7, x) 
:::

2. Celotna množica rešitev za neenačbo $|t-7| \geq 3$ je $(-\infty, 4] \cup [10, \infty)$:

:::{code-cell} python
t=var("t")
solve( abs(t - 7) >= 3, t)  
:::

3. Edina rešitev za sistem enačb $2x+ y= 17$ in $x-3y=-16$ je $x = 5$ in $y = 7$:

:::{code-cell} python
x, y = var("x y")
solve( [2*x + y == 17, x - 3*y == -16], x, y)   
:::

4. Ena rešitev enačbe $e^{x} = \cos(x)$ na intervalu $[-\pi/2,0]$ je seveda $x=0$,
ker je $e^{0} = \cos(0) = 1$:

:::{code-cell} python
find_root( exp(x) == cos(x), -pi/2 , 0) 
:::

5. Druga rešitev enačbe $e^{x} = \cos(x)$ na intervalu $[-\pi/2,0]$ je približno $-1.2926957193733983$, kar lahko najdemo z uporabo `find_root()` z drugačnim začetnim intervalom:

:::{code-cell} python
find_root( exp(x) == cos(x), -pi/2 , -0.1) 
:::



::::