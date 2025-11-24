---
kernelspec:
  name: python
  display_name: Python 3
---

(08_geogebraDinGeometrija)=
# Dinamična geometrija z GeoGebro

:::{code-cell} python
:tags: remove-input
import IPython.display as display
from IPython.display import IFrame
:::

V poglavju [](./07_geogebraUvod.md) smo spoznali osnove dela z GeoGebro. V tem poglavju bomo raziskali, kako ustvariti animacije in dinamične konstrukcije z uporabo GeoGebre.

## Točka na objektu

Najlažje način za ustvarjanje dinamične konstrukcije je uporaba točke, ki je vezana na drug objekt. Točko lahko postavimo na premico, krožnico ali katerikoli drug objekt, kar omogoča, da se točka premika znotraj omejitve tega objekta.

:::{exercise}
:label: ex-paralelogram

1. Ustvarite točki $A$ in $B$ in premico $f$ skozi ti dve točki.
2. Ustvarite premico $g$, ki je vzporedna premici $a$. Lahko uporabite pomožno točko $P$, ki jo bomo skriti.
3. Ustvarite točko $C$ na premici $g$. Za to uporabite orodje <img src="./geogebra/images/32px-Mode_pointonobject.svg.png" class="inline" width="22px"> *Point on Object* (*Točka na objektu*) oziroma ukaz `Point(g)`.
4. Ustvarite vektor $v=\overrightarrow{AB}$, za to lahko uporabite orodje <img src="./geogebra/images/32px-Mode_Vector.svg.png" class="inline" width="22px"> *Vector* (*Vektor*) oziroma ukaz `v=Vector(A, B)` ali ukaz `v=A-B`. Opazite razlika med tema dvema ukazoma: prvi ustvari vektor, ki gre iz točke $A$ do točke $B$, drugi pa ustvari vektor z izhodiščem v koordinatnem izhodišču; v tem primeru je to nepomembno, saj bomo vektor uporabili le za premikanje točke.
5. Uporabi orodje <img src="./geogebra/images/32px-Mode_TranslatebyVector.svg.png" class="inline" width="22px"> *Translate by Vector* (*Premakni z vektorjem*) oziroma ukaz `D=Translate(C, v)`, da ustvarite točko $D$, ki je slika točke $C$ ob premiku za vektor $v$.
6. Ustvarite štirikotnik $ABDC$ z orodjem <img src="./geogebra/images/32px-Mode_Polygon.svg.png" class="inline" width="22px"> *Polygon* (*Poligon*) oziroma ukaz `Polygon(A, B, D, C)`.
7. Z uporabo *vrstice za zamenjavo sloga* in sicer gumba <img src="./geogebra/images/32px-Mode_showhidelabel.svg.png" class="inline" width="22px"> *Show/Hide Label* (*Prikaži/skrij oznako*), prikazi površine štirikotnika (izberite možnost *Value* (*Vrednost*)).
8. Poiščite točko $C$ v algebrsko okno, upoštevajte, da ima gumb <img src="./geogebra/images/18px-Nav_play_circle.svg.png" class="inline" width="16px"> *Play*, jo kliknite in opazujte, kako se spreminja površina štirikotnika $ABDC$. Kaj opazite? lahko to dokažite?
:::

```{margin}
[Seznam vaj](#08_geogebraDinGeometrija_vaje)
```

::::{solution} ex-paralelogram
:class: tip dropdown
Spodaj lahko vidite rešitev v GeoGebri. 

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/jsje5fbj/width/800/height/571/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/true/ctl/false", width="570", height=413, allowfullscreen=True)
:::

