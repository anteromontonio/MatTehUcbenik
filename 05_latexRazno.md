(05_latexRazno)=

# LaTeX: Razno

V tej poglavju so zbrani različni nasveti in triki za delo z LaTeX-om, ki ne sodijo v druge poglavja.

## Obsežnejši projekti

Za obsežnejše projekte, kot so diplomske naloge, je priporočljivo razdeliti dokument na več datotek in jih vključiti v glavno datoteko z ukazom `\input{}` ali `\include{}`.
To omogoča lažje upravljanje in urejanje posameznih delov dokumenta.

Ukaz `\include{<pot do datoteke>}` vključi vsebino navedene datoteke in samodejno začne novo stran pred in po vključitvi.

Ukaz `\includeonly{<ime_datoteke1>, <ime_datoteke2>, ...}` omogoča vključitev samo določenih datotek med kompilacijo, kar je uporabno za hitrejše pregledovanje določenih delov dokumenta.

:::{admonition} Pazite!
:class: warning

- Ukaz `\include{<ime_datoteke>}` lahko uporabljamo samo v **telesu glavne datoteke** ne znotraj drugih vklučenih datotek.
- Ukaz `\includeonly{<ime_datoteke1>, <ime_datoteke2>, ...}` mora biti postavljen v preambulo glavne datoteke.
  V telesu dokumenta morajo biti
  ukaze `\include{}` za vse datoteke, ki jih želimo vključiti.
- Ukaz `\include{}` vedno začne novo stran, zato ni primeren za vključevanje manjših delov besedila. Poleg tega, ta ukaz ne deluje znotraj okolij, kot so `\begin{figure}...\end{figure}` ali `\begin{table}...\end{table}`.
  :::

Ukaz `\include` je malo omejevalen in ima posebno uporabo: vključiti več poglavje (`chapter`) v velik projekt. Ta ukaz vedno začne novo stran, to je koristno ko uporabljamo ukaz `\indludeonly{}`, ker se prelomi strani ne bodo premaknili, če bomo vključili samo določene datoteke.

Včasih je bolj smiselno uporabiti ukaz `\input{<pot do datoteke>}`, ki vključi vsebino navedene datoteke brez preloma strani.
Ukaz `\input{}` lahko uporabljamo kjerkoli v dokumentu, tudi znotraj okolij, kot so `\begin{figure}...\end{figure}` ali `\begin{table}...\end{table}`.

Ukaz `\input{}` lahko uporabimo tudi za vključitev datotek z ukazi LaTeX-a, kot so definicije makrov ali nastavitve paketov. Pogosta uporaba je vključitev datoteke, recimo, `preambula.tex`, ki vsebuje vse nastavitve in pakete, ki jih želimo uporabiti v našem dokumentu.

:::{admonition} Pazite!
:class: warning
Čeprav lahko uporabimo ukaz `\input` za naložitev paketov v našo datoteko, mora vrstica, ki vsebuje ukaz `\documentclass`, **vedno** biti v glavni datoteki, pred vsemi ukazi `\input`.

:::

:::{exercise}
:label: ex_input_include

1. Napišite glavno datoteko `glavno.tex` s standardno preambulo in okoljem `document`.
   Uporabite razred `book` ali razred `report` namesto `article`.
2. Ustvarite dve datoteki, `poglavje1.tex` in `poglavje2.tex`, ki vsebujeta besedilo za dva poglavja. Lahko uporabite paket `lipsum` za generiranje naključnega besedila.
3. Vključite ti dve datoteki v glavno datoteko z uporabo ukaza `\include{}`.
4. Shranite vse datoteke in kompilirajte glavno datoteko `glavno.tex`.
5. S uporabo ukaza `\includeonly` v preambuli, vključujete samo datoteko `poglavje2.tex`.
6. Nato spremenite glavno datoteko, da uporabite razred `article`. Spremenite tudi vse `\chapter{}` ukaze v `\section{}` ukaze v obeh vključenih datotekah. Shranite.
7. Spremenite ukaz `\input{}` za vključitev obeh datotek namesto `\include{}`, komentirate ukaz `\includeonly{}` in ponovno shranite glavno datoteko.
8. Ustvarite datoteko `preambula.tex`, ki vsebuje vse pakete in nastavitve, ki jih želite uporabiti v glavnem dokumentu. Vključite to datoteko v glavno datoteko z uporabo ukaza `\input{preambula.tex}`.
   :::

```{margin}
[Seznam vaj](#05_latexRazno_vaje)
```

:::{solution} ex_input_include
:class: tip, dropdown
Na koncu datoteke `glavno.tex` bi moral izgledati nekako takole:

