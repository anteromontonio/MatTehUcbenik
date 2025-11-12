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

:::{caution} Opozorilo
Razred `beamer` uporaba paket `babel` za jezike malo drugače kot običajni razredi dokumentov (kot so `article` ali `report`).
V tem razredu je priporočljivo, da je jezik dokumenta določen kot možnost razreda dokumenta (npr. `\documentclass[slovene]{beamer}`) in da se paket `babel` naloži brez možnosti jezika (npr. `\usepackage{babel}`).
:::

Ukaz `\frametitle{}` določi naslov drsnice. Lahko tudi uporabimo ukaz `framesubtitle{}` za podnaslov drsnice.
Krajša možnost je, da naslov oz. podnaslov drsnice podamo kot možnost okolja `frame`; [Primer %s](#eg_beamer_1).

:::{prf:example}
:label: eg_beamer_1

`````{tab-set}
````{tab-item} LaTeX
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
````
````{tab-item} PDF
``` {figure} ./img/06_eg-beamer-1.pdf
:label: fig:06_eg-beamer-2

Primer drsnice z naslovom in podnaslovom.
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
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-title-1.pdf
:label: fig_06_eg-beamer-title-1
Primer naslovne drsnice z dodatnimi informacijami.
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
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-title-2.pdf
```
````
````{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-title-3.pdf
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
\documentclass[slovene]{beamer}
\usepackage{babel}

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
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-toc-1.pdf
:label: fig_06_eg-beamer-toc-1

Primer drsnice s kazalom vsebine.
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
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-toc-1.gif
:label: fig_06_eg-beamer-toc-1b

Uporaba možnosti `pausesections` za postopno prikazovanje kazala vsebine.

```
````
`````

:::

Ukaze kot `\section` ne ustvarijo drsnic, vendar lahko z ukazom `\sectionpage` znotraj okolja `frame` ustvarimo drsnico, ki prikazuje naslov razdelka.

<!-- Na žalost, ukaz `\sectionpage` ni dela skupaj z paketom `babel`. -->

Druga možnost je ponatis kazala na začetku vsakega poglavja, da bralce spomnimo, kje smo.
To lahko storimo z uporabo ukazov `\AtBeginSection[]` in `\tableofcontents[currentsection]` poglejte [Primer %s](#eg_beamer-toc-3). Če želimo, da se v kazalu prikažejo samo razdelek (in ne podrazdelek), dodamo ukaz \tableofcontents opcijo `hidesubsections`.

:::{prf:example}
:label: eg_beamer-toc-3

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-toc-2.gif
:label: fig_06_eg-beamer-toc-2b

Kazalo vsebine na začetku vsakega razdelka.
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
\documentclass[slovene]{beamer}
\usepackage{babel}

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
``` {figure} ./img/06_eg-beamer-parts.gif
:label: fig_06_eg-beamer-toc-2

Uporaba logične enote `\part` v Beamer predstavitvi.

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
``` {figure} ./img/06_eg-pause.gif
:label: fig-06_eg-pause

Uporaba ukaza `\pause`.
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
``` {figure} ./img/06_eg-overlays-1.gif
:label:fig_06_eg-overlay

Uporaba specifikacij prekrivanja.

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
    \item<4-> Peta točka je vidna od četrtega sloja naprej.
  \end{enumerate}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg-overlays-2.gif
:label: fig_beamer-overlay-2

Uporaba specifikacij prekrivanja v okoljih `enumerate` in `itemize`.

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

Ukaz \includegraphics podpira tudi specifikacije prekrivanja, kar omogoča prikazovanje različnih slik na različnih slojih drsnice. To je uporabno za simulacijo animacij z zaporednim prikazovanjem slik;
poglejte [Primer %s](#eg_beamer-overlay-3).

:::{prf:example}
:label: eg_beamer-overlay-3

`````{tab-set}
````{tab-item} LaTeX
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
````
````{tab-item} PDF
``` {figure} ./img/06_eg-overlays-3.gif
:label: fig_06_eg-overlay-3

Lažna animacija s specifikacijami prekrivanja.
```
````
```
````
`````

:::

:::{dropdown} Paket `animate`
Za bolj gladke in prilagodljive animacije v Beamer predstavitvah lahko uporabimo paket [`animate`](https://ctan.org/pkg/animate?lang=en). Ta paket omogoča vključevanje animacij, ki se samodejno predvajajo znotraj drsnic Beamer.
Paket `animate` omogoča uporabo ukaza `\animategraphics`, ki ima naslednjo sintakso:

```latex
\animategraphics[<možnost>]{<fps>}{<basename>}{<first>}{<last>}
```

Kjer:

- `<možnost>` so dodatne možnosti, kot so `loop` (za neskončno ponavljanje) in `autoplay` (za samodejno predvajanje ob prikazu drsnice).
- `<fps>` določa število sličic na sekundo.
- `<basename>` je osnovno ime datotek s slikami (brez številk in pripone).
- `<first>` in `<last>` določata obseg številk slik, ki se bodo uporabile v animaciji.

Na primer, zaporedje slik, da smo uporabili v [Primeru %s](#eg_beamer-overlay-3), lahko vključimo kot animacijo z uporabo paketa `animate` kot sledi:

```latex
%V preambuli
\usepackage{animate}

%V telesu dokumenta
\begin{frame}{Z uporabo paketa \texttt{animate}}
  \begin{figure}
    \centering
    \animategraphics[loop,autoplay,width=0.5\textwidth]{2}{stick0}{1}{8}
    \caption{Prava animacija s paketom \texttt{animate}.}
  \end{figure}
\end{frame}

```

Na žalost, nekatere PDF gledalnike ne podpirajo animacij.
Najvarnejša možnost je uporaba »lažnih animacij«, kot je prikazano v [Primeru %s](#eg_beamer-overlay-3).

:::

Naslednje tri ukaze delujejo zelo podobno. Prikazujejo `<besedilo>` v skladu z `<spec_prek>`. Razlika med njimi je v tem, kako se obnašajo, ko besedilo ni prikazano.

- `\only<spec_prek>{<besedilo>}`: Prikaže `<besedilo>` samo na slojih, določenih z `<spec_prek>`. Na drugih slojih `<besedilo>` ni prisotno (ne zavzame prostora).
- `\visible<spec_prek>{<besedilo>}`: Prikaže `<besedilo>` na slojih, določenih z `<spec_prek>`, in na drugih slojih ohrani prostor, ki ga `<besedilo>` zavzema (vendar je **nevidno**).
- `\uncover<spec_prek>{<besedilo>}`: Prikaže `<besedilo>` na slojih, določenih z `<spec_prek>`, in na drugih slojih ohrani prostor, ki ga `<besedilo>` zavzema (vendar je **prozoren**).

Razlika med `\visible` in `\uncover` je odvisno od uporabe _prosojnosti_ (ang. _transparency_). To se nadzoruje z ukazom `\setbeamercovered{<možnost>}` v preambuli dokumenta. Možnosti vključujejo:

- `invisible`: Besedilo je popolnoma nevidno (privzeta možnost).
- `transparent=<neprosojnost>`: Besedilo je prikazano z določeno stopnjo prosojnosti: `<neprosojnost>` je vrednost med `0` (popolnoma prozorno) in `100` (popolnoma neprozorno); privzeta vrednost je `15`.
- `dynamic`: Vse prekrite besede postanejo precej prosojne, vendar na dinamičen način. Daljši čas potreben za odkritje besedila, močnejša je prosojnost. Poglejte [Primer %s](#eg_overlays-only-1).

:::{prf:example}
:label: eg_overlays-only-1

`````{tab-set}
````{tab-item} LaTeX
```latex
%V preambuli
\setbeamercovered{transparent}

%V telesu dokumenta
\begin{frame}{\texttt{\textbackslash only}, \texttt{\textbackslash visible} in \texttt{\textbackslash uncover}}

  Smo na sloju: \alert<1>{1}, \alert<2>{2}, \alert<3>{3}, \alert<4>{4}, \alert<5>{5}, \alert<6>{6}, \alert<7>{7}, \alert<8>{8}.


  Moja najgloblja skrivnost je prikazana samo na drugem in sedmem sloju:
  \only<2,7>{ \textcolor{blue}{srkivnost!}}
  medtem pa zanjo ni rezerviranega prostora.

  Sporočilo z drugega planeta je tukaj:
  \visible<4->{Izbranci so resnični, vendar živijo zelo daleč}.
  V prihodnosti ga bomo lahko prebrali (od sloja 4 naprej).

  Sporočilo iz podzemlja ni povsem nevidno:
  \uncover<6->{Pozdravljeni! Sem duh, vendar sem prijazen.}
  Bojim se duhov!.

\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg-overlays-only-1.gif
:label: fig_06_eg-overlays-only-1

Uporaba ukazov `\only`, `\visible` in `\uncover`.
```
````
`````

:::

Obstajajo še drugi ukazi za specifikacije prekrivanja, kot so:

- `\invisible<spec_prek>{<besedilo>}`: Točno nasprotje ukaza `\visible`. Prikaže `<besedilo>` na slojih, določenih z `<spec_prek>`, in na drugih slojih besedilo ni prisotno.
- `\alt<spec_prek>{<besedilo1>}{<besedilo2>}`: Prikaže `<besedilo1>` na slojih določenih z `<spec_prek>`, in `<besedilo2>` na ostalih slojih.
- `\temporal<spec_prek>{<besedilo1>}{<besedilo2>}{<besedilo3>}`: Prikaže `<besedilo1>` pred prvi sloji določenimi z `<spec_prek>`, `<besedilo2>` na slojih določenih z `<spec_prek>`, in `<besedilo3>` po zadnji sloji določeni z `<spec_prek>`.

V [Primeru %s](#eg_overlays-only-2) so prikazani ti ukazi v akciji.

:::{prf:example}
:label: eg_overlays-only-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{\texttt{\textbackslash invisible}, \texttt{\textbackslash alt} in \texttt{\textbackslash temporal}}

  Smo na sloju: \alert<1>{1}, \alert<2>{2}, \alert<3>{3}, \alert<4>{4}, \alert<5>{5}, \alert<6>{6}, \alert<7>{7}, \alert<8>{8}.

  Tukaj je nekaj besedila, ki je nevidno na slojih 3 in 5:
  \structure{\invisible<3,5>{To besedilo je nevidno na slojih 3 in 5.}}

  Tukaj je nekaj besedila, ki se spreminja glede na sloj:
  \alt<2,4,6>{\textcolor{blue}{To je besedilo za sloje 2, 4 in 6.}}
  {\textcolor{red}{To je besedilo za vse ostale sloje.}}

  Tukaj je nekaj besedila, ki se spreminja glede na čas:
  \temporal<3-5>{\textcolor{red}{To je besedilo pred sloji 3.}}
  {\textcolor{blue}{To je besedilo med sloji 3 in 5.}}
  {\textcolor{green}{To je besedilo po sloji 5.}}

\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg-overlays-only-2.gif
:label: fig_06_eg-overlays-only-2

Uporaba ukazov `\invisible`, `\alt` in `\temporal`.
```
````
`````

:::

Nekatere okolje v Beamerju podpirajo specifikacije prekrivanja.
Sintaksa je običajno `\begin{okolja}<spec_prek>` in rezultat je, da se celotno okolje prikaže samo na slojih določenih z `<spec_prek>`.

Vsak od ukazov `\only`, `\alt`, `\visible`, `\uncover` in `\invisible` ima svojo različico okolja, in sicer, `onlyenv`, `altenv`, `visibleenv`, `uncoverenv` in `invisibleenv`.
Vsi razen `altenv` ima sintakso

```latex
\begin{okolja}<spec_prek>
  <vsebina>
\end{okolja}
```

in delujejo podobno kot njihovi ukazni ekvivalenti.
Okolje `altenv` ima sintakso

```latex
\begin{altenv}<spec_prek>
{<begin_privzeto>}{<end_privzeto>}
{<begin_alternativno>}{<end_alternativno>}
  <vsebina>
\end{altenv}
```

V določenih slojih določenih z `<spec_prek>`, se `<vsebina>` obdana med `<begin_privzeto>` in `<end_privzeto>`, medtem ko se v ostalih slojih prikaže vsebina obdana z `<begin_alternativno>` in `<begin_alternativno>`.

Lahko uporabimo ukaze kot je `\only` za dinamično spremeniti vsebino drsnice, npr.

```latex
  \only<1>{Besedilo za prvi sloj.}
  \only<2>{Besedilo za drugi sloj, ki je lahko daljše. Če je besedilo daljše, se okvir prilagodi višini vsebine.}
  \only<3>{Tretji sloj ima spet krajše besedilo.}
```

Težava pri tem pristopu je, da lahko pride do nadležnih razlik v višini
elementov, kar lahko povzroči, da se celoten okvir »trese« od sloja do sloja.

Za rešitev tega problema lahko uporabimo okolje `overlayarea`, ki ima naslednjo sintakso:

```latex
\begin{overlayarea}{<širina>}{<višina>}
  <vsebina>
\end{overlayarea}
```

To okolje ustvari območje `<širina>` krat `<višina>`, v katerem se vsebina lahko dinamično spreminja brez vpliva na višino okvirja drsnice; poglejte [Primer %s](#eg_overlayarea).

:::{prf:example}
:label: eg_overlayarea

`````{tab-set}
````{tab-item} LaTeX
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
  \visible<1-4>{\textcolor{red}{Ostali elementi niso nestabilni}. }

\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg-overlayarea-1.gif
:label: fig_06_overlayarea-1

Brez okolja \texttt{overlayarea}
```
````
````{tab-item} LaTeX
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
  \visible<1-4>{Ostali elementi zdaj \alert{so} nestabilni. }
\end{frame}
```
````

````{tab-item} PDF
``` {figure} ./img/06_eg-overlayarea-2.gif
:label: fig_06_overlayarea-2
Z okoljem \texttt{overlayarea}

```
````
`````

:::

(beamer_vsebina)=

## Vsebina predstavitve

### Seznami

Navadna okolja za sezname, kot so `itemize`, `enumerate` in `description`, so podprta v Beamerju.

Seveda lahko uporabimo tudi ukaz `\pause` ali specifikacije prekrivanja kot prikazano v [Primeru %s](#eg_beamer-overlay-2) za postopno prikazovanje elementov seznama.
Druga možnost je uporaba speficikacije `[<+->]` v okolju seznama, kar samodejno prikaže vsak element na naslednjem sloju; poglejte [Primer %s](#eg_beamer-lists-1).

V tem primeru tudi pokažemo uporabo ukaza `\vspace{<višina>}` za ustvarjanje navpičnega prostora med seznami in ukaza `\vfill`, ki potisne vsebino navzdol do dna okvirja drsnice.

:::{prf:example}
:label: eg_beamer-lists-1

`````{tab-set}
````{tab-item} LaTeX
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
    \item[Itemize] Okolje za neseznamne sezname.
    \item[Enumerate] Okolje za oštevilčene sezname.
    \item[Description] Okolje za sezname z opisi.
  \end{description}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-lists-1.gif
:label: fig_06_eg_beamer-lists-1

Seznami v Beamerju z uporabo specifikacij prekrivanja.

```
````
`````

:::

Če je seznam predolg, da bi ga lahko prikazali na eni drsnici. V tem primeru lahko uporabimo pristop, ki ga prikazuje [Primer %s](#eg_beamer-lists-2).

:::{prf:example}
:label: eg_beamer-lists-2

`````{tab-set}
````{tab-item} LaTeX
```latex
% V preambuli, definiramo števec za nadaljevanje seznama
\newcounter{currentenumi}
% V telesu dokumenta
\begin{frame}{Predolgi seznami}{Priva drsnica}
  \begin{enumerate}[<+->]
    \item Točka 1.
    \item Točka 2.
    \item Točka 3.
    % Shranimo trenutni števec
    \setcounter{currentenumi}{\theenumi}
  \end{enumerate}
\end{frame}
\begin{frame}{Predolgi seznami}{Druga drsnica}
  \begin{enumerate}[<+->]
    % Nadaljujmo s shranjenim števcem
    \setcounter{enumi}{\thecurrentenumi}
        \item Točka 4.
        \item Točka 5.
    \end{enumerate}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-lists-2.gif
:label: fig_06_eg_beamer-lists-2

Predolgi seznami razdeljeni na več drsnic.
```
````
`````

:::

### Stolpci

Beamer omogoča ustvarjanje stolpcev z uporabo okolja `columns`. Vsak stolpec je definiran z okoljem `column`, ki ima naslednjo sintakso:

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

Kjer `<širina>` določa širino stolpca (lahko je absolutna vrednost, npr. `5cm`, ali relativna vrednost, npr. `0.5\textwidth`), `<spec_prek>` pa so opcijske specifikacije prekrivanja, ki določajo, na katerih slojih bo stolpec prikazan.
Poglejte [Primer %s](#eg_beamer-columns-1).

:::{prf:example}
:label: eg_beamer-columns-1

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{Stolpci v Beamerju}
  \begin{columns}
  \column{0.6\textwidth}<2>
      \centering
      Ta stolpec zavzema $60\%$ širine besedila, in je viden na drugem sloju.
  \column{0.4\textwidth}<1->
      \centering
      Ta stolpec zavzema $40\%$ širine besedila in je viden na vseh slojih.
  \end{columns}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-columns-1.gif
:label: fig_06_eg_beamer-columns-1

Stolpci v Beamerju z uporabo specifikacij prekrivanja.
```
````
`````

:::

Ta pristop lahko uporabimo za ustvarjanje drsnic z besedilom na eni strani in sliko na drugi strani; poglejte [Primer %s](#eg_beamer-columns-2).

:::{prf:example}
:label: eg_beamer-columns-2

`````{tab-set}
````{tab-item} LaTeX
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
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-columns-2.pdf
:label: fig_06_eg_beamer-columns-2

Drsnica z besedilom in sliko v stolpcih.
```
````
```
````
`````

:::

### Tabele

Na splošno večina ukazov, ki smo jih opisali
v poglavju [](./02_latexOsnovnaOkolja) za ustvarjanje tabel v LaTeX-u deluje tudi v Beamerju, dokler naložimo ustrezne pakete (npr. `booktabs`, `array`, `multrow`).

Poleg tega lahko uporabimo specifikacije prekrivanja za postopno prikazovanje vrstic ali stolpcev v tabeli; poglejte [Primer %s](#eg_beamer-tables-1).

:::{prf:example}
:label: eg_beamer-tables-1

`````{tab-set}
````{tab-item} LaTeX
```latex
  \begin{table}
  \begin{tabular}{ l c l }
    \toprule
    % \visible<1->
    Oseba & Obraz & Razpoloženje\\
    \midrule %\pause
    \visible<2->{Jaz & :) & Vesel} \\ %\pause
    \visible<3->{Vi & :/ & Zaskrbljen} \\ %\pause
    \visible<4->
    {Svoj partner} & \visible<5->{:(} & \visible<6>{Žalosten} \\
    \bottomrule
    \end{tabular}
    \caption{Primer preproste tabele v Beamerju.}
  \end{table}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-tables-1.gif
:label: fig_06_eg_beamer-tables-1

Tabele v Beamerju z uporabo specifikacij prekrivanja.
```
````
`````

:::

Če je tabela preširoka ali predolga za drsnico, lahko uporabimo okolje `resizebox` iz paketa `graphicx`. Sintaksa je `\resizebox{<širina>}{<višina>}{<vsebina>}`, kjer lahko uporabimo `!` za samodejno prilagoditev višine ali širine glede na drugo dimenzijo.
Poglejte [Primer %s](#eg_beamer-tables-2).

:::{prf:example}
:label: eg_beamer-tables-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{Velike tabele v Beamerju}
  \begin{table}
  \resizebox{\textwidth}{!}
  {
  \begin{tabular}{ccccccccccccc}
  \toprule
      To & je & tabela, & ki & je & preširoka & za & drsnico. & Nimamo & dovolj & prostor & 12 & 13\\
  \midrule
      a & b & c & d & e & f & g & h & i & j & k & l & m\\
  \bottomrule
  \end{tabular}
  }
  \caption{Primer tabela, ki presega širino drsnice v Beamerju.}
  \end{table}
  \end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-tables-2-1.pdf
:label: fig_06_eg_beamer-tables-2-1

Tabela, ki presega širino drsnice v Beamerju.
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_beamer-tables-2-2.pdf
:label: fig_06_eg_beamer-tables-2-2

Z uporabo ukaz `\resizebox` za prilagoditev tabele širini drsnice.
```
````
`````

:::

### Bloki

Beamer ponuja okolje `block` za ustvarjanje poudarjenih vsebinskih blokov znotraj drsnic. Sintaksa je naslednja:

```latex
\begin{block}{<naslov bloka>}
  <vsebina bloka>
\end{block}
```

Poleg tega Beamer ponuja posebne vrste blokov, kot so `exampleblock` in `alertblock`, ki imajo različne sloge za poudarjanje vsebine. Slog bloka je odvisen od izbrane teme Beamerja. Poglejte [Primer %s](#eg_beamer-blocks-1).

:::{prf:example}
:label: eg_beamer-blocks-1

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{Bloki}
  \begin{block}{Navaden blok}
    To je vsebina navadnega bloka.
  \end{block}
  \begin{exampleblock}{Blok z primerom}
    To je vsebina bloka z primerom.
  \end{exampleblock}
  \begin{alertblock}{Blok z opozorilom}
    To je vsebina bloka z opozorilom.
  \end{alertblock}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_bloki-1-1.pdf
:label: fig_06_eg_bloki-1-1
Bloki v Beamerju z privzeto temo.
```
````
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_bloki-1-2.pdf
:label: fig_06_eg_bloki-1-2
Bloki v Beamerju z temo „Boadilla“.
```
````
`````

:::

Okolje za teoreme, kot so `theorem`, `lemma`, `definition`, `proof`, itd. so prav tako podprta v Beamerju in imajo slog, ki je podobno kot bloki. Poglejte [Primer %s](#eg_beamer-blocks-2).

:::{prf:example}
:label: eg_beamer-blocks-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{frame}{Bloki za teoreme}
  \begin{theorem}[Pitagorov izrek]
    V pravokotnem trikotniku velja: $a^2 + b^2 = c^2$.
  \end{theorem}

  \begin{lemma}
    To je primer lema bloka.
  \end{lemma}

  \begin{proof}
    To je primer dokaza.
  \end{proof}
\end{frame}
```
````
````{tab-item} PDF
``` {figure} ./img/06_eg_bloki-2.pdf
:label:
```
````
`````

:::

Lahko tudi definiramo svoje matematične bloke z uporabo ukaza `\newtheorem` točno tako, kot v običajnem LaTeXu.

(beamer_teme)=

## Teme in barvne sheme

Beamer ponuja različne teme in barvne sheme za prilagoditev videza predstavitve. Teme določajo splošno postavitev in slog drsnic, in barvno paleto.

Obstajajo štiri parametri za prilagoditev videza predstavitve v Beamerju:

- Tema barv (ang. `color theme`): Določa barvno shemo predstavitve.
- Tema pisave (ang. `font theme`): Določa slog pisave.
- Notranje teme (ang. `inner theme`): Določa slog notranjih elementov, kot so sezname, bloki, kazalo, itd.
- Zunanje teme (ang. `outer theme`): Določa slog zunanjih elementov, kot so glave, noge, okvirji drsnic, itd.

Poleg teh štirih parametrov lahko izberemo tudi celotno temo, ki združuje vse te vidike v eno samo temo. Večinoma časa, je dovolj, da izberemo samo temo, saj bo ta samodejno nastavila ustrezne barvne sheme, pisave in notranje ter zunanje teme in če želimo, lahko dodatno prilagodimo posamezne parametre.

Teme se naložijo z ukazom `\usetheme{<ime_teme>}`, medtem ko se posamezni parametri naložijo z ukazi

- `\usecolortheme{<ime_barvne_sheme>}`
- `\usefonttheme{<ime_pisave>}`
- `\useinnertheme{<ime_notranje_teme>}`
- `\useoutertheme{<ime_zunanje_teme>}`

Število možnosti za te ukaze je ogromno in nemogoče je prikazati vse relevantne primere.
Lahko pa ponudimo zunanje vire za raziskovanje različnih tem.

- [Beamer Theme Matrix](https://hartwork.org/beamer-theme-matrix/): Interaktivno orodje za raziskovanje različnih kombinacij tem in barvnih shem v Beamerju.
- [Beamer Theme Gallery](https://deic.uab.es/~iblanes/beamer_gallery/index.html): Galerija različnih tem Beamer, tem pisave in tem barv.
- [Beamer User Guide](https://tug.ctan.org/macros/latex/contrib/beamer/doc/beameruserguide.pdf): Del III vodiča za uporabnike Beamerja vsebuje podrobne informacije o temah in barvnih shemah.

(06_latexBeamer_vaje)=

## Vaje

::: {exercise} Domača naloga
:nonumber:

1. Ustvarite predstavitev Beamer, ki ima od 5 do 10 drsnic.
2. Vsebina predstavitve naj bo vaša izbira.
3. Vključite različne elemente, kot so sezname, tabele, slike, bloke, itd. (ni treba vključiti vse elemente, opisane v tem poglavju).
4. Uporabite specifikacije prekrivanja za postopno prikazovanje vsebine na drsnicah.
5. Ne bojte se raziskovati različnih tem za svojo predstavitev.
   :::
