(06_latex_beamer)=

# Beamer: Predstavitve v LaTeXu

% https://www.overleaf.com/learn/latex/Beamer_Presentations%3A_A_Tutorial_for_Beginners_(Part_1)%E2%80%94Getting_Started

:::{admonition} Cilji poglavja
:class: tip
Po tem poglavju boste znali:

- s Beamerjem pripraviti predstavitev z naslovno drsnico in kazalom,
- predstavitev razdeliti na dele in razdelke,
- s specifikacijami prekrivanja vsebino drsnice prikazovati postopoma,
- na drsnice postaviti sezname, stolpce, tabele in bloke,
- izbrati temo in barvno shemo predstavitve.

Predvideni čas: 3 do 4 pedagoške ure.
:::

Beamer je razred dokumentov LaTeX za izdelavo drsnic ("slajdov").
Za izdelavo predstavitve z Beamerjem uporabimo razred `beamer` namesto `article`.
Nato za vsako posamezno drsnico uporabimo okolje `frame`.

:::{seealso} Glej tudi
V tem poglavju bomo predstavili osnovne koncepte in ukaze za ustvarjanje predstavitev z Beamerjem.
Za podrobnejše informacije in napredne funkcije si oglejte uradni [Beamer user guide](https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf).
:::

:::{admonition} Opozorilo!
:class: caution
Pri razredu `beamer` jezik dokumenta podamo kot možnost razreda (npr. `\documentclass[slovene]{beamer}`), paket `babel` pa naložimo brez možnosti (`\usepackage{babel}`). Beamer namreč besedila, kot sta _Theorem_ in _Definition_, prevaja s paketom `translator`, ta pa vidi le jezik, podan kot možnost razreda.

Upoštevajte, da standardna namestitev LaTeXa nima slovenskih prevodov za Beamer, zato vgrajena okolja, kot sta `theorem` in `definition`, izpišejo angleška imena. Najpreprosteje je, da za slovenske izreke definirate svoja okolja z ukazom `\newtheorem` (glej poglavje [](./04_latexMatematika.md)), npr. `\newtheorem{izrek}{Izrek}`.
:::

Ukaz `\frametitle{}` določi naslov drsnice, ukaz `\framesubtitle{}` pa njen podnaslov.
Krajša možnost je, da naslov in podnaslov drsnice podamo kot argumenta takoj za `\begin{frame}`; glejte [Primer %s](#eg_beamer_1).

::::::{prf:example}
:label: eg_beamer_1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}
\begin{document}
\begin{frame}
{Naslov drsnice}
{Podnaslov}
Vsebina drsnice.
\end{frame}
\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-beamer-1.pdf
:label: fig:06_eg-beamer-1
:alt: Drsnica z modrim naslovom Naslov drsnice, manjšim podnaslovom in besedilom Vsebina drsnice.

Primer drsnice z naslovom in podnaslovom.
:::
::::
:::::

::::::

## Pomembne drsnice

Podobno kot pri člankih lahko tudi pri predstavitvah z Beamerjem ustvarimo naslovno drsnico z ukazi `\title{}`, `\author{}` in `\date{}` v preambuli dokumenta.

Ukaz `\maketitle` v telesu dokumenta nato ustvari naslovno drsnico. Ukaz `\maketitle` je enakovreden

```latex
\begin{frame}
\titlepage
\end{frame}
```

V ukaz `\date` pogosto zapišemo tudi ime konference ali dogodka, kjer bo predstavitev prikazana.
V razredu `beamer` lahko uporabimo tudi ukaze `\institute{}`, `\subtitle{}` in `\titlegraphic{}` za dodajanje dodatnih informacij na naslovno drsnico; glejte [Primer %s](#eg_beamer-title-1).

::::::{prf:example}
:label: eg_beamer-title-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\title{Naslov predstavitve}
\author{Antonio Montero}
\date{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.pdf}}


\begin{document}
\maketitle
\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-beamer-title-1.pdf
:label: fig_06_eg-beamer-title-1
:alt: Naslovna drsnica z naslovom, podnaslovom, avtorjem, ustanovo, datumom in logotipom Univerze v Ljubljani.

Primer naslovne drsnice z dodatnimi informacijami.
:::
::::
:::::

::::::

