(06_latex_beamer)=

# Beamer: Prestavitve v LaTeXu

% https://www.overleaf.com/learn/latex/Beamer_Presentations%3A_A_Tutorial_for_Beginners_(Part_1)%E2%80%94Getting_Started

Beamer je LaTeX razširitev za izdelavo drsnic ("slajdov").
Za izdelavo predstavitve z Beamerjem uporabimo razred `beamer` namesto `article`.
Nato uporabimo okolja `frame` za vsak posamezen diapozitiv.

:::{seealso} Glej tudi: Beamer uporabniški vodič.
:class: seealso
V tem poglaviu bomo predstavili osnovne koncepte in ukaze za ustvarjanje predstavitev z Beamerjem.
Za podrobnejše informacije in napredne funkcije si oglejte uradno [Beamer user guide](https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf).
:::

Ukaz `\frametitle{}` določi naslov drsnice. Lahko tudi uporabimo ukaz `framesubtitle{}` za podnaslov drsnice.
Krajša možnost je, da naslov oz. podnaslov drsnice podamo kot možnost okolja `frame`; [Primer %s](#eg_beamer_1).

:::{prf:example}
:label: eg_beamer_1

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}
\begin{document}
\begin{frame}
{Naslov drsnice}
{Podnaslov}
Vsebina drsnice.
\end{frame}
\end{document}
```
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-1.pdf
:name: fig:06_eg-beamer-1
```
````
`````

:::

## Pomembne drsnice

Podobno kot pri člankih lahko tudi pri Beamer predstavitvah ustvarimo naslovni diapozitiv z uporabo ukazov `\title{}`, `\author{}` in `\date{}` v preambuli dokumenta.

Zdaj ukaz `\maketitle` v telesu dokumenta ustvari naslovni diapozitiv. Ukaz `\maketitle` je enakomerno kot

```latex
\begin{frame}
\titlepage
\end{frame}
```

Običajno ukaz `\date` nastavimo na ime konference ali dogodek, kjer bo predstavitev prikazana.
V razreed beamer lahko tudi uporabljamo ukaze `\institute{}`, `\subtitle{}` in `\titlegraphic{}` za dodajanje dodatnih informacij na naslovno drsnico; poglejte [Primer %s](#eg_beamer-title-1).

:::{prf:example}
:label: eg_beamer-title-1

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}

\title{Naslov predstavitve}
\author{Antonio Montero}
\date{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
\institute{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.pdf}}


\begin{document}
\maketitle
\end{document}
```
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-title-1.pdf
```
````
`````

:::