Lahko tudi jo [odprite v GeoGebri](https://www.geogebra.org/classic/jsje5fbj).
::::

Ko ustvarimo točko na krivulji (kot so premice, krožnice, graf funkcij itd.), lahko to točko animiramo. To naredimo tako, da izberemo točko in kliknemo na gumb <img src="./geogebra/images/18px-Nav_play_circle.svg.png" class="inline" width="16px"> *Play* v algebrskem oknu ali uporabimo ukaz `StartAnimation(<točka>)`. S tem se bo točka začela premikati po objektu, na katerem je bila ustvarjena.

Na žalost GeoGebra ne omogoča animacije točk na daljših objektih, kot so mnogokotniki. Vendar pa lahko ustvarimo drsnike, ki nam omogočajo nadzor nad položajem točke na takšnih objektih s pomočjo parametra.

## Drsniki

V resnični, drsniki so samo orodja za spreminjanje vrednosti spremenljivk. Vendar pa so zelo uporabni pri ustvarjanju dinamičnih konstrukcij, saj nam omogočajo, da spreminjamo vrednosti in opazujemo, kako se konstrukcija spreminja.

Drsniki imajo tri glavne lastnosti: `Min` (minimalna vrednost), `Max` (maksimalna vrednost) in `Increment` (prirastek). Te lastnosti določajo obseg vrednosti, ki jih drsnik lahko zavzame, in kako hitro se vrednost spreminja, ko premikamo drsnik. 

Za ustvarjanje drsnika lahko uporabimo orodje <img src="./geogebra/images/32px-Mode_Slider.svg.png" class="inline" width="22px"> *Slider* (*Drsnik*) in dobimo okno za nastavitev lastnosti drsnika. Drsnike lahko ustvarimo tudi z vnosom imena spremenljivke v vnosno vrstico, na primer `a=5`, kar ustvari spremenljivk z imenom `a` in začetno vrednostjo $5$. Nato lahko kliknemo na tri pike poleg imena spremenljivke v algebrskem oknu in nato *Create slider* (*Ustvari drsnik*). To ustvari drsnik z privzetimi lastnostmi (`Min=-5`, `Max=5`, `Increment=0.1`), ki jih lahko spremenimo z dvojnim klikom na drsnik (v grafičnem pogledu) ali z desnim klikom na ime spremenljivke v algebrskem oknu in izbiro *Settings* (*Nastavitve*). V oknu z nastavitvami lahko spremenimo lastnosti drsnika, kot so `Min`, `Max` in `Increment`, in tudi druge lastnosti, kot so barva, slog in vidnost.

:::{exercise} 
:label: ex-drsniki-1
1. Ustvarite novo datoteko na GeoGebri v prikaznem načinu *Geometry* (*Geometrija*). Odprite algebrske okno v meniju *View* (*Pogled*) in izberite *Algebra* (*Algebra*).
2. S uporabo *vrstice za zamenajavo sloga* skrijte prikaz osi v grafičnem pogledu.
3. Ustvarite drznika `m` in `b` z uporabo orodja <img src="./geogebra/images/32px-Mode_Slider.svg.png" class="inline" width="22px"> *Slider* (*Drsnik*) ali z vnosom `m` in `b` v vnosno vrstico. Nastavite drsnika tako, da imata naslednje lastnosti:
   - Drsnik `m`: `Min=-20`, `Max=20`, `Increment=0.5`
   - Drsnik `b`: `Min=-5`, `Max=5`, `Increment=0.1`
4. Ustvarite premico z enačbo `y=m*x+b` v vnosni vrstici.
5. Z orodjem <img src="./geogebra/images/32px-Mode_slope.svg.png" class="inline" width="22px"> *Slope* (*Naklon*) oziroma ukazom `Slope(<premica>)` izračunajte naklon premice in ga prikažite v grafičnem pogledu.
6. Ustvarite segment med izhodiščem in točko presečišča premice z osjo $y$ z ukazom ukaz `Segment((0, 0), Intersect(<premica>, yAxis))` 
7. Pobarvate daljico in drsnik $b$ z isti barvi, ter drsnik $m$ in naklon z drugo barvo.
8. Možno je, da naklon ima različen ime (npr $a$) od drsnika $m$. V tem primeru uredite naslov (caption) naklona tako, da se ujema z imenom drsnika $m$. Izberite tudi možnost *Caption in value* (*Naslov in vrednost*) za oznake, da se prikaže vrednost naklona.
9. Ponovite korak 8 za drsnik $b$ in segment.
10. Premikajte drsnika in opazujte, kako se spreminja premica, njen naklon in točka presečišča z osjo $y$.
::: 



```{margin}
[Seznam vaj](#08_geogebraDinGeometrija_vaje)
```

::::{solution} ex-drsniki-1
:class: tip dropdown
Spodaj lahko vidite rešitev v GeoGebri.

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/a8bv9bss/width/1140/height/690/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/true/ctl/false", width="570", height=345, allowfullscreen=True)
:::

Lahko tudi jo [odprite v GeoGebri](https://www.geogebra.org/classic/a8bv9bss).

::::

:::{exercise}
:label: ex-drsniki-2

**Trikotnik neenakosti**

Klasični rezultat v geometriji pravi, da obstaja trikotnik s stranicami dolžin $a$, $b$ in $c$ natanko tedaj, ko so izpolnjene neenakosti:  
\begin{align*}
a + b &> c \\
a + c &> b \\
b + c &> a
\end{align*}

Sgornje neenakosti so znanje kot *trikotne neenakosti*. V tej vaji bomo ustvarili dinamično konstrukcijo, ki bo prikazala, kdaj je mogoče sestaviti trikotnik s pomočjo drsnikov za dolžine stranic.


1. Ustvarite novo datoteko na GeoGebri v prikaznem načinu *Geometry* (*Geometrija*). Odprite algebrske okno v meniju *View* (*Pogled*) in izberite *Algebra* (*Algebra*).
2. Ustvarite tri drsnike `a`, `b` in `c` z uporabo orodja <img src="./geogebra/images/32px-Mode_Slider.svg.png" class="inline" width="22px"> *Slider* (*Drsnik*) ali z vnosom `a`, `b` in `c` v vnosno vrstico. Nastavite drsnike tako, da imajo naslednje lastnosti:
   - Drsnik `a`: `Min=1`, `Max=10`, `Increment=0.1`
   - Drsnik `b`: `Min=1`, `Max=10`, `Increment=0.1`
   - Drsnik `c`: `Min=1`, `Max=10`, `Increment=0.1`
3. Ustvarite točko $A$, ter ustvarite daljico $AB$ dolžine $c$ z orodjem <img src="./geogebra/images/24px-Mode_segmentfixed.svg.png" class="inline" width="22px"> *Segment with given length* (*Daljica z določeno dolžino*) oziroma ukazom `Segment(A, c)`.
4. Ustvarite krožnico s središčem v točki $A$ in polmerom $b$ z orodjem <img src="./geogebra/images/32px-Mode_circlepointradius.svg.png" class="inline" width="22px"> *Circle with Center and Radius* (*Krožnica s središčem in polmerom*) oziroma ukazom `Circle(A, b)`.
5. Ustvarite krožnico s središčem v točki $B$ in polmerom $a$ z orodjem <img src="./geogebra/images/32px-Mode_circlepointradius.svg.png" class="inline" width="22px"> *Circle with Center and Radius* (*Krožnica s središčem in polmerom*) oziroma ukazom `Circle(B, a)`.
6. Ustvarite točko $C$ kot presečišče obeh krožnic z orodjem <img src="./geogebra/images/32px-Mode_Intersect.svg.png" class="inline" width="22px"> *Intersect* (*Presečišče*) oziroma ukazom `Intersect(<krožnica1>, <krožnica2>)`.
7. Ustvarite trikotnik $ABC$ z orodjem <img src="./geogebra/images/32px-Mode_Polygon.svg.png" class="inline" width="22px"> *Polygon* (*Mnogokotnik*) oziroma ukazom `Polygon(A, B, C)`.
---

Geogebra nam omogoča, da uporabimo dinamične barve. Barvo lahko določimo z uporabo funkcije `If()`, ki deluje tako, da preveri pogoj in vrne eno vrednost, če je pogoj resničen, in drugo vrednost, če je pogoj neresničen. V našem primeru bomo uporabili funkcijo `If()` za določitev barv drsnikov glede na to, ali velja trikotna neenakost.

8. Izberite dve barvi za prikaz veljavnosti trikotne neenakosti, na primer zeleno za veljavno in rdečo za neveljavno. Potrebujete RGB kodo barv, za to, lahko uporabite spletno orodje, kot je [HTML Color Picker](https://www.w3schools.com/colors/colors_picker.asp). V našem primeru bomo uporabili zeleno z RGB kodo `(0, 153, 51)` in rdečo z RGB kodo `(204, 0, 0)`.
9. Nastavite barvo drsnika `a` z uporabo funkcije `If()`, kot sledi:
   - Desni klik na drsnik `a` v algebrskem oknu in izberite *Settings* (*Nastavitve*).
   - Pojdite na zavihek {kbd}`Advanced`.
   - V polje `Red` pod `Dynamic Colours` vnesite naslednji izraz: `If(a<b+c, 0, 204/255)`. Ta izraz določa rdečo komponento barve glede na veljavnost prve trikotne neenakosti `a < b + c` v pogojni funkciji `If()`: $0$ (rdeča komponenta izbrane zelene barve) če velja, $204/255$ (rdeča komponenta izbrane rdeče barve) če ne velja. Vrednost mora biti med $0$ in $1$, zato delimo z $255$.
    - V polje `Green` vnesite naslednji izraz: `If(a< b + c, 153/255, 0)`. 
    - V polje `Blue` vnesite naslednji izraz: `If(a < b + c, 51 / 255, 0)`.
10. Ponovite korak 9 za drsnika `b` in `c`, pri čemer prilagodite pogoj v funkciji `If()` za vsako neenakost:
    - Za drsnik `b`: `If(b < a + c, ...)`
    - Za drsnik `c`: `If(c < a + b, ...)`
11. Premikajte drsnike in opazujte, kako se spreminjajo barve drsnikov. Ko so vse trikotne neenakosti izpolnjene, bodo vsi drsniki zeleni, kar pomeni, da je mogoče sestaviti trikotnik s danimi dolžinami stranic. Če katera od neenakosti ni izpolnjena, bo ustrezni drsnik rdeč, kar pomeni, da trikotnik ni mogoče sestaviti.
 

::: 


```{margin}
[Seznam vaj](_vaje)
```

::::{solution} ex-drsniki-2
:class: tip dropdown

Spodaj lahko vidite rešitev v GeoGebri.

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/ajje5wsn/width/1140/height/500/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/false/ctl/false", width="570", height="250px", allowfullscreen=True)
:::

Lahko tudi jo [odprite v GeoGebri](https://www.geogebra.org/classic/ajje5wsn).

::::





(08_geogebraDinGeometrija_vaje)=
## Vaje

- [Vaje %s](#ex-paralelogram) - Ustvarite dinamični paralelogram in opazujte, kako se spreminja njegova površina.
- [Vaje %s](#ex-drsniki-1) - Ustvarite premico z drsniki za naklon in presečišče z osjo y ter opazujte, kako se spreminja premica.
- [Vaje %s](#ex-drsniki-2) - Ustvarite dinamično konstrukcijo, ki prikazuje veljavnost trikotne neenakosti s pomočjo drsnikov in dinamičnih barv.

## Dodatne vaje


