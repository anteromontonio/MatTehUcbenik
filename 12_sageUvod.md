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

:::{code-cell} sage
1+1
:::

:::{code-cell} sage
( 1 + 2 * (3 + 5) ) * 2
:::

Simbol * pomeni množenje, ki se ne sme izpustiti, tudi v izrazih, kot je $2x$: `2*x`. Za združevanje simbolov uporabljamo oklepaj `(` `)` nikoli `[` `]` ali `{` `}`.