Nekatere teme Bemerja (glej [](#beamer_teme)) dodajo informacije o avtorju in datumu na vsako drsnico.
Če je vsebina teh polj predolga, ne bo dovolj prostora; v tem primeru lahko dodamo neobvezni kratek argument v ukaze (npr. `\author[<kratek>]{<dolg>}`), ki se bo prikazal v glavi ali nogi drsnice, poglejte [Primer %s](#eg_beamer-title-2).

:::{prf:example}
:label: eg_beamer-title-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}

\usetheme{Boadilla}

\title{Naslov predstavitve}
\author{Antonio Montero}
\date{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
\institute{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.pdf}}


\begin{document}
\maketitle
\end{document}
```
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-title-2.pdf
```
````
````{tab-item} LaTeX
```latex
\documentclass{beamer}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh - Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.pdf}}


\begin{document}
\maketitle
\end{document}
```
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-title-3.pdf
```
````
`````

:::

Ukaz `\titlegraphic{}` doda sliko na naslovno drsnico.
Če želimo dodati logotip na vse drsnice, lahko uporabimo ukaz `\logo{}` v preambuli dokumenta, poglejte [Primer %s](#eg_beamer-logo).
Upoštevajte, da je pozicija logotipa odvisna od uporabljene teme. Poleg tega, nekatere teme ne podpirajo logotipov/grafik na naslovni drsnici.

:::{prf:example}
:label: eg_beamer-logo

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}
\usepackage[slovene]{babel}

% \usetheme{Boadilla} %logo na spodaj desno
% \usetheme{PaloAlto} %logo na zgoraj levo
% \usetheme{Marburg} %titlegraphi, ampak nima logotipa
%\usetheme{Bergen} %logo na spodaj desno, nima graphic na naslovnici

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh - Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
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
````
````{tab-item} PDF (Boadilla)
```{figure}
:label: boadilla
:align: left

![Boadilla - Naslov](./img/06_logo-boadilla-1.pdf)

![Boadilla - Drsnica](./img/06_logo-boadilla-2.pdf)

Boadilla tema.
```
````
````{tab-item} PDF (PaloAlto)
```{figure}
:label: paloalto
:align: left

![PaloAlto - Naslov](./img/06_logo-paloalto-1.pdf)

![PaloAlto - Drsnica](./img/06_logo-paloalto-2.pdf)

PaloAlto tema.
```
````
````{tab-item} PDF (Marburg)
```{figure}
:label: marburg
:align: left

![Marburg - Naslov](./img/06_logo-marburg-1.pdf)

![Marburg - Drsnica](./img/06_logo-marburg-2.pdf)

Marburg tema.
```
````
````{tab-item} PDF (Bergen)
```{figure}
:label: bergen
:align: left

![Bergen - Naslov](./img/06_logo-bergen-1.pdf)

![Bergen - Drsnica](./img/06_logo-bergen-2.pdf)

Bergen tema.
```
````
`````

:::

V razredu beamer lahko tudi uporabimo ukaze za _logične strukture_ kot so `\section{}` in `\subsection{}` za organizacijo predstavitve.
Ti ukazi ne ustvarijo drsnic, vendar jih lahko uporabimo za generiranje kazala vsebine.
To lahko storimo z uporabo ukaza `\tableofcontents` v okolju `frame`, poglejte [Primer %s](#eg_beamer-toc-1).
Upoštevajte, da razdelek `Literatura` ni v kazalo vključen, ker je definiran z ukazom `\section*{}`.

:::{prf:example}
:label: eg_beamer-toc-1

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}
\usepackage[slovene]{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle

% Drsnica s kazalom
\begin{frame}{Kazalo}
  \tableofcontents
\end{frame}


% Logične strukture
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
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-toc-1.pdf
:name: fig_06_eg-beamer-toc-1
```
````
`````

:::

Če želimo kazalo prikazati postopoma, lahko k ukazom `\tableofcontents` dodamo možnost `pausesections`. Poglejte [Primer %s](#eg_beamer-toc-2).

:::{prf:example}
:label: eg_beamer-toc-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}
\usepackage[slovene]{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle

% Drsnica s kazalom
\begin{frame}{Kazalo}
  \tableofcontents[pausesections]
\end{frame}


% Logične strukture
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
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-toc-1.gif
:name: fig_06_eg-beamer-toc-1b
```
````
`````

:::

Ukaze kot `\section` ne ustvarijo drsnic, vendar lahko z ukazom `\sectionpage` znotraj okolja `frame` ustvarimo drsnico, ki prikazuje naslov razdelka.
Na žalost, ukaz `\sectionpage` ni dela skupaj z paketom `babel`.
Druga možnost je ponatis kazala na začetku vsakega poglavja, da bralce spomnimo, kje smo.
To lahko storimo z uporabo ukazov `\AtBeginSection[]` in `\tableofcontents[currentsection]` poglejte [Primer %s](#eg_beamer-toc-3). Če želimo, da se v kazalu prikažejo samo razdelek (in ne podrazdelek), dodamo ukaz \tableofcontents opcijo `hidesubsections`.

:::{prf:example}
:label: eg_beamer-toc-3

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}
\usepackage[slovene]{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
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

% Logične strukture
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
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-toc-2.gif
:name: fig_06_eg-beamer-toc-2b
```
````
`````

:::

Poleg ukazov `\section` in `\subsection`, Beamer podpira tudi ukaz `\part{}` za večje logične enote.
Vsak del prestavitve (definiran z `\part{}`) lahko začne z drsnico, ki prikazuje naslov dela z uporabo ukaza `\partpage` v okolju `frame`. Poleg tega, ima vsak del lahko svoje kazalo vsebine; poglejte [Primer %s](#eg_beamer-parts).

:::{prf:example}
:label: eg_beamer-parts

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass{beamer}
\usepackage[slovene]{babel}

\title{Naslov predstavitve}
\author[A. Montero]{Antonio Montero}
\date[MatTeh -- Nov. 2025]{Matematične tehnologije \\ November 2025}
\subtitle{Zanimivni podnaslov}
\institute[UL-PEF]{Univerza v Ljubljani \\ Pedagoška fakulteta}
\titlegraphic{\includegraphics[width=0.2\textwidth]{UL_logo.png}}
\logo{\includegraphics[width=0.2\textwidth]{UL_logo.png}}

\begin{document}
\maketitle



% Logične strukture
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
````
````{tab-item} PDF
``` {image} ./img/06_eg-beamer-parts.gif
:name: fig_06_eg-beamer-toc-2
```
````
`````

:::

(beamer_prekrivanje)=

## Spefifikacije prekrivanja

Izhodna datoteka Beamer je običajno v formatu `PDF` kar je v principu statična datoteka. Beamer pa omogoča ustvarjanje dinamičnih učinkov z uporabo _specifikacij prekrivanja_ (ang. _overlay specifications_).

Prestavitve Beamer sestoji iz serie drsnic, vsaka drsnica pa je lahko razdeljena na več slojev oz. stran (ang. _slides_). V izhodni `PDF` datoteki vsak sloj ustreza eni strani. Specfikacije prekrivanja so ukazi, ki določajo, kateri deli vsebine so prikazani na določenem sloju.

Najlažji način za uporabo specifikacij prekrivanja je z uporabo ukaza `\pause`, ki ustvari prekinitev na trenutni točki v drsnici.
Če dodamo ukaz `\pause` v okolje `frame`, prvi sloj drsnice prikaže vsebino do prva uporaba ukaza `\pause`, drugi sloj prikaže vsebino do druge uporabe ukaza `\pause` in tako naprej. Poglejte [Primer %s](#eg_beamer-pause).

:::{prf:example}
:label: eg_beamer-pause

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{Primer uporabe ukaza \texttt{\textbackslash pause}}
  Ta besedilo bo napisano od prvega sloja naprej, \pause
  to od drugega, \pause
  in to samo na tretjem in zadnjem sloju.
\end{frame}
```
````

````{tab-item} PDF
``` {image} ./img/06_eg-pause.gif
:name: fig-06_eg-pause
```
````
`````

:::

Ukaz `\pause` je enostaven za uporabo, vendar ponuja omejene možnosti prilagajanja. Za bolj natančno kontrolo nad tem, kdaj se posamezni deli vsebine prikažejo, lahko uporabimo _specifikacije prekrivanja_ znotraj ukazov kot so `\textbf`, `\textit`, `\textcolor` in druge (poglejte [Tabelo %s](#tab-prekrivanje-ukaze)).

:::{dropdown} Ukazi, ki podpirajo specifikacije prekrivanja

```{list-table}
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

```

Beamer uporaba ukaza `\alert` in `\structure` za poudarjanje besedila. Ukaz `\alert` običajno prikaže besedilo v rdeči barvi, medtem ko `\structure` uporabi barvo, določeno s temo Beamerja za poudarjeno besedilo.
:::

Sintaksa za specifikacije prekrivanja je naslednja:

```latex
\ukaz<spec_prek>{<besedilo>}
```

Kjer `\ukaz` predstavlja ukaz, ki ga želimo nadzorovati (npr. `\textbf`), `spec_prek` pa določa, na katerih slojih bo ukaz uporabljen. Na primer, `\textbf<2>{<besedilo>}` bo prikazalo `<besedilo>` krepko le na drugem sloju drsnice (ostali sloji bodo prikazali `<besedilo>` v običajnem slogu); poglejte [Primer %s](#eg_beamer-overlay-1).

:::{prf:example}
:label: eg_beamer-overlay-1

`````{tab-set}
````{tab-item} LaTeX
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

  \textit<3,5>{To besedilo je poševno v tretjem in petem sloju.}

  \textcolor<1-2,4>{blue}{To besedilo je modro v prvim, drugim in četrtem sloju.}
\end{frame}
```
````
````{tab-item} PDF
``` {image} ./img/06_eg-overlays-1.gif
:name:fig_06_eg-overlay
```
```
````
`````

:::

Nekatere ukaze, kot so `\item` v okolju `itemize` in `enumerate`, imajo vgrajeno podporo za specifikacije prekrivanja; poglejte [Primer %s](#eg_beamer-overlay-2).

:::{prf:example}
:label: eg_beamer-overlay-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{Specifikacije prekrivanja v okoljih}
  \begin{enumerate}
    \item<1-> Prva točka je vidna od prvega sloja naprej.
    \item<2,4> Druga točka je vidna v drugem in četrtem sloju.
    \item<2> Tretja točka je vidna samo v drugem sloju.
    \item<3-> Četrta točka je vidna od tretjega sloja naprej.
    \item <4-> Peta točka je vidna od četrtega sloja naprej.
  \end{enumerate}
\end{frame}
```
````
````{tab-item} PDF
``` {image} ./img/06_eg-overlays-2.gif
:name: fig_beamer-overlay-2
```
````
`````

:::{exercise}
:label: ex_overlays-1

1. Napišite Beamer drsnico, ki prikazuje naslednji neurejen seznam:

- Ena
- Dve
- Tri
- Štiri

2. Z uporabo specifikacij prekrivanja naredite naslednje:

- Točko prikažite v obratnem vrstnem redu, nato ostanejo štiri sloje in izginejo v nasprotnem vrstnem redu, kot so se pojavile (tako da je beseda „Štiri“ prva, ki se prikaže, in zadnja, ki izgine).
- Če je število slojev liho, morajo biti vse besede, ki predstavljajo soda števila, rdeče. Nasprotno velja za besede, ki predstavljajo liha števila.
  :::

```{margin}
[Seznam vaj](#06_latexBeamer_vaje)
```

:::{solution} ex_overlays-1
:class: tip dropdown
Možna rešitev:

```latex
\begin{frame}{Vaja 6.1}
  \begin{itemize}
    \item<4-8> \textcolor<4,6,8>{red}{Ena}
    \item<3-9> \textcolor<3,5,7,9>{red}{Dve}
    \item<2-10> \textcolor<2,4,6,8,10>{red}{Tri}
    \item<1-11> \textcolor<1,3,5,7,9,11>{red}{Štiri}
  \end{itemize}
  \end{frame}
```

:::

(beamer_teme)=

## Teme in barvne sheme

(06_latexBeamer_vaje)=

## Vaje