````latex
\documentclass{article}
\input{preambula.tex}
%Vsebina preambula.tex:
% \usepackage[slovene]{babel}
% \usepackage{lipsum}
% \usepackage{mathtools, amssymb, amsthm}
% \usepackage{graphicx, caption, subcaption}
% \usepackage{array, booktabs}


\begin{document}
\include{poglavje1}
% \input{poglavje1}
%Vsebina razdelek1.tex:
% \section{Prvi}
% \lipsum[1-3]
\include{poglavje2}
% \input{poglavje2}
%Vsebina poglavje2.tex:
% \section{Drugi}
% \lipsum[4-6]
\end{document}

:::


## Barve

Za uporabo barv v LaTeX dokumentih uporabimo paket `xcolor`. Paket omogoča uporabo treh ukazov za barvanje besedila ali ozadij:

- `\textcolor[<model>]{<barva>}{<besedilo>}`: Barva besedilo z določeno barvo.
- `\color[<model>]{<barva>}`: Spremeni barvo besedila od tega mesta naprej. To je različica _switch_ ukaza `\textcolor`, kot je ukaz `\bfseries` za krepko pisavo (prim. `\textbf{}`).
- `\mathcolor[<model>]{<barva>}{<matematični_izraz>}`: Barva matematični izraz z določeno barvo. Ne pozabite, da ukaze za _navadno_ besedilo običajno ne delujejo v matematičnem načinu.

Za zdaj se ne skrbite za neobvezni parameter `<model>`. Ta parameter nadzira, kaj se pričakuje za argument `<barva>`. Če ni določen, se privzeto uporablja model `named`, ki omogoča uporabo vnaprej določenih imen barv, to pomeni, barve pokličemo z imeni.


::::{grid} 2 2 2 2


:::{card} LaTeX

