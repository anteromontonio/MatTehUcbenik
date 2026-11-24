(05_latexRazno)=

# LaTeX: Razno

:::{admonition} Cilji poglavja
:class: tip
Po tem poglavju boste znali:

- razdeliti obsežnejši dokument na več datotek z ukazoma `\include` in `\input`,
- s paketom `xcolor` barvati besedilo, matematične izraze, ozadja in okvirje ter mešati in definirati barve,
- definirati lastne ukaze in okolja z ukazoma `\NewDocumentCommand` in `\NewDocumentEnvironment`.

Predvideni čas: 2 do 3 pedagoške ure.
:::

V tem poglavju so zbrani različni nasveti in triki za delo z LaTeXom, ki ne sodijo v druga poglavja.

## Obsežnejši projekti

Za obsežnejše projekte, kot so diplomske naloge, je priporočljivo razdeliti dokument na več datotek in jih vključiti v glavno datoteko z ukazom `\input{}` ali `\include{}`.
To omogoča lažje upravljanje in urejanje posameznih delov dokumenta.

Ukaz `\include{<pot do datoteke>}` vključi vsebino navedene datoteke in samodejno začne novo stran pred vključitvijo in po njej. Datoteko navedemo brez končnice `.tex`.

Ukaz `\includeonly{<ime_datoteke1>,<ime_datoteke2>,...}` omogoča, da se med prevajanjem vključijo samo določene datoteke, kar je uporabno za hitrejše pregledovanje določenih delov dokumenta.

:::{admonition} Pazite!
:class: warning

- Ukaz `\include{<ime_datoteke>}` lahko uporabljamo samo v **telesu glavne datoteke**, ne pa znotraj drugih vključenih datotek.
- Ukaz `\includeonly{<ime_datoteke1>,<ime_datoteke2>,...}` mora biti v preambuli glavne datoteke.
  V telesu dokumenta morajo biti še vedno ukazi `\include{}` za vse datoteke, ki jih želimo vključiti.
- Ukaz `\include{}` vedno začne novo stran, zato ni primeren za vključevanje manjših delov besedila. Poleg tega ta ukaz ne deluje znotraj okolij, kot sta `\begin{figure}...\end{figure}` ali `\begin{table}...\end{table}`.
:::

Ukaz `\include` je precej omejujoč in ima posebno uporabo: vključevanje posameznih poglavij (`chapter`) v velik projekt. Ker vedno začne novo stran, je koristen skupaj z ukazom `\includeonly{}`: prelomi strani se ne premaknejo, tudi če vključimo samo nekatere datoteke, zato številke strani in sklici ostanejo pravilni.

Včasih je bolj smiselno uporabiti ukaz `\input{<pot do datoteke>}`, ki vključi vsebino navedene datoteke brez preloma strani.
Ukaz `\input{}` lahko uporabljamo kjerkoli v dokumentu, tudi znotraj okolij, kot sta `\begin{figure}...\end{figure}` ali `\begin{table}...\end{table}`.

Ukaz `\input{}` lahko uporabimo tudi za vključitev datotek z ukazi LaTeX, kot so definicije makrov ali nastavitve paketov. Pogosto na primer vključimo datoteko, recimo `preambula.tex`, ki vsebuje vse nastavitve in pakete, ki jih želimo uporabiti v našem dokumentu.

:::{admonition} Pazite!
:class: warning
Čeprav lahko z ukazom `\input` naložimo pakete v našo datoteko, mora biti vrstica z ukazom `\documentclass` **vedno** v glavni datoteki, pred vsemi ukazi `\input`.
:::

:::{exercise}
:label: ex_input_include

1. Napišite glavno datoteko `glavno.tex` s standardno preambulo in okoljem `document`.
   Namesto razreda `article` uporabite razred `book` ali `report`.
2. Ustvarite dve datoteki, `poglavje1.tex` in `poglavje2.tex`, ki vsebujeta besedilo za dve poglavji. Za nadomestno besedilo lahko uporabite paket `lipsum`.
3. Z ukazom `\include{}` vključite ti dve datoteki v glavno datoteko.
4. Shranite vse datoteke in prevedite glavno datoteko `glavno.tex`.
5. Z ukazom `\includeonly` v preambuli vključite samo datoteko `poglavje2.tex` in dokument ponovno prevedite.
6. Nato v glavni datoteki namesto razreda `book` oz. `report` uporabite razred `article`. V obeh vključenih datotekah spremenite tudi vse ukaze `\chapter{}` v ukaze `\section{}`. Shranite.
7. Ukaze `\include{}` zamenjajte z ukazi `\input{}`, ukaz `\includeonly{}` zakomentirajte in ponovno shranite glavno datoteko.
8. Ustvarite datoteko `preambula.tex`, ki vsebuje vse pakete in nastavitve, ki jih želite uporabiti v glavnem dokumentu. Z ukazom `\input{preambula.tex}` jo vključite v glavno datoteko.
:::