Nekatere teme Beamerja (glej [](#beamer_teme)) dodajo informacije o avtorju in datumu na vsako drsnico.
Če je vsebina teh polj predolga, ne bo dovolj prostora. V tem primeru lahko ukazom dodamo neobvezni kratki argument (npr. `\author[<kratko>]{<dolgo>}`), ki se bo prikazal v glavi ali nogi drsnice; glejte [Primer %s](#eg_beamer-title-2).

::::::{prf:example}
:label: eg_beamer-title-2

:::::{tab-set}
::::{tab-item} LaTeX (dolgo)
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\usetheme{Boadilla}

\title{Naslov predstavitve}
\author{Antonio Montero}
\date{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.pdf}}


\begin{document}
\maketitle
\end{document}
```
::::

::::{tab-item} PDF (dolgo)
:::{figure} ./img/06_eg-beamer-title-2.pdf
:label: fig_06_eg-beamer-title-2
:alt: Naslovna drsnica s temo Boadilla, v kateri dolgi podatki o avtorju, ustanovi in datumu ne gredo v nogo.
:::
::::

::::{tab-item} LaTeX (kratko)
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\usetheme{Boadilla}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.pdf}}


\begin{document}
\maketitle
\end{document}
```
::::

::::{tab-item} PDF (kratko)
:::{figure} ./img/06_eg-beamer-title-3.pdf
:label: fig_06_eg-beamer-title-3
:alt: Naslovna drsnica s temo Boadilla, kjer so v nogi kratke oznake A. Montero (UL-PEF) in MatTeh -- Nov. 2025.
:::
::::
:::::

::::::

Ukaz `\titlegraphic{}` doda sliko na naslovno drsnico.
Če želimo dodati logotip na vse drsnice, lahko uporabimo ukaz `\logo{}` v preambuli dokumenta; glejte [Primer %s](#eg_beamer-logo).
Upoštevajte, da je položaj logotipa odvisen od uporabljene teme. Poleg tega nekatere teme ne prikažejo logotipa ali slike na naslovni drsnici.

::::::{prf:example}
:label: eg_beamer-logo

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

% \usetheme{Boadilla} % logotip spodaj desno
% \usetheme{PaloAlto} % logotip zgoraj levo
% \usetheme{Marburg}  % slika na naslovnici, logotipa ni
% \usetheme{Bergen}   % logotip spodaj desno, slike na naslovnici ni

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}


\begin{document}
\maketitle


\begin{frame}
{Naslov drsnice}
{Podnaslov}
Vsebina drsnice.
\end{frame}


\end{document}
```
::::

::::{tab-item} PDF (Boadilla)
:::{figure}
:label: boadilla
:align: left

![Naslovna drsnica s temo Boadilla.](./img/06_logo-boadilla-1.pdf)

![Drsnica s temo Boadilla z logotipom spodaj desno.](./img/06_logo-boadilla-2.pdf)

Tema Boadilla.
:::
::::

::::{tab-item} PDF (PaloAlto)
:::{figure}
:label: paloalto
:align: left

![Naslovna drsnica s temo PaloAlto.](./img/06_logo-paloalto-1.pdf)

![Drsnica s temo PaloAlto z logotipom zgoraj levo v stranski vrstici.](./img/06_logo-paloalto-2.pdf)

Tema PaloAlto.
:::
::::

::::{tab-item} PDF (Marburg)
:::{figure}
:label: marburg
:align: left

![Naslovna drsnica s temo Marburg in sliko.](./img/06_logo-marburg-1.pdf)

![Drsnica s temo Marburg brez logotipa.](./img/06_logo-marburg-2.pdf)

Tema Marburg.
:::
::::

::::{tab-item} PDF (Bergen)
:::{figure}
:label: bergen
:align: left

![Naslovna drsnica s temo Bergen brez slike.](./img/06_logo-bergen-1.pdf)

![Drsnica s temo Bergen z logotipom spodaj desno.](./img/06_logo-bergen-2.pdf)

Tema Bergen.
:::
::::
:::::

::::::

V razredu `beamer` lahko uporabimo tudi ukaze za _logične enote_, kot sta `\section{}` in `\subsection{}`, za organizacijo predstavitve.
Ti ukazi ne ustvarijo drsnic, vendar iz njih Beamer sestavi kazalo vsebine.
Kazalo natisnemo z ukazom `\tableofcontents` v okolju `frame`; glejte [Primer %s](#eg_beamer-toc-1).
Upoštevajte, da razdelek _Literatura_ ni vključen v kazalo, ker je definiran z ukazom `\section*{}`.

::::::{prf:example}
:label: eg_beamer-toc-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle

% Drsnica s kazalom
\begin{frame}{Kazalo}
  \tableofcontents
\end{frame}


% Logične enote
\section{Prvi razdelek}
    \subsection{Podrazdelek 1.1}
    \subsection{Podrazdelek 1.2}
    \subsection{Podrazdelek 1.3}
\section{Drugi razdelek}

\section{Zadnji razdelek}
\section*{Literatura}


\begin{frame}
{Naslov drsnice}
{Podnaslov}
Vsebina drsnice.
\end{frame}

\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-beamer-toc-1.pdf
:label: fig_06_eg-beamer-toc-1
:alt: Drsnica Kazalo s tremi razdelki in tremi podrazdelki prvega razdelka; razdelka Literatura v kazalu ni.

Primer drsnice s kazalom vsebine.
:::
::::
:::::

::::::

Če želimo kazalo prikazati postopoma, lahko ukazu `\tableofcontents` dodamo možnost `pausesections`; glejte [Primer %s](#eg_beamer-toc-2).

::::::{prf:example}
:label: eg_beamer-toc-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle

% Drsnica s kazalom
\begin{frame}{Kazalo}
  \tableofcontents[pausesections]
\end{frame}


% Logične enote
\section{Prvi razdelek}
    \subsection{Podrazdelek 1.1}
    \subsection{Podrazdelek 1.2}
    \subsection{Podrazdelek 1.3}
\section{Drugi razdelek}

\section{Zadnji razdelek}
\section*{Literatura}


\begin{frame}
{Naslov drsnice}
{Podnaslov}
Vsebina drsnice.
\end{frame}

\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-beamer-toc-1.gif
:label: fig_06_eg-beamer-toc-1b
:alt: Animacija drsnice s kazalom, v kateri se razdelki pojavljajo drug za drugim.

Uporaba možnosti `pausesections` za postopno prikazovanje kazala vsebine.
:::
::::
:::::

::::::

Ukazi, kot je `\section`, ne ustvarijo drsnic, vendar lahko z ukazom `\sectionpage` znotraj okolja `frame` ustvarimo drsnico, ki prikazuje naslov razdelka.

<!-- Na žalost, ukaz `\sectionpage` ni dela skupaj z paketom `babel`. -->

Druga možnost je, da kazalo ponovno prikažemo na začetku vsakega razdelka, da poslušalce spomnimo, kje smo.
To storimo z ukazoma `\AtBeginSection` in `\tableofcontents[currentsection]`; glejte [Primer %s](#eg_beamer-toc-3). Ukaz `\AtBeginSection` v preambuli ali pred prvim razdelkom poskrbi, da se njegova vsebina izvede ob vsakem ukazu `\section`; prazen neobvezni argument `[ ]` pomeni, da se pri razdelkih "z zvezdico" ne zgodi nič.
Če želimo, da se v kazalu prikažejo samo razdelki (brez podrazdelkov), ukazu `\tableofcontents` dodamo možnost `hideallsubsections`.

::::::{prf:example}
:label: eg_beamer-toc-3

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle

% Drsnica s kazalom
\begin{frame}{Kazalo}
  \tableofcontents
\end{frame}

\AtBeginSection[ ]
{
\begin{frame}{Kazalo}
    \tableofcontents[currentsection, hideallsubsections]
\end{frame}
}

% Logične enote
\section{Prvi razdelek}
\begin{frame}
{Drsnica razdelka 1}
Vse drsnice v razdelku 1.
\end{frame}
    \subsection{Podrazdelek 1.1}
    \subsection{Podrazdelek 1.2}
    \subsection{Podrazdelek 1.3}
\section{Drugi razdelek}
\begin{frame}
{Drsnica razdelka 2}
Vse drsnice v razdelku 2.
\end{frame}
\section{Zadnji razdelek}
\begin{frame}
{Drsnica razdelka 3}
Vse drsnice v razdelku 3.
\end{frame}
\section*{Literatura}


\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-beamer-toc-2.gif
:label: fig_06_eg-beamer-toc-2b
:alt: Animacija, v kateri se pred vsakim razdelkom pojavi kazalo s poudarjenim trenutnim razdelkom.

Kazalo vsebine na začetku vsakega razdelka.
:::
::::
:::::

::::::

Poleg ukazov `\section` in `\subsection` Beamer podpira tudi ukaz `\part{}` za večje logične enote.
Vsak del predstavitve (definiran z `\part{}`) lahko začnemo z drsnico, ki z ukazom `\partpage` v okolju `frame` prikaže naslov dela. Poleg tega ima lahko vsak del svoje kazalo vsebine, saj `\tableofcontents` prikaže le razdelke trenutnega dela; glejte [Primer %s](#eg_beamer-parts).

::::::{prf:example}
:label: eg_beamer-parts

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimiv podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle



% Logične enote
\part{Uvod}
\begin{frame}
  \partpage
\end{frame}

\begin{frame}
  \tableofcontents
\end{frame}

\section{Prvi razdelek}
    \subsection{Podrazdelek 1.1}
    \subsection{Podrazdelek 1.2}
    \subsection{Podrazdelek 1.3}
\section{Drugi razdelek}
\begin{frame}
  {Drsnica del I}
  Vse drsnice v delu Uvod.
\end{frame}

\part{Zaključek}
\begin{frame}
  \partpage
\end{frame}

\begin{frame}
  \tableofcontents
\end{frame}

\section{Zadnji razdelek}
\begin{frame}
  {Drsnica del II}
  Vse drsnice v delu Zaključek.
\end{frame}
\section*{Literatura}


\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-beamer-parts.gif
:label: fig_06_eg-beamer-parts
:alt: Animacija predstavitve z dvema deloma, Uvod in Zaključek, kjer ima vsak del svojo naslovno drsnico in svoje kazalo.

Uporaba logične enote `\part` v predstavitvi z Beamerjem.
:::
::::
:::::

::::::

(beamer_prekrivanje)=

## Specifikacije prekrivanja

Izhodna datoteka Beamerja je običajno datoteka PDF, ki je v principu statična. Beamer pa omogoča ustvarjanje dinamičnih učinkov z uporabo _specifikacij prekrivanja_ (ang. _overlay specifications_).

Predstavitev Beamer sestoji iz zaporedja drsnic, vsaka drsnica pa je lahko razdeljena na več slojev (ang. _slides_). V izhodni datoteki PDF vsak sloj ustreza eni strani. Specifikacije prekrivanja so ukazi, ki določajo, kateri deli vsebine so prikazani na določenem sloju.

Najlažji način za uporabo specifikacij prekrivanja je ukaz `\pause`, ki ustvari prekinitev na trenutnem mestu v drsnici.
Če v okolje `frame` dodamo ukaz `\pause`, prvi sloj drsnice prikaže vsebino do prve uporabe ukaza `\pause`, drugi sloj prikaže vsebino do druge uporabe ukaza `\pause` in tako naprej; glejte [Primer %s](#eg_beamer-pause).

::::::{prf:example}
:label: eg_beamer-pause

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Primer uporabe ukaza \texttt{\textbackslash pause}}
  To besedilo bo napisano od prvega sloja naprej, \pause
  to od drugega, \pause
  in to samo na tretjem in zadnjem sloju.
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-pause.gif
:label: fig-06_eg-pause
:alt: Animacija drsnice s tremi sloji, na kateri se stavek pojavlja po delih.

Uporaba ukaza `\pause`.
:::
::::
:::::

::::::

Ukaz `\pause` je enostaven za uporabo, vendar ponuja omejene možnosti prilagajanja. Za natančnejši nadzor nad tem, kdaj se posamezni deli vsebine prikažejo, lahko uporabimo _specifikacije prekrivanja_ v ukazih, kot so `\textbf`, `\textit`, `\textcolor` in drugi (glejte [Tabelo %s](#tab-prekrivanje-ukaze)).

::::{dropdown} Ukazi, ki podpirajo specifikacije prekrivanja

:::{list-table}
:label: tab-prekrivanje-ukaze
* - `\textbf`
  - `\textit`
  - `\textmd`
  - `\textnormal`
  - `\textrm`
* - `\textsc`
  - `\textsf`
  - `\textsl`
  - `\texttt`
  - `\textup`
* - `\emph`
  - `\color`
  - `\textcolor`
  - `\alert`
  - `\structure`
:::

Beamer uporablja ukaza `\alert` in `\structure` za poudarjanje besedila. Ukaz `\alert` običajno prikaže besedilo v rdeči barvi, medtem ko `\structure` uporabi barvo, ki jo tema uporablja za strukturne elemente, npr. naslove drsnic.
::::

Sintaksa za specifikacije prekrivanja je naslednja:

```latex
\ukaz<spec_prek>{<besedilo>}
```

kjer `\ukaz` predstavlja ukaz, ki ga želimo nadzorovati (npr. `\textbf`), `<spec_prek>` pa določa, na katerih slojih bo ukaz uporabljen. Na primer, `\textbf<2>{<besedilo>}` bo `<besedilo>` prikazalo krepko le na drugem sloju drsnice (ostali sloji bodo `<besedilo>` prikazali v običajnem slogu).

Specifikacija je lahko posamezen sloj (`<2>`), seznam slojev (`<2,4>`), obseg (`<2-4>`) ali obseg brez konca (`<2->`, tj. od drugega sloja naprej); glejte [Primer %s](#eg_beamer-overlay-1).

::::::{prf:example}
:label: eg_beamer-overlay-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Specifikacije prekrivanja}
  Tukaj je nekaj besedila, ki je vedno vidno.

  Naslednje številke kažejo, v katerem sloju smo:
  \alert<1>{1},
  \alert<2>{2},
  \alert<3>{3},
  \alert<4>{4},
  \alert<5>{5}.

  \textbf<2->{To besedilo je od drugega sloja naprej krepko.}

  \textit<3,5>{To besedilo je ležeče v tretjem in petem sloju.}

  \textcolor<1-2,4>{blue}{To besedilo je modro v prvem, drugem in četrtem sloju.}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-overlays-1.gif
:label: fig_06_eg-overlay
:alt: Animacija drsnice s petimi sloji, na kateri se spreminja, katera številka je rdeča in kateri stavki so krepki, ležeči ali modri.

Uporaba specifikacij prekrivanja.
:::
::::
:::::

::::::

Nekateri ukazi, kot je `\item` v okoljih `itemize` in `enumerate`, imajo vgrajeno podporo za specifikacije prekrivanja. Pri njih specifikacija določa, na katerih slojih je točka vidna; glejte [Primer %s](#eg_beamer-overlay-2).

::::::{prf:example}
:label: eg_beamer-overlay-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Specifikacije prekrivanja v okoljih}
  \begin{enumerate}
    \item<1-> Prva točka je vidna od prvega sloja naprej.
    \item<2,4> Druga točka je vidna v drugem in četrtem sloju.
    \item<2> Tretja točka je vidna samo v drugem sloju.
    \item<3-> Četrta točka je vidna od tretjega sloja naprej.
    \item<4-> Peta točka je vidna od četrtega sloja naprej.
  \end{enumerate}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-overlays-2.gif
:label: fig_beamer-overlay-2
:alt: Animacija oštevilčenega seznama s petimi točkami, ki se pojavljajo in izginjajo na štirih slojih.

Uporaba specifikacij prekrivanja v okoljih `enumerate` in `itemize`.
:::
::::
:::::

::::::

:::{exercise}
:label: ex_overlays-1

1. Napišite drsnico Beamer, ki prikazuje naslednji neurejeni seznam:

   - Ena
   - Dve
   - Tri
   - Štiri

2. Z uporabo specifikacij prekrivanja naredite naslednje:

   - Točke naj se pojavijo v obratnem vrstnem redu (najprej "Štiri", nato "Tri" ...). Ko so vidne vse štiri, naj ostanejo vidne še nekaj slojev, nato pa naj izginejo v obratnem vrstnem redu, kot so se pojavile (tako da je beseda "Štiri" prva, ki se prikaže, in zadnja, ki izgine).
   - Na slojih z lihim zaporednim številom naj bodo rdeče besede, ki predstavljajo soda števila ("Dve" in "Štiri"). Na slojih s sodim številom pa naj bodo rdeče besede, ki predstavljajo liha števila.
:::

:::{margin}
[Seznam nalog](#06_latexBeamer_vaje)
:::

:::{solution} ex_overlays-1
:class: tip dropdown
Možna rešitev:

```latex
\begin{frame}{Naloga 6.1}
  \begin{itemize}
    \item<4-8> \textcolor<4,6,8>{red}{Ena}
    \item<3-9> \textcolor<3,5,7,9>{red}{Dve}
    \item<2-10> \textcolor<2,4,6,8,10>{red}{Tri}
    \item<1-11> \textcolor<1,3,5,7,9,11>{red}{Štiri}
  \end{itemize}
\end{frame}
```

:::

Tudi ukaz `\includegraphics` podpira specifikacije prekrivanja, kar omogoča prikazovanje različnih slik na različnih slojih drsnice. To je uporabno za simulacijo animacij z zaporednim prikazovanjem slik;
glejte [Primer %s](#eg_beamer-overlay-3).

::::::{prf:example}
:label: eg_beamer-overlay-3

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Specifikacije prekrivanja s slikami}
  \begin{figure}
    % \centering %V Beamerju so slike privzeto poravnane na sredino.
    \includegraphics<1>[width=0.5\textwidth]{stick01.png}%
    \includegraphics<2>[width=0.5\textwidth]{stick02.png}%
    \includegraphics<3>[width=0.5\textwidth]{stick03.png}%
    \includegraphics<4>[width=0.5\textwidth]{stick04.png}%
    \includegraphics<5>[width=0.5\textwidth]{stick05.png}%
    \includegraphics<6>[width=0.5\textwidth]{stick06.png}%
    \includegraphics<7>[width=0.5\textwidth]{stick07.png}%
    \includegraphics<8>[width=0.5\textwidth]{stick08.png}%
    \caption{Lažna animacija}
  \end{figure}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-overlays-3.gif
:label: fig_06_eg-overlay-3
:alt: Animacija iz osmih slik paličaste figure, ki se premika.

Lažna animacija s specifikacijami prekrivanja.
:::
::::
:::::

::::::

Datoteka [`stick.zip`](./img/stick.zip) vsebuje slike, uporabljene v zgornjem primeru.

:::{dropdown} Paket `animate`
Za bolj gladke in prilagodljive animacije v predstavitvah Beamer lahko uporabimo paket [`animate`](https://ctan.org/pkg/animate). Ta paket omogoča vključevanje animacij, ki se samodejno predvajajo znotraj drsnic.
Paket `animate` ponuja ukaz `\animategraphics`, ki ima naslednjo sintakso:

```latex
\animategraphics[<možnosti>]{<fps>}{<osnovno_ime>}{<prva>}{<zadnja>}
```

kjer:

- `<možnosti>` so dodatne možnosti, kot sta `loop` (za neskončno ponavljanje) in `autoplay` (za samodejno predvajanje ob prikazu drsnice).
- `<fps>` določa število sličic na sekundo.
- `<osnovno_ime>` je skupni začetek imen datotek s slikami (brez številk in pripone).
- `<prva>` in `<zadnja>` določata obseg številk slik, ki se bodo uporabile v animaciji.

Na primer, zaporedje slik, ki smo ga uporabili v [Primeru %s](#eg_beamer-overlay-3), lahko s paketom `animate` vključimo kot animacijo takole:

```latex
% V preambuli
\usepackage{animate}

% V telesu dokumenta
\begin{frame}{Z uporabo paketa \texttt{animate}}
  \begin{figure}
    \centering
    \animategraphics[loop,autoplay,width=0.5\textwidth]{2}{stick0}{1}{8}
    \caption{Prava animacija s paketom \texttt{animate}.}
  \end{figure}
\end{frame}
```

Na žalost animacij ne podpirajo vsi pregledovalniki PDF (delujejo npr. v Adobe Acrobat Readerju, ne pa v brskalnikih in v Predogledu na macOS).
Najvarnejša možnost je uporaba "lažnih animacij", kot je prikazano v [Primeru %s](#eg_beamer-overlay-3).

:::

Naslednji trije ukazi delujejo zelo podobno. Prikažejo `<besedilo>` v skladu z `<spec_prek>`. Razlika med njimi je v tem, kako se obnašajo, ko besedilo ni prikazano.

- `\only<spec_prek>{<besedilo>}`: Prikaže `<besedilo>` samo na slojih, določenih z `<spec_prek>`. Na drugih slojih `<besedilo>` ni prisotno (ne zavzame prostora).
- `\visible<spec_prek>{<besedilo>}`: Prikaže `<besedilo>` na slojih, določenih z `<spec_prek>`, na drugih slojih pa ohrani prostor, ki ga `<besedilo>` zavzema (vendar je besedilo **nevidno**).
- `\uncover<spec_prek>{<besedilo>}`: Prikaže `<besedilo>` na slojih, določenih z `<spec_prek>`, na drugih slojih pa ohrani prostor, ki ga `<besedilo>` zavzema (vendar je besedilo **prekrito**).

Razlika med `\visible` in `\uncover` je v tem, kako je prikazano _prekrito_ besedilo. To nadzorujemo z ukazom `\setbeamercovered{<možnost>}` v preambuli dokumenta. Možnosti vključujejo:

- `invisible`: Prekrito besedilo je popolnoma nevidno (privzeta možnost). Takrat se `\visible` in `\uncover` obnašata enako.
- `transparent=<neprosojnost>`: Prekrito besedilo je prikazano prosojno; `<neprosojnost>` je vrednost med `0` (popolnoma prozorno) in `100` (popolnoma neprozorno), privzeta vrednost je `15`.
- `dynamic`: Prekrito besedilo je prosojno, vendar na dinamičen način: dlje kot je do sloja, na katerem se besedilo prikaže, bolj je prosojno.

Glejte [Primer %s](#eg_overlays-only-1).

::::::{prf:example}
:label: eg_overlays-only-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
% V preambuli
\setbeamercovered{transparent}

% V telesu dokumenta
\begin{frame}{\texttt{\textbackslash only}, \texttt{\textbackslash visible} in \texttt{\textbackslash uncover}}

  Smo na sloju: \alert<1>{1}, \alert<2>{2}, \alert<3>{3}, \alert<4>{4}, \alert<5>{5}, \alert<6>{6}, \alert<7>{7}, \alert<8>{8}.


  Moja najgloblja skrivnost je prikazana samo na drugem in sedmem sloju:
  \only<2,7>{ \textcolor{blue}{skrivnost!}}
  zanjo pa ni rezerviranega prostora.

  Sporočilo z drugega planeta je tukaj:
  \visible<4->{Izbranci so resnični, vendar živijo zelo daleč}.
  V prihodnosti ga bomo lahko prebrali (od sloja 4 naprej).

  Sporočilo iz podzemlja ni povsem nevidno:
  \uncover<6->{Pozdravljeni! Sem duh, vendar sem prijazen.}
  Bojim se duhov!

\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-overlays-only-1.gif
:label: fig_06_eg-overlays-only-1
:alt: Animacija drsnice z osmimi sloji: skrivnost se pojavi na drugem in sedmem sloju, sporočilo z drugega planeta je nevidno do četrtega sloja, sporočilo iz podzemlja pa je do šestega sloja prosojno.

Uporaba ukazov `\only`, `\visible` in `\uncover`.
:::
::::
:::::

::::::

Obstajajo še drugi ukazi za specifikacije prekrivanja, kot so:

- `\invisible<spec_prek>{<besedilo>}`: Nasprotje ukaza `\visible`. Na slojih, določenih z `<spec_prek>`, je `<besedilo>` nevidno (prostor zanj ostane), na drugih slojih pa je prikazano.
- `\alt<spec_prek>{<besedilo1>}{<besedilo2>}`: Prikaže `<besedilo1>` na slojih, določenih z `<spec_prek>`, in `<besedilo2>` na ostalih slojih.
- `\temporal<spec_prek>{<besedilo1>}{<besedilo2>}{<besedilo3>}`: Prikaže `<besedilo1>` na slojih pred prvim slojem, določenim z `<spec_prek>`, `<besedilo2>` na slojih, določenih z `<spec_prek>`, in `<besedilo3>` na slojih po zadnjem sloju, določenem z `<spec_prek>`.

V [Primeru %s](#eg_overlays-only-2) so prikazani ti ukazi v akciji.

::::::{prf:example}
:label: eg_overlays-only-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{\texttt{\textbackslash invisible}, \texttt{\textbackslash alt} in \texttt{\textbackslash temporal}}

  Smo na sloju: \alert<1>{1}, \alert<2>{2}, \alert<3>{3}, \alert<4>{4}, \alert<5>{5}, \alert<6>{6}, \alert<7>{7}, \alert<8>{8}.

  Tukaj je nekaj besedila, ki je nevidno na slojih 3 in 5:
  \structure{\invisible<3,5>{To besedilo je nevidno na slojih 3 in 5.}}

  Tukaj je nekaj besedila, ki se spreminja glede na sloj:
  \alt<2,4,6>{\textcolor{blue}{To je besedilo za sloje 2, 4 in 6.}}
  {\textcolor{red}{To je besedilo za vse ostale sloje.}}

  Tukaj je nekaj besedila, ki se spreminja glede na čas:
  \temporal<3-5>{\textcolor{red}{To je besedilo pred slojem 3.}}
  {\textcolor{blue}{To je besedilo na slojih od 3 do 5.}}
  {\textcolor{green}{To je besedilo po sloju 5.}}

\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg-overlays-only-2.gif
:label: fig_06_eg-overlays-only-2
:alt: Animacija drsnice z osmimi sloji, na kateri en stavek izgine na slojih 3 in 5, drugi menja modro in rdeče besedilo, tretji pa se spremeni pred, med in po slojih od 3 do 5.

Uporaba ukazov `\invisible`, `\alt` in `\temporal`.
:::
::::
:::::

::::::

Tudi nekatera okolja v Beamerju podpirajo specifikacije prekrivanja.
Sintaksa je običajno `\begin{<okolje>}<spec_prek>`, rezultat pa je, da se celotno okolje prikaže samo na slojih, določenih z `<spec_prek>`.

Vsak od ukazov `\only`, `\alt`, `\visible`, `\uncover` in `\invisible` ima svojo različico v obliki okolja, in sicer `onlyenv`, `altenv`, `visibleenv`, `uncoverenv` in `invisibleenv`.
Vsa razen `altenv` imajo sintakso

```latex
\begin{<okolje>}<spec_prek>
  <vsebina>
\end{<okolje>}
```

in delujejo podobno kot ustrezni ukazi.
Okolje `altenv` ima sintakso

```latex
\begin{altenv}<spec_prek>
{<začetek>}{<konec>}
{<alternativni_začetek>}{<alternativni_konec>}
  <vsebina>
\end{altenv}
```

Na slojih, določenih z `<spec_prek>`, se `<vsebina>` prikaže med `<začetek>` in `<konec>`, na ostalih slojih pa med `<alternativni_začetek>` in `<alternativni_konec>`.

Z ukazi, kot je `\only`, lahko vsebino drsnice spreminjamo od sloja do sloja, npr.

```latex
  \only<1>{Besedilo za prvi sloj.}
  \only<2>{Besedilo za drugi sloj, ki je lahko daljše. Če je besedilo daljše, se okvir prilagodi višini vsebine.}
  \only<3>{Tretji sloj ima spet krajše besedilo.}
```

Težava pri tem pristopu je, da lahko pride do nadležnih razlik v višini
elementov, kar lahko povzroči, da se celotna drsnica "trese" od sloja do sloja.

Za rešitev tega problema lahko uporabimo okolje `overlayarea`, ki ima naslednjo sintakso:

```latex
\begin{overlayarea}{<širina>}{<višina>}
  <vsebina>
\end{overlayarea}
```

To okolje ustvari območje velikosti `<širina>` krat `<višina>`, v katerem se vsebina lahko spreminja, ne da bi vplivala na postavitev preostale drsnice; glejte [Primer %s](#eg_overlayarea).

::::::{prf:example}
:label: eg_overlayarea

:::::{tab-set}
::::{tab-item} LaTeX (brez)
```latex
\begin{frame}{\texttt{overlayarea}}
  \begin{center}
    \includegraphics[width=\linewidth, height=0.2\textheight]{example-image-a}
  \end{center}


  \only<1>{Besedilo za prvi sloj.}
  \only<2>{Besedilo za drugi sloj, ki je lahko daljše. Če je besedilo daljše, se okvir prilagodi višini vsebine.}
  \only<3>{Tretji sloj ima spet krajše besedilo.}

  \begin{center}
    \includegraphics[width=\linewidth,height=0.1\textheight]{example-image-b}
  \end{center}
  \visible<1-4>{\textcolor{red}{Ostali elementi niso stabilni.}}

\end{frame}
```
::::

::::{tab-item} PDF (brez)
:::{figure} ./img/06_eg-overlayarea-1.gif
:label: fig_06_overlayarea-1
:alt: Animacija drsnice, na kateri se slika B in rdeče besedilo pod njo premikata gor in dol, ker se dolžina besedila nad njima spreminja.

Brez okolja `overlayarea`.
:::
::::

::::{tab-item} LaTeX (z overlayarea)
```latex
\begin{frame}{\texttt{overlayarea}}
  \begin{center}
    \includegraphics[width=\linewidth, height=0.2\textheight]{example-image-a}
  \end{center}

\begin{overlayarea}{\linewidth}{0.15\textheight}
  \only<1>{Besedilo za prvi sloj.}
  \only<2>{Besedilo za drugi sloj, ki je lahko daljše. Če je besedilo daljše, se okvir prilagodi višini vsebine.}
  \only<3>{Tretji sloj ima spet krajše besedilo.}
\end{overlayarea}

  \begin{center}
    \includegraphics[width=\linewidth,height=0.1\textheight]{example-image-b}
  \end{center}
  \visible<1-4>{Ostali elementi \alert{so} zdaj stabilni.}
\end{frame}
```
::::

::::{tab-item} PDF (z overlayarea)
:::{figure} ./img/06_eg-overlayarea-2.gif
:label: fig_06_overlayarea-2
:alt: Animacija drsnice, na kateri se besedilo v sredini spreminja, slika B in besedilo pod njo pa ostaneta na istem mestu.

Z okoljem `overlayarea`.
:::
::::
:::::

::::::

(beamer_vsebina)=

## Vsebina predstavitve

### Seznami

Navadna okolja za sezname, kot so `itemize`, `enumerate` in `description`, so podprta tudi v Beamerju.

Seveda lahko za postopno prikazovanje elementov seznama uporabimo tudi ukaz `\pause` ali specifikacije prekrivanja, kot je prikazano v [Primeru %s](#eg_beamer-overlay-2).
Druga možnost je specifikacija `[<+->]` kot neobvezni argument okolja seznama. Znak `+` pomeni "naslednji sloj", zato se vsaka točka prikaže na svojem sloju in ostane vidna do konca drsnice; glejte [Primer %s](#eg_beamer-lists-1).

V tem primeru pokažemo tudi uporabo ukaza `\vspace{<višina>}`, ki ustvari navpični prostor med seznamoma, in ukaza `\vfill`, ki zapolni ves preostali navpični prostor in tako zadnji seznam potisne na dno drsnice.

::::::{prf:example}
:label: eg_beamer-lists-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}
  {Seznami v Beamerju}
  \begin{itemize}[<+->]
    \item Točkasti seznam
    \item Druga točka
  \end{itemize}
  \vspace{1cm}
  \begin{enumerate}[<+->]
    \item Prva točka urejenega seznama.
    \item Druga točka urejenega seznama.
  \end{enumerate}
  \vfill
  \begin{description}[<+->]
    \item[Itemize] Okolje za neurejene sezname.
    \item[Enumerate] Okolje za oštevilčene sezname.
    \item[Description] Okolje za sezname z opisi.
  \end{description}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg_beamer-lists-1.gif
:label: fig_06_eg_beamer-lists-1
:alt: Animacija drsnice, na kateri se točke treh seznamov pojavljajo ena za drugo; opisni seznam je na dnu drsnice.

Seznami v Beamerju z uporabo specifikacij prekrivanja.
:::
::::
:::::

::::::

Včasih je seznam predolg, da bi ga lahko prikazali na eni drsnici. Takrat ga razdelimo na več drsnic, številčenje pa nadaljujemo, kot prikazuje [Primer %s](#eg_beamer-lists-2).

::::::{prf:example}
:label: eg_beamer-lists-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
% V preambuli definiramo števec za nadaljevanje seznama
\newcounter{currentenumi}
% V telesu dokumenta
\begin{frame}{Predolgi seznami}{Prva drsnica}
  \begin{enumerate}[<+->]
    \item Točka 1.
    \item Točka 2.
    \item Točka 3.
    % Shranimo trenutni števec
    \setcounter{currentenumi}{\value{enumi}}
  \end{enumerate}
\end{frame}
\begin{frame}{Predolgi seznami}{Druga drsnica}
  \begin{enumerate}[<+->]
    % Nadaljujemo s shranjenim števcem
    \setcounter{enumi}{\value{currentenumi}}
    \item Točka 4.
    \item Točka 5.
  \end{enumerate}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg_beamer-lists-2.gif
:label: fig_06_eg_beamer-lists-2
:alt: Animacija dveh drsnic, na prvi se pojavijo točke od 1 do 3, na drugi pa točki 4 in 5.

Predolgi seznami, razdeljeni na več drsnic.
:::
::::
:::::

::::::

### Stolpci

Beamer omogoča ustvarjanje stolpcev z okoljem `columns`. Vsak stolpec je definiran z okoljem `column`, ki ima naslednjo sintakso:

```latex
\begin{columns}
  \begin{column}<spec_prek>{<širina>}
    <vsebina stolpca 1>
  \end{column}
  \begin{column}<spec_prek>{<širina>}
    <vsebina stolpca 2>
  \end{column}
  ...
\end{columns}
```

kjer `<širina>` določa širino stolpca (lahko je absolutna vrednost, npr. `5cm`, ali relativna vrednost, npr. `0.5\textwidth`), `<spec_prek>` pa je neobvezna specifikacija prekrivanja, ki določa, na katerih slojih bo stolpec prikazan.
Namesto okolja `column` lahko uporabimo tudi krajši ukaz `\column{<širina>}`, ki stolpec začne, konča pa se ob naslednjem ukazu `\column` ali na koncu okolja `columns`; glejte [Primer %s](#eg_beamer-columns-1).

::::::{prf:example}
:label: eg_beamer-columns-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Stolpci v Beamerju}
  \begin{columns}
  \column{0.6\textwidth}<2>
      \centering
      Ta stolpec zavzema $60\%$ širine besedila in je viden na drugem sloju.
  \column{0.4\textwidth}<1->
      \centering
      Ta stolpec zavzema $40\%$ širine besedila in je viden na vseh slojih.
  \end{columns}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg_beamer-columns-1.gif
:label: fig_06_eg_beamer-columns-1
:alt: Animacija dveh slojev: na prvem je viden le desni stolpec, na drugem tudi levi, širši stolpec.

Stolpci v Beamerju z uporabo specifikacij prekrivanja.
:::
::::
:::::

::::::

Ta pristop lahko uporabimo za ustvarjanje drsnic z besedilom na eni strani in sliko na drugi strani; glejte [Primer %s](#eg_beamer-columns-2).

::::::{prf:example}
:label: eg_beamer-columns-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Besedilo in slika}
  \begin{columns}
    \begin{column}{0.4\textwidth}
      Tukaj je nekaj besedila na levi strani.
      Morda nekaj več besedila, da zapolnimo prostor.
    \end{column}
    \begin{column}{0.6\textwidth}
      \begin{figure}
      \centering
      \includegraphics[width=\textwidth]{example-image-a}
      \caption{Primer slike na desni strani.}
      \end{figure}
    \end{column}
  \end{columns}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg_beamer-columns-2.pdf
:label: fig_06_eg_beamer-columns-2
:alt: Drsnica z besedilom v levem stolpcu in sliko s podnapisom v desnem.

Drsnica z besedilom in sliko v stolpcih.
:::
::::
:::::

::::::

### Tabele

Na splošno večina ukazov za tabele, ki smo jih opisali v poglavju [](./02_latexOsnovnaOkolja.md), deluje tudi v Beamerju, če naložimo ustrezne pakete (npr. `booktabs`, `array`, `multirow`).

Poleg tega lahko uporabimo specifikacije prekrivanja za postopno prikazovanje vrstic ali stolpcev v tabeli; glejte [Primer %s](#eg_beamer-tables-1).

::::::{prf:example}
:label: eg_beamer-tables-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Tabele v Beamerju}
  \begin{table}
  \begin{tabular}{ l c l }
    \toprule
    Oseba & Obraz & Razpoloženje\\
    \midrule %\pause
    \visible<2->{Jaz & :) & Vesel} \\
    \visible<3->{Vi & :/ & Zaskrbljen} \\
    \visible<4->
    {Vaš partner} & \visible<5->{:(} & \visible<6>{Žalosten} \\
    \bottomrule
    \end{tabular}
    \caption{Primer preproste tabele v Beamerju.}
  \end{table}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg_beamer-tables-1.gif
:label: fig_06_eg_beamer-tables-1
:alt: Animacija tabele s tremi stolpci, v kateri se vrstice in zadnji vrstici celice pojavljajo postopoma.

Tabele v Beamerju z uporabo specifikacij prekrivanja.
:::
::::
:::::

::::::

Če je tabela preširoka ali previsoka za drsnico, lahko uporabimo ukaz `\resizebox` iz paketa `graphicx`. Sintaksa je `\resizebox{<širina>}{<višina>}{<vsebina>}`, kjer lahko za eno od mer napišemo `!`, da se prilagodi samodejno in ohrani razmerje.
Upoštevajte, da `\resizebox` pomanjša tudi pisavo, zato naj bo to zadnja možnost: pogosto je bolje tabelo skrajšati ali razdeliti na več drsnic. Glejte [Primer %s](#eg_beamer-tables-2).

::::::{prf:example}
:label: eg_beamer-tables-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Velike tabele v Beamerju}
  \begin{table}
  \resizebox{\textwidth}{!}
  {
  \begin{tabular}{ccccccccccccc}
  \toprule
      To & je & tabela, & ki & je & preširoka & za & drsnico. & Nimamo & dovolj & prostora & 12 & 13\\
  \midrule
      a & b & c & d & e & f & g & h & i & j & k & l & m\\
  \bottomrule
  \end{tabular}
  }
  \caption{Primer tabele, ki presega širino drsnice v Beamerju.}
  \end{table}
\end{frame}
```
::::

::::{tab-item} PDF (brez `\resizebox`)
:::{figure} ./img/06_eg_beamer-tables-2-1.pdf
:label: fig_06_eg_beamer-tables-2-1
:alt: Drsnica s tabelo, ki je širša od drsnice in sega čez desni rob.

Ista tabela brez ukaza `\resizebox` presega širino drsnice.
:::
::::

::::{tab-item} PDF (z `\resizebox`)
:::{figure} ./img/06_eg_beamer-tables-2-2.pdf
:label: fig_06_eg_beamer-tables-2-2
:alt: Drsnica s tabelo, pomanjšano na širino drsnice, z zelo drobno pisavo.

Z ukazom `\resizebox` tabelo prilagodimo širini drsnice.
:::
::::
:::::

::::::

### Bloki

Beamer ponuja okolje `block` za ustvarjanje poudarjenih vsebinskih blokov znotraj drsnic. Sintaksa je naslednja:

```latex
\begin{block}{<naslov bloka>}
  <vsebina bloka>
\end{block}
```

Poleg tega Beamer ponuja posebni vrsti blokov, `exampleblock` in `alertblock`, ki imata drugačen slog za poudarjanje vsebine. Slog blokov je odvisen od izbrane teme Beamerja; glejte [Primer %s](#eg_beamer-blocks-1).

::::::{prf:example}
:label: eg_beamer-blocks-1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Bloki}
  \begin{block}{Navaden blok}
    To je vsebina navadnega bloka.
  \end{block}
  \begin{exampleblock}{Blok s primerom}
    To je vsebina bloka s primerom.
  \end{exampleblock}
  \begin{alertblock}{Blok z opozorilom}
    To je vsebina bloka z opozorilom.
  \end{alertblock}
\end{frame}
```
::::

::::{tab-item} PDF (privzeta tema)
:::{figure} ./img/06_eg_bloki-1-1.pdf
:label: fig_06_eg_bloki-1-1
:alt: Drsnica s tremi bloki s privzeto temo, kjer so naslovi blokov modri, zeleni in rdeči.

Bloki v Beamerju s privzeto temo.
:::
::::

::::{tab-item} PDF (Boadilla)
:::{figure} ./img/06_eg_bloki-1-2.pdf
:label: fig_06_eg_bloki-1-2
:alt: Drsnica s tremi bloki s temo Boadilla, kjer ima vsak blok barvno ozadje naslova in senčeno vsebino.

Bloki v Beamerju s temo Boadilla.
:::
::::
:::::

::::::

Tudi okolja za teoreme, kot so `theorem`, `lemma`, `definition` in `proof`, so v Beamerju že definirana in imajo podoben slog kot bloki; glejte [Primer %s](#eg_beamer-blocks-2).
Na sliki so imena okolij slovenska, ker smo predstavitev prevedli s slovenskimi prevodi za Beamer. V standardni namestitvi LaTeXa bodo imena angleška (_Theorem_, _Lemma_ ...), kot je opisano v opozorilu na začetku poglavja.

::::::{prf:example}
:label: eg_beamer-blocks-2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{frame}{Bloki za teoreme}
  \begin{theorem}[Pitagorov izrek]
    V pravokotnem trikotniku velja: $a^2 + b^2 = c^2$.
  \end{theorem}

  \begin{lemma}
    To je primer leme.
  \end{lemma}

  \begin{proof}
    To je primer dokaza.
  \end{proof}
\end{frame}
```
::::

::::{tab-item} PDF
:::{figure} ./img/06_eg_bloki-2.pdf
:label: fig_06_eg_bloki-2
:alt: Drsnica z blokoma Izrek (Pitagorov izrek) in Lema ter dokazom, ki se konča s kvadratkom.
:::
::::
:::::

::::::

Svoja okolja za teoreme lahko definiramo z ukazom `\newtheorem` natanko tako kot v običajnem LaTeXu (glej poglavje [](./04_latexMatematika.md)).

(beamer_teme)=

## Teme in barvne sheme

Beamer ponuja različne teme in barvne sheme za prilagoditev videza predstavitve. Teme določajo splošno postavitev in slog drsnic ter barvno paleto.

Videz predstavitve v Beamerju lahko prilagajamo s štirimi vrstami tem:

- Barvna tema (ang. _color theme_): določa barvno shemo predstavitve.
- Tema pisave (ang. _font theme_): določa slog pisave.
- Notranja tema (ang. _inner theme_): določa slog notranjih elementov, kot so seznami, bloki, kazalo itd.
- Zunanja tema (ang. _outer theme_): določa slog zunanjih elementov, kot so glava, noga, stranska vrstica itd.

Poleg teh štirih vrst lahko izberemo tudi celotno temo, ki združuje vse te vidike. Največkrat je dovolj, da izberemo samo temo, saj ta samodejno nastavi ustrezno barvno shemo, pisave ter notranjo in zunanjo temo. Če želimo, lahko posamezne vidike nato še dodatno prilagodimo.

Teme se naložijo z ukazom `\usetheme{<ime_teme>}`, posamezne vrste tem pa z ukazi

- `\usecolortheme{<ime_barvne_teme>}`
- `\usefonttheme{<ime_teme_pisave>}`
- `\useinnertheme{<ime_notranje_teme>}`
- `\useoutertheme{<ime_zunanje_teme>}`

Število možnosti za te ukaze je ogromno in nemogoče je prikazati vse zanimive primere.
Lahko pa ponudimo zunanje vire za raziskovanje različnih tem.

- [Beamer Theme Matrix](https://hartwork.org/beamer-theme-matrix/): interaktivno orodje za raziskovanje različnih kombinacij tem in barvnih shem v Beamerju.
- [Beamer Theme Gallery](https://deic.uab.es/~iblanes/beamer_gallery/index.html): galerija različnih tem Beamer, tem pisave in barvnih tem.
- [Beamer User Guide](https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf): III. del vodiča za uporabnike Beamerja vsebuje podrobne informacije o temah in barvnih shemah.
- [Overleaf beamer templates](https://www.overleaf.com/gallery/tagged/beamer): sodobne teme Beamer na Overleafu.

(06_latexBeamer_vaje)=

## Naloge

Tukaj so naloge šestega poglavja:

- [ ] [Naloga %s](#ex_overlays-1): Specifikacije prekrivanja v seznamu.

:::{exercise} Domača naloga
:label: dn_beamer
:nonumber:

1. Ustvarite predstavitev Beamer, ki ima od 5 do 10 drsnic.
2. Vsebina predstavitve naj bo vaša izbira.
3. Vključite različne elemente, kot so seznami, tabele, slike, bloki itd. (ni treba vključiti vseh elementov, opisanih v tem poglavju).
4. Uporabite specifikacije prekrivanja za postopno prikazovanje vsebine na drsnicah.
5. Ne bojte se raziskovati različnih tem za svojo predstavitev.
6. Domačo nalogo oddajte kot datoteko `.zip` prek spletne učilnice. Če ne veste, kako pridobiti datoteko `.zip` iz Overleafa, poglejte [](./B_izvozIzOverleaf.md).
:::
