(06_latex_beamer)=

# Beamer: Prestavitve v LaTeXu

% https://www.overleaf.com/learn/latex/Beamer_Presentations%3A_A_Tutorial_for_Beginners_(Part_1)%E2%80%94Getting_Started

Beamer je LaTeX razširitev za izdelavo drsnic ("slajdov").
Za izdelavo predstavitve z Beamerjem uporabimo razred `beamer` namesto `article`.
Nato uporabimo okolja `frame` za vsak posamezen diapozitiv.
Ukaz `\frametitle{}` določi naslov drsnice. Lahko tudi uporabimo ukaz `framesubtitle{}` za podnaslov drsnice.
Krajša možnost je, da naslov oz. podnaslov drsnice podamo kot možnost okolja `frame`, {prf:ref}`eg_beamer_1`.

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
:label: eg\_

`````{tab-set}
````{tab-item} LaTeX
```latex

```
````
````{tab-item} PDF
``` {image} --path--to--image
:name:
```
````
`````

:::

(beamer_teme)=

## Teme in barvne sheme

(06_latexBeamer_vaje)=

## Vaje