:::{margin}
[Seznam nalog](#05_latexRazno_vaje)
:::

:::{solution} ex_input_include
:class: tip dropdown
Na koncu bi lahko bila datoteka `glavno.tex` videti nekako takole:

```latex
\documentclass{article}
\input{preambula.tex}
%Vsebina preambula.tex:
% \usepackage[slovene]{babel}
% \usepackage{lipsum}
% \usepackage{mathtools, amssymb, amsthm}
% \usepackage{graphicx, caption, subcaption}
% \usepackage{array, booktabs}
% \includeonly{poglavje2}

\begin{document}
\input{poglavje1}
% \include{poglavje1}
%Vsebina poglavje1.tex:
% \section{Prvi}
% \lipsum[1-3]
\input{poglavje2}
% \include{poglavje2}
%Vsebina poglavje2.tex:
% \section{Drugi}
% \lipsum[4-6]
\end{document}
```
:::

## Barve

Za uporabo barv v dokumentih LaTeX uporabimo paket `xcolor`. Paket omogoča uporabo treh ukazov za barvanje besedila:

- `\textcolor[<model>]{<barva>}{<besedilo>}`: obarva besedilo z dano barvo.
- `\color[<model>]{<barva>}`: spremeni barvo besedila od tega mesta naprej. To je različica _switch_ ukaza `\textcolor`, tako kot je ukaz `\bfseries` različica _switch_ ukaza `\textbf{}` za krepko pisavo.
- `\mathcolor[<model>]{<barva>}{<matematični_izraz>}`: obarva matematični izraz z dano barvo. Ukaz `\textcolor` sicer deluje tudi v matematičnem načinu, vendar `\mathcolor` bolje ohrani razmike in postavitev indeksov.

Za zdaj ne skrbite za neobvezni argument `<model>`. Ta argument določa, kaj se pričakuje kot argument `<barva>`. Če ga ne podamo, se privzeto uporablja model `named`, ki omogoča uporabo vnaprej določenih imen barv, kar pomeni, da barve pokličemo z imeni.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
%V preambuli
\usepackage{xcolor}
%V telesu dokumenta
\color{red} Svet je zdaj rdeč,
nekateri deli so
\textcolor{yellow}{rumeni}.
\[
\mathcolor{blue}{\sum_{k=0}}^{10} k
\]
Vse je še vedno rdeče,
\color{blue}
zdaj modro.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-barve-1.png
:label: fig:eg-barve-1
:alt: Rdeče besedilo z rumeno besedo rumeni, pod njim rdeča vsota, katere znak za vsoto in spodnja meja sta modra, na koncu stavek, ki preide iz rdeče v modro barvo.
:::
::::
:::::

Barve, ki so vnaprej določene v paketu `xcolor`, so prikazane na [Sliki %s](#tbl:basecolors).

:::{figure} ./img/05_xcolorList.png
:label: tbl:basecolors
:alt: Seznam devetnajstih barv z barvnim kvadratkom in imenom, od red, green in blue do brown, lime, olive, orange, pink, purple, teal in violet.
:height: 400px
Osnovne barve, ki jih določa paket `xcolor`.
:::

Seznam določenih barv lahko razširimo z možnostmi paketa `xcolor`. Na primer, z možnostjo `dvipsnames` (`\usepackage[dvipsnames]{xcolor}`) lahko uporabimo dodatne barve, prikazane na [Sliki %s](#tbl:dvipsnames).

:::{figure} ./img/05_xcolorDvipsnames.png
:label: tbl:dvipsnames
:alt: Seznam 68 barv v štirih stolpcih, vsaka z barvnim kvadratkom in imenom, na primer Apricot, Cerulean, ForestGreen, Mahogany in YellowOrange.
:height: 350px
Dodatne barve, ki jih določa paket `xcolor` z možnostjo `dvipsnames`.
:::

Drugi možnosti sta `svgnames` in `x11names`. Možnost `svgnames` določa 151 barv, ki so definirane v standardu SVG, možnost `x11names` pa 317 barv, ki so bile prvotno definirane za okenski sistem X11. Celoten seznam barv je na voljo v dokumentaciji paketa [`xcolor`](https://ctan.org/pkg/xcolor?lang=en).

Drugi način pridobivanja novih barv je mešanje dveh ali več barv. Sintaksa za mešanje dveh barv je naslednja:

```latex
<barva1>!<odstotek>!<barva2>
```

Rezultat je barva, ki je sestavljena iz `<odstotek>` odstotkov barve `<barva1>` in `(100 - <odstotek>)` odstotkov barve `<barva2>`. Na primer, `red!40!blue` ustvari vijolično barvo, ki je mešanica 40 % rdeče in 60 % modre.

Mešanje lahko vključuje tudi več kot dve barvi. V tem primeru se barve mešajo zaporedno. Na primer, `red!50!green!30!blue` najprej zmeša 50 % rdeče in 50 % zelene, nato pa dobljeno barvo zmeša z modro: rezultat je 30 % prej dobljene barve in 70 % modre.

::::{exercise}
:label: ex-gradient
Z mešanjem barv poustvarite barvni prehod (gradient), prikazan na spodnji sliki:

:::{figure} ./img/05_ex-gradient.png
:label: fig:ex-gradient
:alt: Beseda Slovenija z razmaknjenimi črkami, ki postopoma prehajajo od svetlo modre prek modre in vijolične do rdeče.
:height: 100px
:::
::::

:::{margin}
[Seznam nalog](#05_latexRazno_vaje)
:::

:::{solution} ex-gradient
:class: tip dropdown
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

Včasih moramo biti natančnejši pri barvah, ki jih uporabljamo. Za to uporabimo neobvezni argument `<model>`. Najlažje ga razumemo prek modela `Gray`. V tem modelu določimo odtenek sive barve z vrednostjo med `0` in `15`, kjer `0` predstavlja črno in `15` belo.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
\textcolor[Gray]{0}{Nula} \\
\textcolor[Gray]{3}{Tri} \\
\textcolor[Gray]{7}{Sedem} \\
\textcolor[Gray]{11}{Enajst} \\
\textcolor[Gray]{15}{Petnajst}
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-Gray-model.png
:label: fig:eg-Gray-model
:alt: Besede Nula, Tri, Sedem in Enajst druga pod drugo, vsaka v svetlejšem odtenku sive; zadnja beseda je bela in zato nevidna.
:width: 100px
:::
::::
:::::

Podobno lahko uporabimo model `gray`, kjer vrednosti segajo od `0` do `1`, pri čemer `0` predstavlja črno in `1` belo.

V [Tabeli %s](#tbl:color-models) so prikazani nekateri barvni modeli, ki jih podpira paket `xcolor`.

:::{list-table} Najpogostejši modeli barv v paketu `xcolor`
:label: tbl:color-models
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
* - `wave`
  - Valovna dolžina (nm)
  - $[363,814]$
  - `\textcolor[wave]{700}{Rdeča}`
:::

:::{admonition} Opozorilo!
:class: warning
Pri mešanju barv v različnih modelih lahko dobimo nepričakovane rezultate. Na primer, izraza `<barva1>!25!<barva2>` in `<barva2>!75!<barva1>` ne dasta vedno iste barve, če sta `<barva1>` in `<barva2>` definirani v različnih barvnih modelih.
Zato je priporočljivo, da pri mešanju vedno uporabljamo barve iz istega modela.
Več o pretvarjanju med barvnimi modeli najdemo v 6. poglavju dokumentacije paketa [`xcolor`](https://ctan.org/pkg/xcolor?lang=en).
:::

Z ukazom `\definecolor{<ime_barve>}{<model>}{<parametri>}` (v preambuli) lahko definiramo svoje barve. Na primer, z ukazom `\definecolor{ULrdeca}{RGB}{226,25,30}` definiramo barvo z imenom `ULrdeca`, ki je rdeča barva Univerze v Ljubljani.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\definecolor{ULrdeca}{RGB}{226,25,30}
% V telesu dokumenta:
\noindent
\textcolor{ULrdeca}
{To je rdeča barva Univerze v Ljubljani.}
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-ULrdeca.png
:label: fig:eg-ULrdeca
:alt: Stavek To je rdeča barva Univerze v Ljubljani, izpisan v rdeči barvi.
:::
::::
:::::

Doslej smo obravnavali ukaze za barvanje besedila. Spremenimo lahko tudi barvo ozadja strani, in sicer z ukazom

```latex
\pagecolor[<model>]{<barva>}
```

Tudi ta ukaz je različica _switch_, kar pomeni, da spremeni barvo strani od mesta, kjer je uporabljen, naprej. Če želimo nazaj privzeto barvo ozadja (prozorno), uporabimo ukaz `\nopagecolor`.

V izrazu za barvo lahko uporabimo znak `-` (minus), da dobimo nasprotno (komplementarno) barvo. Na primer, `-white` predstavlja črno barvo.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
\newpage
\pagecolor{yellow}
\color{-yellow}
\noindent
Barva strani je rumena, \\
besedilo pa nasprotno rumeno.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-pagecolor.png
:label: fig:eg-pagecolor
:alt: Rumena stran s temno modrim besedilom Barva strani je rumena, besedilo pa nasprotno rumeno.
:::
::::
:::::

Če želimo spremeniti barvo ozadja samo za določen del besedila, lahko uporabimo ukaz `\colorbox[<model>]{<barva>}{<besedilo>}`.
Ta ukaz besedilu doda ozadje dane barve.
Ukaz `\fcolorbox[<model>]{<barva_okvirja>}{<barva_ozadja>}{<besedilo>}` besedilo obda z okvirjem ene barve in ozadjem druge barve.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
Zanimivo je, kako lahko barve
\colorbox{yellow}{\textcolor{red}{izboljšajo}}
dokument.
Vendar pa lahko prekomerna uporaba barv dokument tudi
\fcolorbox{orange}{gray}{pokvari}.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-colorbox.png
:label: fig:eg-colorbox
:alt: Odstavek, v katerem je rdeča beseda izboljšajo na rumenem ozadju, beseda pokvari pa na sivem ozadju z oranžnim okvirjem.
:::
::::
:::::

## Ukazi in okolja po meri

LaTeX omogoča ustvarjanje lastnih ukazov in okolij, kar lahko olajša pisanje ponavljajočih se struktur v dokumentu.
Klasični način za definiranje novega ukaza je ukaz `\newcommand{<ime_ukaza>}[<število_argumentov>]{<definicija>}`, za definiranje novega okolja pa ukaz `\newenvironment{<ime_okolja>}[<število_argumentov>]{<začetek_definicije>}{<konec_definicije>}`.
Ti ukazi za osnovne definicije novih ukazov in okolij delujejo povsem dobro, vendar razvijalci LaTeXa danes priporočajo sodobnejši pristop, ki ga opišemo spodaj.
Klasičnega pristopa tukaj ne bomo obravnavali. Če vas zanima, priporočamo branje Overleafovih navodil za [nove ukaze](https://www.overleaf.com/learn/latex/Commands) in [nova okolja](https://www.overleaf.com/learn/latex/Environments) (v angleščini).

Sodobnejši in zmogljivejši način za definiranje novih ukazov in okolij sta ukaza `\NewDocumentCommand` in `\NewDocumentEnvironment`.
Ta pristop omogoča bolj prilagodljivo določanje argumentov in podpira različne vrste argumentov, kot so obvezni, neobvezni in preklopni argumenti.

Ukaz `\NewDocumentCommand` ima naslednjo sintakso:

```latex
\NewDocumentCommand{<ime_ukaza>}{<vrsta_argumentov>}{<definicija>}
```

- `<ime_ukaza>`: ime novega ukaza, ki ga želimo definirati (vključno z `\`).
- `<vrsta_argumentov>`: niz, ki določa vrste argumentov, ki jih ukaz sprejema. Vrste argumentov bomo postopoma spoznali v nadaljevanju.
- `<definicija>`: telo ukaza, v katerem lahko uporabimo argumente ukaza.

Najpreprostejši je ukaz brez argumentov, pri katerem je `<vrsta_argumentov>` prazen niz.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\NewDocumentCommand{\pozdrav}{}
{Pozdravljen, svet!}
% V telesu dokumenta:
Vsakič, ko uporabimo ukaz
\texttt{\textbackslash pozdrav},
dobimo isti rezultat: \pozdrav
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-NewCommand-NoArgs-1.png
:label: fig:eg-NewCommand-NoArgs-1
:alt: Odstavek, ki se konča z besedilom Pozdravljen, svet!, ki ga natisne ukaz pozdrav.
:::
::::
:::::

Takšni ukazi so zelo uporabni za dele besedila ali strukture, ki jih v dokumentu pogosto uporabljamo.
Če se kdaj odločimo to besedilo ali strukturo spremeniti, moramo to storiti samo na enem mestu: v definiciji ukaza.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\NewDocumentCommand{\pozdrav}{}
{\textit{Pozdravljen},
\textbf{svet}!}
% V telesu dokumenta:
Vsakič, ko uporabimo ukaz
\texttt{\textbackslash pozdrav},
dobimo isti rezultat: \pozdrav
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-NewCommand-NoArgs-2.png
:label: fig:eg-NewCommand-NoArgs-2
:alt: Enak odstavek kot v prejšnjem primeru, le da je beseda Pozdravljen ležeča, beseda svet pa krepka.
:::
::::
:::::

Pogosta uporaba novih ukazov je definicija matematičnih izrazov, ki jih pogosto uporabljamo. Kot smo videli v poglavju [](./04_latexMatematika.md), nekateri viri (npr. [Standard ISO 80000-2](https://www.sist.si/velicine-in-enote-2-del-matematika-sist-en-iso-80000-220196-prevod-v-slovenscino.html)) priporočajo, da za matematične konstante in posebne funkcije uporabljamo pokončno pisavo (upravičeno).
Seveda ni smiselno vsakič pisati `\mathrm{e}` za Eulerjevo število ali `\uppi` (iz paketa `upgreek`) za število $\pi$. Spomnite se, da ukaz `\mathrm{\pi}` za pokončni $\pi$ ne zadošča.
Namesto tega lahko definiramo nove ukaze za te konstante:

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\usepackage{upgreek}
\NewDocumentCommand{\kpi}{}
{\uppi} %Ukaz \kpi, kot 'konstantni pi'
\NewDocumentCommand{\ke}{}
{\mathrm{e}} %Ukaz \ke za Eulerjevo število
% V telesu dokumenta:
\[
\ke^{i \kpi} + 1 = 0 \text{ vs. }
e^{i \pi} + 1 = 0
\]
```
::::

::::{card} PDF
$$
 \mathrm{e}^{i \mathrm{\pi}} + 1 = 0 \text{ vs. }
 e^{i \pi} + 1 = 0
$$
::::
:::::

:::{admonition} Nasvet!
:class: tip
Ko definiramo nove ukaze, ki jih bomo uporabljali v matematičnem načinu, je priporočljivo, da v definicijo ne vključimo znakov, ki začnejo matematični način.
Na primer, ukaz `\kpi` za konstanto $\pi$ je bolje definirati kot `\uppi` namesto `$\uppi$`. Tako ga lahko brez težav uporabimo znotraj drugih formul.
:::

Če želimo definirati nov ukaz, ki sprejema argumente, moramo v nizu `<vrsta_argumentov>` določiti vrsto in število argumentov.
Nekatere najpogostejše vrste argumentov so prikazane v [Tabeli %s](#tbl:arg-types).

:::{list-table} Najpogostejše vrste argumentov v `\NewDocumentCommand`
:label: tbl:arg-types
:header-rows: 1

* - Vrsta argumenta
  - Opis
* - `m`
  - Obvezni argument.
* - `O{<privzeta_vrednost>}`
  - Neobvezni argument. Če ga ne podamo, ima privzeto vrednost `<privzeta_vrednost>`.
* - `o`
  - Neobvezni argument. Če ga ne podamo, ima posebno vrednost `-NoValue-`, zato v definiciji običajno s pogojem, kot je `\IfValueTF`, preverimo, ali je bil podan.
* - `D<levo><desno>{<privzeta_vrednost>}`
  - Neobvezni argument, ki je obdan z `<levo>` in `<desno>`. Če ga ne podamo, ima privzeto vrednost `<privzeta_vrednost>`. Običajno uporabimo znaka `<` in `>`. Deluje kot `O`, vendar s posebnimi ločevalniki.
* - `d<levo><desno>`
  - Podobno kot `D`, vendar brez privzete vrednosti. Deluje kot `o`, vendar s posebnimi ločevalniki.
* - `s`
  - Preklopni argument (zvezdica). Če je prisoten, je vrednost `\BooleanTrue`, sicer `\BooleanFalse`. Uporaben je, ko definiramo ukaze "z zvezdico" in "brez zvezdice".
:::

Argument nobene od teh vrst ne sme vsebovati prazne vrstice (tj. novega odstavka). Če to želimo, pred vrsto argumenta dodamo znak `+`, npr. `+m`.

Najpreprostejša vrsta argumenta je `m`, ki predstavlja obvezni argument. Na primer, lahko definiramo ukaz za barvanje besedila z določeno barvo. V definiciji ukaza se na prvi argument sklicujemo z `#1`.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\NewDocumentCommand{\textULrdeca}{m}
{\textcolor[RGB]{226,25,30}{#1}}
% V telesu dokumenta:
Dobrodošli na
\textULrdeca{Univerzi v Ljubljani}!
Ta \textULrdeca{barva} mi je zelo všeč.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsM-1.png
:label: fig:eg-ArgsM-1
:alt: Stavek Dobrodošli na Univerzi v Ljubljani! Ta barva mi je zelo všeč, v katerem sta besedi Univerzi v Ljubljani in barva rdeči.
:::
::::
:::::

Seveda lahko definiramo tudi ukaze z več argumenti. Dovolj je, da v niz `<vrsta_argumentov>` dodamo več vrst argumentov in se na naslednje argumente sklicujemo z `#2`, `#3` …

:::::{grid} 2 2 2 2
::::{card} LaTeX
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
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsM-2.png
:label: fig:eg-ArgsM-2
:alt: Odstavek, ki pojasni, da ukaz zap z argumentoma x in n da zaporedje x_1 do x_n, z argumentoma a in 10 pa zaporedje a_1 do a_10.
:::
::::
:::::

Če želimo definirati ukaz z neobveznim argumentom, lahko uporabimo vrsto `O{<privzeta_vrednost>}`. Ne pozabite, da neobvezne argumente pri klicu ukaza podamo v oglatih oklepajih `[]`.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\NewDocumentCommand{\pozdrav}{O{svet}}
{Pozdravljeni, #1!}
% V telesu dokumenta:
Ukaz
\texttt{\textbackslash pozdrav[<arg>]}
pozdravi \texttt{<arg>},
če ga ne damo, pozdravi \texttt{svet}:
\pozdrav[vsi], \pozdrav.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsO-1.png
:label: fig:eg-ArgsO-1
:alt: Odstavek, ki se konča z izpisoma Pozdravljeni, vsi! in Pozdravljeni, svet!.
:::
::::
:::::

Seveda lahko kombiniramo različne vrste argumentov. Na primer, lahko definiramo ukaz z enim neobveznim in enim obveznim argumentom:

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\NewDocumentCommand{\Zap}{O{n}m}
{#2_{1}, \dots, #2_{#1}}
% V telesu dokumenta:
Nekatera zaporedja imajo veliko elementov:
$\Zap[1000]{a}$,
za večino pa sploh ne vemo,
koliko jih je:
$\Zap{b}$.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsMO-1.png
:label: fig:eg-ArgsMO-1
:alt: Odstavek z zaporedjema a_1 do a_1000 in b_1 do b_n.
:::
::::
:::::

Upoštevajte, da je vrstni red argumentov pomemben. Če je ukaz `\ukaz` definiran z vrsto argumentov `O{}m`, ga moramo klicati najprej z neobveznim argumentom (če ga želimo podati) in nato z obveznim. Klic `\ukaz[<neobvezni>]{<obvezni>}` je torej pravilen, klic `\ukaz{<obvezni>}[<neobvezni>]` pa ne.
Dobra praksa je, da najprej definiramo vse neobvezne argumente, nato pa obvezne.

Včasih želimo, da ukaz deluje drugače glede na to, ali je neobvezni argument podan ali ne. V tem primeru lahko uporabimo vrsto argumenta `o` in z ukazom `\IfValueTF` preverimo, ali je bil argument podan.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
%V preambuli:
\NewDocumentCommand{\ukaz}{o}
{
  \IfValueTF{#1}
  {Neobvezni argument je: \textbf{#1}} %Če je argument podan, vrni njegovo vrednost
  {Ni neobveznega argumenta.} %Če argument ni podan
}
% V telesu dokumenta:
 \ukaz
 \ukaz[Podan argument]
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsMo-2.png
:label: fig:eg-ArgsMo-2
:alt: Dva stavka, Ni neobveznega argumenta. in Neobvezni argument je: Podan argument, pri čemer je Podan argument krepko.
:::
::::
:::::

Namesto ukaza `\IfValueTF` lahko uporabimo tudi ukaz `\IfValueT`, če želimo izvesti dejanje samo takrat, ko je argument podan, ali ukaz `\IfValueF`, če želimo izvesti dejanje samo takrat, ko argument ni podan. Uporabimo lahko tudi ukaze `\IfNoValueTF`, `\IfNoValueT` in `\IfNoValueF`, ki delujejo nasprotno.

Če želimo, da ukaz sprejme neobvezni argument z določenimi ločevalniki, lahko uporabimo vrsto argumenta `D<levo><desno>{<privzeta_vrednost>}`.
Običajno kot ločevalnika uporabimo znaka `<` in `>`.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
% V preambuli:
\NewDocumentCommand{\zapLim}{D<>{1}O{n}m}
{#3_{#1}, \dots, #3_{#2}}
% V telesu dokumenta:
Večina zaporedij gre od $1$ do $n$:
$\zapLim{a}$,
vendar včasih želimo drugačen začetek:
$\zapLim<0>{a}$,
ali drugačen konec:
$\zapLim[500]{a}$,
ali pa kar oboje:
$\zapLim<5>[500]{a}$.
```
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsD-1.png
:label: fig:eg-ArgsD-1
:alt: Odstavek z zaporedji a_1 do a_n, a_0 do a_n, a_1 do a_500 in a_5 do a_500.
:::
::::
:::::

Če namesto `D<levo><desno>{<privzeta_vrednost>}` uporabimo `d<levo><desno>`, dobimo podoben učinek, vendar brez privzete vrednosti (tako kot pri `o`). V tem primeru moramo vedno preveriti, ali je bil argument podan, z ukazom `\IfValueTF` ali podobnimi.

Nazadnje lahko v nizu `<vrsta_argumentov>` uporabimo tudi znak `s`, s katerim definiramo preklopni argument oz. različico ukaza _z zvezdico_. V definiciji ukaza z ukazom `\IfBooleanTF` preverimo, ali je bil preklopni argument podan.

:::::{grid} 2 2 2 2
::::{card} LaTeX
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
::::

::::{card} PDF
:::{figure} ./img/05_eg-ArgsS-1.png
:label: fig:eg-ArgsS-1
:alt: Dve vrstici, Boštjan je rekel: "Danes je lep dan." in Ana je rekla: "Upam, da bo jutri tudi tako lep dan."
:::
::::
:::::

:::{exercise}
:label: ex_ukazi

1. Definirajte nov ukaz `\sporocilo`, ki sprejme en obvezni argument in en neobvezni argument (privzeta vrednost naj bo "Obvestilo"). Ukaz naj natisne neobvezni argument, nato znak `:` in nato obvezni argument v ležeči pisavi.
2. Ustvarite nov ukaz `\vektor`, ki sprejme en obvezni argument (za komponente vektorja) in en neobvezni argument (za dimenzijo vektorja). Če je dimenzija $n$ podana, naj ukaz natisne $n$-dimenzionalni vektor, sicer pa $3$-dimenzionalni vektor. Na primer, `\vektor[17]{v}` naj natisne $(v_{1}, \dots, v_{17})$, `\vektor{v}` pa $(v_{1}, v_{2}, v_{3})$.
3. Ustvarite nov ukaz `\rdeceAliModre`, ki sprejme en obvezni argument in en preklopni argument. Če je preklopni argument podan, naj ukaz natisne besedilo v rdeči barvi, sicer v modri.
4. Ustvarite nov ukaz `\myInt` za integral, ki sprejme dva obvezna argumenta: funkcijo in spremenljivko integracije; en neobvezni argument za spodnjo mejo (privzeta vrednost naj bo prazna) z ločevalnikoma `<` in `>`; in en neobvezni argument za zgornjo mejo (privzeta vrednost naj bo prazna) z ločevalnikoma `[` in `]`. Ukaz naj natisne integral z ustreznimi mejami, če so podane. Na primer, `\myInt<0>[1]{f(x)}{x}` naj natisne $\int_{0}^{1} f(x) \, dx$, `\myInt{f(x)}{x}` pa $\int f(x) \, dx$.
:::

:::{margin}
[Seznam nalog](#05_latexRazno_vaje)
:::

:::{solution} ex_ukazi
:class: tip dropdown

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
     {(#2_{1}, #2_{2}, #2_{3})} %Če argument ni podan, vrni 3-dimenzionalni vektor
   }
   ```

3. Definicija ukaza `\rdeceAliModre`:

   ```latex
   \NewDocumentCommand{\rdeceAliModre}{sm}
   {\IfBooleanTF{#1}
   {\textcolor{red}{#2}} %Če je podan preklopni argument, natisni rdeče
   {\textcolor{blue}{#2}} %Če preklopni argument ni podan, natisni modro
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

Nova okolja lahko definiramo z ukazom `\NewDocumentEnvironment`, ki ima podobno sintakso kot `\NewDocumentCommand`.

```latex
\NewDocumentEnvironment{<ime_okolja>}{<vrsta_argumentov>}
{<začetek_definicije>}
{<konec_definicije>}
```

- `<ime_okolja>`: ime novega okolja, ki ga želimo definirati.
- `<vrsta_argumentov>`: niz, ki določa vrste argumentov, ki jih okolje sprejema. Deluje skoraj enako kot pri ukazu `\NewDocumentCommand`.
- `<začetek_definicije>`: koda na začetku okolja, v kateri lahko uporabimo argumente okolja.
- `<konec_definicije>`: koda na koncu okolja.

Uporabo tega ukaza pojasnimo z naslednjimi primeri. Okolja `FlushLeft`, `Center` in `FlushRight` iz paketa `ragged2e` smo spoznali v poglavju [](./02_latexOsnovnaOkolja.md).

::::::{prf:example}
:label: eg_okolja_kralj-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
% V preambuli:
\usepackage{ragged2e}
\NewDocumentEnvironment{kralj}{}
{
  \begin{FlushLeft} \textbf{Poslušajte!}
  Njegovo veličanstvo, kralj Artur bo podal izjavo:
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
::::

::::{tab-item} PDF
:::{figure} ./img/05_eg-okolja-kralj-1.png
:label: fig:eg-okolja-kralj-1
:alt: Krepko Poslušajte! z uvodom o kralju Arturju, pod njim na sredini izjava v malih velikih črkah, desno spodaj zaključek Konec izjave. Hvala za vašo pozornost.
:::
::::
:::::

::::::

Definiramo lahko tudi okolja z argumenti. Na primer, lahko definiramo okolje `kraljIme`, ki sprejme en obvezni argument za ime kralja.

::::::{prf:example}
:label: eg_okolja_kralj-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
% V preambuli:
\usepackage{ragged2e}
\NewDocumentEnvironment{kraljIme}{m}
{
  \begin{FlushLeft} \textbf{Poslušajte!}
  Njegovo veličanstvo, kralj \emph{#1} bo podal izjavo:
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
::::

::::{tab-item} PDF
:::{figure} ./img/05_eg-okolja-kralj-2.png
:label: fig:eg-okolja-kralj-2
:alt: Enaka izjava kot v prejšnjem primeru, le da je ime Artur v uvodu ležeče, izjava pa se glasi Kralj vam želi lepe praznike.
:::
::::
:::::

::::::

Težava nastane, če želimo imeti različna uvoda in zaključka za kralja in kraljico. To lahko rešimo s preklopnim argumentom `s`.
V definiciji okolja z ukazom `\IfBooleanTF` preverimo, ali je bil preklopni argument podan; to lahko storimo v obeh delih definicije okolja.

:::{admonition} Pazite!
:class: warning
Za razliko od nekaterih drugih okolij LaTeX (npr. `align*`) zvezdico pri takem okolju zapišemo za zavitimi oklepaji z imenom okolja, tj. `\begin{kralji}*{Ime}` namesto `\begin{kralji*}{Ime}`. Na koncu okolja zvezdice ne pišemo: `\end{kralji}` je pravilen tudi za okolje z zvezdico.
:::

::::::{prf:example}
:label: eg_kralji

:::::{tab-set}
::::{tab-item} LaTeX
```latex
% V preambuli:
\usepackage{ragged2e}
\NewDocumentEnvironment{kralji}{sm}
{ % ob \begin{kralji}
  \IfBooleanTF{#1}{ %z zvezdico
    \begin{FlushLeft} \textbf{Poslušajte!} Njegovo veličanstvo, kralj \emph{#2} bo podal izjavo: \end{FlushLeft}\begin{Center} \scshape
  }
  { %brez zvezdice
    \begin{FlushLeft} \textbf{Poslušajte!} Njeno veličanstvo, kraljica \emph{#2} bo podala izjavo: \end{FlushLeft}\begin{Center} \scshape
  }
}
{ % ob \end{kralji}
  \IfBooleanTF{#1}
  { %z zvezdico
    \normalfont \end{Center}\begin{FlushRight} Konec izjave. Kralj je hvaležen za vašo pozornost.\end{FlushRight}
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
::::

::::{tab-item} PDF
:::{figure} ./img/05_eg-okolja-kralj-3.png
:label: fig:eg-okolja-kralj-3
:alt: Dve izjavi druga pod drugo: prva napove kralja Arturja in se konča z Kralj je hvaležen za vašo pozornost, druga napove kraljico Guinevere in se konča z Kraljica je hvaležna za vašo pozornost.
:::
::::
:::::

::::::

(05_latexRazno_vaje)=

## Naloge

Tukaj so naloge petega poglavja:

- [ ] [Naloga %s](#ex_input_include): Ukaza `\input` in `\include`.
- [ ] [Naloga %s](#ex-gradient): Mešanje barv.
- [ ] [Naloga %s](#ex_ukazi): Novi ukazi z `\NewDocumentCommand`.