```latex
%V preambuli
\usepackage{xcolor}
%V telesu dokumenta
\color{red} Svet je zdaj rdeč,
nekateri deli so
\textcolor{yellow}{rumeni}.
\[
\mathcolor{blue}{\sum_{k=0}}^{10} i
\]
Vse še vedno rdeča
\color{blue}
zdaj modra.
````

:::

:::{card} PDF

```{figure} ./img/05_eg-barve-1.png
:name: fig:eg-barve-1
```

:::
::::

Barve, ki so vnaprej določene v paketu `xcolor`, so prikazane v{numref}`Tabeli {number}<tbl:basecolors>`.

```{figure} ./img/05_xcolorList.png
:name: tbl:basecolors
:height: 400px
Osnovne barve, ki jih določa paket `xcolor`.
```

Seznam določenih barv lahko razširimo z uporabo možnosti, ki jih ponuja paket `xcolor`. Npr z možnostjo `dvipsnames` lahko uporabimo dodatne barve prikazane v {numref}`Tabeli {number}<tbl:dvipsnames>`.

```{figure} ./img/05_xcolorDvipsnames.png
:name: tbl:dvipsnames
:height: 350px
Dodatne barve, ki jih določa paket `xcolor` z možnostjo `dvipsnames`.
```

Druge možnosti so `svgnames`, `x11names`. Možnost `svgnames` določa 151 barv, ki so definirane v SVG standardu, medtem ko možnost `x11names` določa 317 barv, ki so bile prvotno definirane za X11 Window System. Celoten seznam barv je na voljo v dokumentaciji paketa [`xcolor`](https://ctan.org/pkg/xcolor?lang=en).

Drugi način pridobivanja novih barv je z mešanjem dveh ali več barv. Sintaksa za mešanje dveh barv je naslednja:

```latex
<barva1>!<odstotno>!<barva2>
```

Rezultat je barva, ki je sestavljena iz `<odstotno>` odstotkov `<barva1>` in `(100 - <odstotno>)` odstotkov `<barva2>`. Na primer, `red!40!blue` ustvari vijolično barvo, ki je mešanica 40% rdeče in 60% modre.

Mešanje lahko vključuje tudi več kot dve barvi. V tem primeru, mešanje je izvedeno zaporedno. Na primer, `red!50!green!30!blue` najprej zmeša 50% rdeče in 50% zelene, nato pa rezultat zmeša z 70% modre in 30% prej dobljene barve.

:::{exercise}
:label: ex-gradient
Z uporabo ukaza za mešanje barv, reproducirajte barvni gradient prikazan na spodnji sliki:

```{figure} ./img/05_ex-gradient.png
:name: fig:ex-gradient
:height: 100px
```

:::

```{margin}
[Seznam vaj](#05_latexRazno_vaje)
```

:::{solution} ex-gradient
:class: tip, dropdown
Ena izmed možnih rešitev je naslednja:

```latex
\textcolor{white!80!blue}{S}
\textcolor{white!60!blue}{l}
\textcolor{white!40!blue}{o}
\textcolor{white!20!blue}{v}
\textcolor{blue}{e}
\textcolor{blue!75!red}{n}
\textcolor{blue!50!red}{i}
\textcolor{blue!25!red}{j}
\textcolor{red}{a}
```

:::

Včasih moramo biti natančnejši pri barvah, ki jih uporabljamo. Za to lahko uporabimo izbirni argument `model`. Najlažje ga razumemo prek modela `Gray`. V tem modelu določimo odtenek sive barve z vrednostjo med `0` in `15`, kjer `0` predstavlja črno in `15` belo.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\textcolor[Gray]{0}{Nula} \\
\textcolor[Gray]{3}{Tri} \\
\textcolor[Gray]{7}{Sedem} \\
\textcolor[Gray]{11}{Enaist} \\
\textcolor[Gray]{15}{Petnaist}
```

:::

:::{card} PDF

```{figure} ./img/05_eg-Gray-model.png
:name: fig:eg-Gray-model
:width: 100px
```

:::
::::

Podobno lahko uporabimo model `grey`, kjer vrednosti segajo od `0` do `1`, pri čemer `0` predstavlja črno in `1` belo.

V Tabeli {numref}`{number}<tbl:color-models>` so prikazani nekateri barvni modeli, ki jih podpira paket `xcolor`.

:::{list-table} Najpogostejši modeli barv v paketu `xcolor`
:name: tbl:color-models
:header-rows: 1

* - Model
  - Osnovne barve/komponente
  - Razpon parametrov
  - Primer
* - `rgb`
  - Rdeča, zelena, modra
  - $[0,1]^3$
  - `\textcolor[rgb]{1,0,0}{Rdeča}`
* - `RGB`
  - Rdeča, zelena, modra
  - $\{0, \dots, 255\}^3$
  - `\textcolor[RGB]{255,0,0}{Rdeča}`
* - `HTML`
  - Rdeča, zelena, modra
  - Šestnajstiški zapis
  - `\textcolor[HTML]{FF0000}{Rdeča}`
* - `cmy`
  - Cijan, magenta, rumena
  - $[0,1]^3$
  - `\textcolor[cmy]{0,1,1}{Rdeča}`
* - `cmyk`
  - Cijan, magenta, rumena, črna
  - $[0,1]^4$
  - `\textcolor[cmyk]{0,1,1,0}{Rdeča}`
* - `Gray`
  - Odtenek sive
  - $\{0, \dots, 15\}$
  - `\textcolor[Gray]{0}{Črna}`
* - `gray`
  - Odtenek sive
  - $[0,1]$
  - `\textcolor[gray]{0}{Črna}`
* - `wave` - Valovna dolžina (nm) - $[380,780]$ - `\textcolor[wave]{700}{Rdeča}`
:::

:::{admonition} Opozorilo!
:class: warning
Pri mešanju barv v različnih modelih lahko dobimo nepričakovane rezultate. Na primer, da izrazi `<barva1>!25!<barva2>` in `<barva2>!75!<barva1>` ne dajeta vedno iste barve, če sta `<barva1>` in `<barva2>` definirani v različnih barvnih modelih.
Zato je priporočljivo, da pri mešanju barv vedno uporabljamo barve iz istega modela.
Alternativno v poglavje 6 dokumentacije paketa [`xcolor`](https://ctan.org/pkg/xcolor?lang=en) najdemo več informacij o spremenjenju med barvnimi modeli.
:::

Z uporabo ukaza `\definecolor{<ime_barve>}{<model>}{<parametri>}` (v preambuli) lahko definiramo svoje barve. Na primer, z ukazom `\definecolor{ULrdeca}{RGB}{226,25,30}` definiramo barvo z imenom `ULrdeca`, ki je rdeča barva Univerze v Ljubljani.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\definecolor{ULrdeca}{RGB}{226,25,30}
% V telesu dokumenta:
\noindent
\textcolor{ULrdeca}
{To je rdeča barva Univerze v Ljubljani.}
```

:::

:::{card} PDF

````{figure} ./img/05_eg-ULrdeca.png
:name: fig:eg-ULrdeca

:::
::::

Doslej smo obravnavali ukaze za barvanje besedila. Možno je tudi spremeniti barbo ozadja strani z ukazom
```latex
\pagecolor[<model>]{<barva>}.
````

Ta ukaz je različica _switch_, to pomeni da spremeni barvo celotne strani od mesta, kjer je uporabljen, naprej. Če želimo vrniti nazaj privzeto barvo ozadja (prozoren), uporabimo ukaz `\nopagecolor`.

V izrazu za barvo lahko uporabimo znak `-` (minus), da dobimo nasprotno barvo. Na primer, `-white` predstavlja črno barvo.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\newpage
\pagecolor{yellow}
\color{-yellow}
\noindent
Barva strani je rumena, \\
besedilo pa nasprotno rumeno.
```

:::

:::{card} PDF

````{figure} ./img/05_eg-pagecolor.png
:name: fig:eg-pagecolor
:::
::::

Če želimo spremeniti barvo samo določenega območja besedila, lahko uporabimo ukaz `\colorbox[<model>]{<barva>}{<besedilo>}`.
Ta ukaz obdaja besedilo z ozadjem določene barve.
Ukaz `\fcolorbox[<model>]{<barva_okvirja>}{<barva_ozadja>}{<besedilo>}` obdaja besedilo z okvirjem določene barve in ozadjem določene barve.

::::{grid} 2 2 2 2


:::{card} LaTeX

```latex
Zanimivo je, kako lahko barve
\colorbox{yellow}{\textcolor{red}{izboljšajo}}
dokument.
Vendar pa lahko prekomerna uporaba barv dokument tudi
\fcolorbox{orange}{gray}{pokvari}.
````

:::

:::{card} PDF

````{figure} ./img/05_eg-colorbox.png
:name: fig:eg-colorbox
:::
::::

## Ukazi in okolja po meri.

LaTeX omogoča ustvarjanje lastnih ukazov in okolij, kar lahko olajša pisanje ponavljajočih se struktur v dokumentu.
Klasični način za definiranje novega ukaza je z uporabo ukaza `\newcommand{<ime_ukaza>}[<število_argumentov>]{<definicija>}` in novega okolja z uporabo ukaza `\newenvironment{<ime_okolja>}[<število_argumentov>]{<začetek_definicije>}{<konec_definicije>}`.
Čeprav ti ukazi delujejo povsem normalno za osnovne definicije novih ukazov in okolij, bodo postopoma postali zastareli.
Tega pristopa tukaj ne bomo obravnavali, vendar če bralca zanima, priporočamo branje Overleafovih navodil za [nove ukaze](https://www.overleaf.com/learn/latex/Commands){target=_blank} in [nova okolja](https://www.overleaf.com/learn/latex/Environments){target=_blank} (v angleščini).

Sodobnejši in bolj zmogljiv način za definiranje novih ukazov in okolij je z uporabo ukaza `\NewDocumentCommand` in `\NewDocumentEnvironment`.
Ta pristop omogoča bolj fleksibilno določanje argumentov in podpira različne vrste argumentov, kot so obvezni, neobvezni, in več vrst argumentov.

Ukaz `\NewDocumentCommand` ima naslednjo sintakso:
```latex
\NewDocumentCommand{<ime_ukaza>}{<vrsta_argumentov>}{<definicija>}
````

- `<ime_ukaza>`: Ime novega ukaza, ki ga želimo definirati (vključno z `\`).
- `<vrsta_argumentov>`: Niz, ki določa vrste argumentov, ki jih ukaz sprejema. To bomo počasi obravnavali v nadaljevanju.
- `<definicija>`: Telo ukaza, kjer lahko uporabimo argumente znotraj ukaza.

Najlažje ukaz, da lahko definiramo je brez argumentov, to pomeni z praznim nizom za `<vrsta_argumentov>`.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\pozdrav}{}
{Pozdravljen, svet!}
% V telesu dokumenta:
Vsakič da uporabljamo ukaz
\texttt{\textbackslash pozdrav},
dobimo isti rezultat: \pozdrav.
```

:::

:::{card} PDF

````{figure} ./img/05_eg-NewCommand-NoArgs-1.png
:::
::::

Ta način je zelo uporaben, ko obstajajo del besedila ali strukture, ki jih pogosto uporabljamo v dokumentu.
Seveda, če se kdajkoli odločimo spremeniti to besedilo ali strukturo, moramo to storiti samo na enem mestu: v definiciji ukaza.

::::{grid} 2 2 2 2


:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\pozdrav}{}
{\textit{Pozdravljen},
\textbf{svet}!}
% V telesu dokumenta:
Vsakič da uporabljamo ukaz
\texttt{\textbackslash pozdrav},
dobimo isti rezultat: \pozdrav.
````

:::

:::{card} PDF

````{figure} ./img/05_eg-NewCommand-NoArgs-2.png
:::
::::

Pogosta uporaba novih ukazov je pri definiciji matematičnih izrazov, ki jih pogosto uporabljamo. Kot smo videli v prejšnjih poglavjih, nekatere vir (npr. [Standard ISO 80000-2](https://www.sist.si/velicine-in-enote-2-del-matematika-sist-en-iso-80000-220196-prevod-v-slovenscino.html)) priporočajo, da se za matematične konstante in posebne funkcije uporablja rimska pisava (upravičeno).
Seveda, ni smiselno vsakič pisati `\mathrm{\pi}` za konstantno $\mathrm{pi}$ ali `\mathrm{e}` za Eulerjevo število.
Namesto tega lahko definiramo nove ukaze za te konstante:

::::{grid} 2 2 2 2


:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\kpi}{}
{\mathrm{\pi}} %Ukaz \kpi, kot 'konstantna pi'
\NewDocumentCommand{\ke}{}
{\mathrm{e}} %Ukaz \ke za Eulerjevo število
% V telesu dokumenta:
\[
\ke^{i \kpi} + 1 = 0 \text{ vs. }
e^{i \pi} + 1 = 0
\]
````

:::

:::{card} PDF

$$
 \mathrm{e}^{i \mathrm{\pi}} + 1 = 0 \text{ vs. }
 e^{i \pi} + 1 = 0
$$

:::
::::

:::{admonition} Nasvet
:class: tip
Ko definiramo nove ukaze, ki se bodo uporabljali v matematičnem načinu, je priporočljivo, da ne vključimo nobenega simbola, ki označuje matematični način.
Na primer, pri definiciji ukaza za konstantno $\pi$, je bolje definirati ukaz `\kpi` kot `\mathrm{\pi}` namesto `$\mathrm{\pi}$`.
:::

Če želimo definirati nov ukaz, ki sprejema argumente, moramo določiti vrsto in število argumentov v nizu `<vrsta_argumentov>`.
Nekateri najpogostejši tipi argumentov so prikazani v {numref}`Tabeli {number}<tbl:arg-types>`.

:::{list-table} Najpogostejši tipi argumentov v `\NewDocumentCommand`
:name: tbl:arg-types
:header-rows: 1

* - Tip argumenta
  - Opis
* - `m`
  - Obvezni argument, ki lahko vsebuje več vrstic.
* - `O{<privzeta_vrednost>}`
  - Neobvezni argument, ki lahko vsebuje več vrstic. Če ni podan, ima privzeto vrednost `<privzeta_vrednost>`.
* - `o`
  - Neobvezni argument. Če ni podan, natisne posebni niz `-NoValue-`. Običajno v definicij uporaba pogojev za preverjanje, ali je bil argument podan kot je ukaz `\IfNoValueTF`.
* - `D<levo><desno>{<privzeta_vrednost>}`
  - Neobvezni argument, ki je obdan z `<levo>` in `<desno>`. Če ni podan, ima privzeto vrednost `<privzeta_vrednost>`. Običajno se uporablja znak `<` in `>`, za `<levo>` in `<desno>`. Deluje kot `o`, vendar s posebnimi ločevalniki.
* - `d<levo><desno>`
  - Podobno kot `D`, vendar brez privzete vrednosti. Deluje kot `o`, vendar s posebnimi ločevalniki.
* - `s`
  - Preklopni argument (switch). Če je prisoten, je vrednost `\BooleanTrue`, sicer `\BooleanFalse`. Uporabno, ko definiramo ukaze 'z zvezdico' ali 'brez zvezdice'.
:::

Najlažje tip argumenta je `m`, ki predstavlja obvezni argument. Na primer, lahko definiramo ukaz za barvanje besedila z določenim in barvo. Pri definiciji ukazo, uporabljamo znak `#1` za sklicevanje na prvi argument.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\textULrdeca}{m}
{\textcolor[RGB]{226,25,30}{#1}}
% V telesu dokumenta:
Dobodošli v
\textULrdeca{Univerzi v Ljubljani}!
Ta \textULrdeca{barva} mi je zelo všeč.
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsM-1.png
:name: fig:eg-ArgsM-1
```

:::
::::

Seveda, lahko definiramo ukaze z več argumenti. Dovolj je da dodamo več tipov argumentov v niz `<vrsta_argumentov>` in uporabimo `#2`, `#3`, ... za sklicevanje na druge argumente.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\zap}{mm}
{#1_{1}, \dots, #1_{#2}}
% V telesu dokumenta:
Ukaz
\texttt{\textbackslash zap\{x\}\{n\}}
ustvari zaporedje
$x_{1}, \dots, x_{n}$,
torej
\texttt{\textbackslash zap\{a\}\{10\}} daje
$ \zap{a}{10} $.
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsM-2.png
:name: fig:eg-ArgsM-2
```

:::
::::

Če želimo definirati ukaz z neobveznimi argumenti, lahko uporabimo tip `O{<privzeta_vrednost>}`. Ne pozabite, da neobvezni argumenti damo znotraj oklepaj `[]` pri klicu ukaza.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\pozdrav}{O{svet}}
{Pozdravljen, #1!}
% V telesu dokumenta:
Ukaz
\texttt{\textbackslash pozdrav[<arg>]}
pozdravi \texttt{<arg>},
če ga ne damo, pozdravi \texttt{svet}:
\pozdrav[vsi], \pozdrav.
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsO-1.png
:name: fig:eg-ArgsO-1
```

::::
::::

Lahko seveda kombiniramo različne tipe argumentov. Na primer, lahko definiramo ukaz z enim obveznim in enim neobveznim argumentom:

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
V preambuli:
\NewDocumentCommand{\Zap}{O{n}m}
{#2_{1}, \dots, #2_{#1}}
% V telesu dokumenta:
Nekatere zaporedje imajo veliko elementov:
$\Zap[1000]{a}$,
za večino pa sploh ne vemo,
koliko jih je:
$\Zap{b}$.
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsMO-1.png
:name: fig:eg-ArgsMO-1
```

:::
::::

Upoštevajte, da je vrstni red argumentov pomemben. Če je ukaz `\ukaz` definiran z vrstnim redom argumentov `O{}m`, ga moramo klicati z obveznim argumentom najprej, nato pa neobveznim argumentom (če ga želimo podati), to pomeni `\ukaz[<neobvezni>]{<obvezni>}` je pravilen klic, medtem ko `\ukaz{<obvezni>}[<neobvezni>]` ni pravilen klic.
Dobra praksa je, da najprej definiramo vse neobvezne argumente, nato pa obvezne argumente.

Včasih želimo da ukaz deluje drugače, če je neobvezni argument podan ali ne. V tem primeru lahko uporabimo tip argumenta `o` in ukaz `\IfValueTF` za preverjanje, ali je bil argument podan.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
%V preambuli:
\NewDocumentCommand{\ukaz}{o}
{
  \IfValueTF{#1}
  {Neobvezni argument je: \textbf{#1}} %Če je podan prvi argument, vrni njegov vrednost
  {Ni neobveznega argumenta.} %Če ni podanega argumenta
}
% V telesu dokumenta:
 \ukaz
 \ukaz[Podan argument]
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsMo-2.png
:name: fig:eg-ArgsMo-2
```

:::
::::

Namesto ukaza `\IfValueTF`, lahko uporabimo tudi ukaz `\IfValueT`, če želimo izvesti dejanje samo, če je bil argument podan, ali ukaz `\IfValueF`, če želimo izvesti dejanje samo, če argument ni bil podan. Lahko tudi uporabimo ukaze `\IfNoValueTF`, `\IfNoValueT`, in `\IfNoValueF`, ki delujejo nasprotno.

Ko želimo da ukaz sprejme neobvezni argument z določenimi ločevalniki, lahko uporabimo tip argumenta `D<levo><desno>{<privzeta_vrednost>}`.
Običajno se uporabljata znaka `<` in `>` kot ločevalnika.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\zapLim}{D<>{1}O{n}m}
{#3_{#1}, \dots, #3_{#2}}
% V telesu dokumenta:
Večina zaporedj gre od $1$ do $n$:
$\zapLim{a}$,
vendar včasih želimo drugačen začetek:
$\zapLim<0>{a}$,
ali drugačen konec:
$\zapLim[500]{a}$.
ali pa kar oboje:
$\zapLim<5>[500]{a}$.
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsD-1.png
:name: fig:eg-ArgsD-1
```

:::
::::

Če namesto `D<levo><desno>{<privzeta_vrednost>}` uporabimo `d<levo><desno>`, dobimo podoben učinek, vendar brez privzete vrednosti (točno tako, kot ko uporabljamo `o`). V tem primeru moramo vedno preveriti, ali je bil argument podan z uporabo ukaza `\IfValueTF` in podobnih.

Nazadnje, lahko tudi uporabljamo znak `s` za niz `<vrsta_argumentov>`, da definiramo preklopni argument oz. različica ukaz _z zvezdico_. Pri definiciji ukaza, lahko uporabimo ukaz `\IfBooleanTF`, da preverimo, ali je bil preklopni argument podan.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
% V preambuli:
\NewDocumentCommand{\jeRekli}{sm}
{\IfBooleanTF{#1}
{Ana je rekla: ``#2''}
{Boštjan je rekel: ``#2''}
}
% V telesu dokumenta:
\jeRekli{Danes je lep dan.}\\
\jeRekli*{Upam, da bo jutri tudi tako lep dan.}
```

:::

:::{card} PDF

```{figure} ./img/05_eg-ArgsS-1.png
:name: fig:eg-ArgsS-1
```

:::
::::

:::{exercise}
:label: ex_ukazi

1. Definirajte nov ukaz `\sporocilo`, ki sprejme en obvezni argument in en neobvezni argument (privzeta vrednost naj bo "Obvestilo"). Ukaz mora natisniti neobvezni argument, nato simbol `:` in nato obvezni argument v poševni pisavi.
2. Ustvarite nov ukaz `\vektor`, ki sprejme en obvezni argument (za vnose vektorja) in en neobvezni argument (za dimenzijo vektorja) tako da, če je podan, ukaz natisne $n$-dimenzionalni vektor, sicer pa $3$-dimenzionalni vektor. To je, `\vektor[17]{v}` mora natisniti $(v_{1}, \dots, v_{17})$, ampak `\vektor{v}` mora natisniti $(v_{1}, v_{2}, v_{3})$.
3. Ustvarite nov ukaz `\rdeceAliModre`, ki sprejme en obvezni argument in en preklopni argument. Če je preklopni argument podan, ukaz natisne besedilo v rdeči barvi, sicer v modri barvi.
4. Ustvarite nov ukaz `\myInt` za integral, ki sprejme dva obvezna argumenta: funkcijo in spremenljivko integracije; en neobvezni argument
   za spodnjo mejo (privzeta vrednost naj bo prazna) z ločevalnikoma `<` in `>`; in en neobvezni argument za zgornjo mejo (privzeta vrednost naj bo prazna) z ločevalnikoma `[` in `]`. Ukaz naj natisne integral z ustreznimi mejami, če so podane. Na primer, `\myInt<0>[1]{f(x)}{x}` naj natisne $\int_{0}^{1} f(x) \, dx$, medtem ko `\myInt{f(x)}{x}` naj natisne $\int f(x) \, dx$.
   :::

```{margin}
[Seznam vaj](#05_latexRazno_vaje)
```

:::{solution} ex_ukazi
:class: tip, dropdown

1. Definicija ukaza `\sporocilo`:

```latex
\NewDocumentCommand{\sporocilo}{O{Obvestilo}m}
{#1: \textit{#2}}
```

2. Definicija ukaza `\vektor`:

```latex
\NewDocumentCommand{\vektor}{om}
{
  \IfValueTF{#1}
  {(#2_{1}, \dots, #2_{#1})} %Če je podan prvi argument, vrni vektor z dimenzijo #1
  {(#2_{1}, #2_{2}, #2_{3})} %Če ni podanega argumenta, vrni 3-dimenzionalni vektor
}
```

3. Definicija ukaza `\rdeceAliModre`:

```latex
\NewDocumentCommand{\rdeceAliModre}{sm}
{\IfBooleanTF{#1}
{\textcolor{red}{#2}} %Če je podan preklopni argument, natisni rdeče
{\textcolor{blue}{#2}} %Če ni podanega preklopnega argumenta, natisni modro
}
```

4. Definicija ukaza `\myInt`:

```latex
\NewDocumentCommand{\myInt}{D<>{}O{}mm}
{
  \int_{#1}^{#2} #3 \, d#4
}
```

:::

Lahko tudi definiramo nova okolja z uporabo ukaza `\NewDocumentEnvironment`, ki ima podobno sintakso kot `\NewDocumentCommand`.

```latex
\NewDocumentEnvironment{<ime_okolja>}{<vrsta_argumentov>}
{<začetek_definicije>}
{<konec_definicije>}
```

- `<ime_okolja>`: Ime novega okolja, ki ga želimo definirati.
- `<vrsta_argumentov>`: Niz, ki določa vrste argumentov, ki jih okolje sprejema. To deluje skoraj enako kot pri ukazu `\NewDocumentCommand`.
- `<začetek_definicije>`: Koda za začetek okolja, kjer lahko uporabimo argumente znotraj okolja.
- `<konec_definicije>`: Koda za konec okolja.

Naslednji primeri naj bi pojasnili uporabo tega ukaza.

:::{prf:example}
:label: eg_okolja_kralj-1

`````{tab-set}
````{tab-item} LaTeX
```latex
% V preambuli:
\NewDocumentEnvironment{kralj}{}
{
  \begin{FlushLeft} \textbf{Poslušajte!}
  Njegova veličanstvo, kralj Artur bo podal izjavo:
  \end{FlushLeft}
  \begin{Center} \scshape
}
{
  \normalfont \end{Center}\begin{FlushRight}
  Konec izjave. Hvala za vašo pozornost.
  \end{FlushRight}
}
% V telesu dokumenta:
\begin{kralj}
To je izjava kralja Arturja.
\end{kralj}
```

````
````{tab-item} PDF
``` {figure} ./img/05_eg-okolja-kralj-1.png
  :name: fig:eg-okolja-kralj-1
```
````
`````

:::

Lahko tudi definiramo okolja z argumenti. Na primer, lahko definiramo okolje `kraljIme`, ki sprejme en obvezni argument za ime kralja.

:::{prf:example}
:label: eg_okolja_kralj-2

`````{tab-set}
````{tab-item} LaTeX
```latex
% V preambuli:
\NewDocumentEnvironment{kraljIme}{m}
{
  \begin{FlushLeft} \textbf{Poslušajte!}
  Njegova veličanstvo, kralj \emph{#1} bo podal izjavo:
  \end{FlushLeft}
  \begin{Center} \scshape
}
{
  \normalfont \end{Center}\begin{FlushRight}
  Konec izjave. Hvala za vašo pozornost.
  \end{FlushRight}
}
% V telesu dokumenta:
\begin{kraljIme}{Artur}
  Kralj vam želi lepe praznike
\end{kraljIme}
```

````
````{tab-item} PDF
``` {figure} ./img/05_eg-okolja-kralj-2.png
  :name: fig:eg-okolja-kralj-2
```
````
`````

:::

Tukaj imamo problem, ker želimo imeti različne naslove in zaključke za kralja in kraljico. To lahko rešimo z uporabo preklopnega argumenta `s`.
Moramo v definiciji okolja uporabiti ukaz `\IfBooleanTF`, da preverimo, ali je bil preklopni argument podan; to lahko storimo v obeh delih definicije okolja.

Pazite, za razliko od nekaterih drugih LaTeX okoljih (npr. `align`), ko uporabljamo okolje z zvezdico, zvezdica gre zunaj oklepajev imenja okolja, t.j. `\begin{kralij}*{Ime}` namesto `\begin{kralij*}{Ime}`. Zvezdica ni potrebna na koncu okolja, t.j. `\end{kralij}` je pravilen klic tudi za okolje z zvezdico.

:::{prf:example}
:label: eg_kralji

`````{tab-set}
````{tab-item} LaTeX
```latex
% V preambuli:
\NewDocumentEnvironment{kralji}{sm}
{ % ob \begin{kralji}
  \IfBooleanTF{#1}{ %z zvezdico
    \begin{FlushLeft} \textbf{Poslušajte!} Njegova veličanstvo, kralj \emph{#2} bo podal izjavo: \end{FlushLeft}\begin{Center} \scshape
  }
  { %brez zvezdice
    \begin{FlushLeft} \textbf{Poslušajte!} Njena veličanstvo, kraljica \emph{#2} bo podala izjavo: \end{FlushLeft}\begin{Center} \scshape
  }
}
{ % ob \end{kralji}
  \IfBooleanTF{#1}
  { %z zvezdico
    \normalfont \end{Center}\begin{FlushRight} Konec izjave.  Kralj je hvalžen za vašo pozornost.\end{FlushRight}
  }
  { %brez zvezdice
    \normalfont \end{Center}\begin{FlushRight} Konec izjave. Kraljica je hvaležna za vašo pozornost. \end{FlushRight}
  }
}

% V telesu dokumenta:
\begin{kralji}*{Artur}
Kraljeve besede.
\end{kralji}

\begin{kralji}{Guinevere}
Kraljičine besede.
\end{kralji}
```
````
````{tab-item} PDF
``` {figure} ./img/05_eg-okolja-kralj-2.png
  :name: fig:eg-okolja-kralj--3
```
````
`````

:::

(05_latexRazno_vaje)=

## Vaje

- [Vaja %s](#ex_input_include): Vaje o ukazih `\input{}` in `\include{}`.
- [Vaja %s](#ex-gradient): Vaja o mešanju barv.
- [Vaja %s](#ex_ukazi): Vaje o definiciji novih ukazov z `\NewDocumentCommand`.
