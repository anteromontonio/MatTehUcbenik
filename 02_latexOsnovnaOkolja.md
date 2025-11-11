# Osnovna okolja

:::{admonition} Opomba
:class: note  
Včasih, ko vadimo z LaTeXom, se znajdemo v situaciji, ko moramo vstaviti lažno besedilo, tj. besedilo, katerega vsebina ni pomembna.
LaTeX ima za to poseben paket, in sicer `lipsum`.
Ta paket nam omogoča dostop do 150 odstavkov besedila [Lorem Ipsum](https://www.lipsum.com/),ki je delček besedila _"De finibus bonorum et malorum"_ avtorja Cicero.

Ko pri vsakem paketu, ga morate naložiti z ukazom `\usepackage{lipsum}` v preambuli.
Nato lahko vstavite lažno besedilo z ukazom `\lipsum[<razpon odstavkov>][<razpon stavkov>]`, kjer sta `<razpon odstavkov>` in `<razpon stavkov>` razpon odstavkov in stavkov, ki jih želimo vstaviti.

Na primer, `\lipsum[1-3]` bo vstavilo prve tri odstavke besedila Lorem Ipsum, medtem ko bo `\lipsum[4][1]` vstavilo samo prvi stavek četrtega odstavka.
:::

## Logična struktura dokumenta

LaTeX ima na voljo posebni ukazi za logično strukturo dokumenta.
Sintaksa teh ukazov je `\ime_enote{naslov}`, kjer je `ime_enote` ime loginčne enote, npr. `section`, medtem ko je `naslov` besedilo naslova, ki ga želimo prikazati v dokumentu.

Dejanske logične enote, ki so na voljo, so odvisne od razreda dokumenta, npr. za razred `article` so na voljo enote `section`, `subsection`, `subsubsection`, `paragraph` in `supargraph`.  
Razreda `report` in `book` imata na voljo tudi ukazi `\chapter{naslov}`.

:::{prf:example}
:label: latexUvod_razdelki

`````{tab-set}
````{tab-item} LaTeX
```latex
\section{To je section}
\subsection{To je subsection}
\subsubsection{To je subsubsection}
\paragraph{To je paragraph}
\subparagraph{To je subparagraph}
```
````

````{tab-item} PDF
```{figure} ./img/02_eg-razdelki.png
:name: razdelki
:alt: Logične enote v LaTeXu
```
````
`````

:::

Vse te razrede dokumentov imajo tudi enote `part`, ki ga lahko uporabite za razdelitev dokumenta na več delov, ne da bi to vplivalo na oštevilčenje poglavij, razdelkov itd.

Razmik med odstavki, oštevilčenje in velikost pisave naslovov bo samodejno nastavil LaTeX. To pomeni, da vam ni treba ročno oštevilčevati naslovov in da se, če na primer, odločite, da boste dodali novo poglavje na začetek dokumenta, vsa oštevilčenje poglavij, razdelkov itd. se bo samodejno posodobilo.

Ukaz `\tableofcontents` natisne kazalo našega dokumenta, ki sledi strukturi, ki smo jo določili z zgoraj opisanimi ukazi.
Upoštevajte, da je treba ta ukaz uporabiti v telesu datoteke, da se kazalo natisne na ustrezno mesto.

Vsi ukazi za logično strukturo dokumenta imajo tudi _"z zvezdico"_ različico, npr. `\section*{naslov}`, ki ustvari naslov brez oštevilčenja in ne vključuje naslova v kazalo.

Včasih je naslov našega razdelka zelo dolg in ne želimo, da se tako natisne v kazalu. V tem primeru lahko uporabimo naslednjo sintakso, da natisnemo krajšo različico naslova.

```latex
\section[Kratki naslov za kazalo]{Dolgi in še posebno dologočasen naslov,
ki se izpiše na začetku razdelka
ampak noro bi bilo,
če bi se tako izpisal tudi v kazalu}
```

:::{exercise}
:label: ex_razdelki
S svojim LaTeX dokumentom naredite naslednje. Shranite po vsakem koraku:

1. Ustvarite razdelek z imenom `Prvi razdelek` in dodajte nekaj besedila. Za ta namen lahko uporabite paket `lipsum`.
1. Ustvarite razdelek z imenom `Drugi razdelek`.
1. Ustvarite dva podrazdelka razdelka `Drugi razdelek` in ju poimenujete.
1. Premaknite razdelek `Prvi razdelek` pod konec razdelka `Drugi razdelek`.
1. Na koncu dokumenta vstavite kazalo.
1. Ustvarite podrazdelek _"z zvezdico"_ razdelka `Prvi razdelek` in ga poimenujte.
1. Ustvarite razdelek z zelo dolgim imenom in uporabite krajšo različico imena za kazalo.
1. Premaknite ukaz za kazalo na začetek dokumenta.
:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_razdelki
:class: tip, dropdown
Tukaj je primer, kako bi lahko izgledal vaš dokument po vseh korakih.

```latex
\documentclass{article}
\usepackage[slovene]{babel}

\usepackage{lipsum}

\begin{document}

\tableofcontents

\section{Drugi razdelek}
\lipsum[4-6]
\subsection{a je to podrazdelek?}
\lipsum[7]
\subsection{Ja, to je podrazdelek!}
\lipsum[8-10]

\section{Privi razdelek}
\lipsum[1-3]
\subsection*{Podrazdelek brez številke}
\lipsum[11-13]

\section[Tretji razdelek]{Tretji razdelek z dolgim naslovom, ki se razteza čez več vrstic}
\lipsum[14-15]


\end{document}
```

:::

(latexOsnovnaOkolja_poravnavaBesedila)=

## Poravnava besedila

LaTeX privzeto poravna besedilo z obeh strani, kar pomeni, da prilagodi prostor med besedami, tako da so vse vrstice približno enake dolžine.
V urejevalnikih WYSIWYG se ta nastavitev pogosto imenuje _obojestransko poravnano_.

Včasih želimo besedilo poravnati drugače, zato ima LaTeX tri različne okolja: `flushleft`, `flushright` in `center`.
Vendar je izvedba tega okolja nekoliko zastarela in povzroča težave z razdeljevanjem besed (kar LaTeX običajno opravi sam).
Sodobne različice teh okolij so bile implementirane v paketu `ragged2e`.
Ta paket morate naložiti v preambuli z ukazom `\usepackage{ragged2e}`.
Ta paket ponuja okolja `FlushLeft`, `FlushRight` in `Center`, ki so izboljšane različice zgoraj omenjenih okolij.

Njegova uporaba je preprosta in lažje razumljiva s pomočjo vaje.

:::{exercise}
:label: ex_poravnava
Naslednje besedilo reproducirajte v LaTeXu. Zadnji dve povedi vsakega odstavka sta ustvarjeni z ukazom `lipsum`.

```{figure} ./img/02_ex-poravnava.png
:name: ex-poravnava
:alt: Poravnava besedila v LaTeXu.
```

:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_poravnava
:class: tip, dropdown

Tukaj je koda, ki jo morate uporabiti za ustvarjanje tega izhoda.

```latex
\begin{flushleft}
Ta besedilo je
levo poravnan.
\LaTeX{} se ne trudi narediti
vrstic z enakimi dolžinami.

\lipsum[1][1-2]
\end{flushleft}

\begin{flushright}
Ta besedilo je desno poravnano.
Kot prej tudi tu vrstice nimajo
enakih dolžin.

\lipsum[1][1-2]
\end{flushright}

\begin{center}
V središču
sveta.

\lipsum[1][1-2]
\end{center}
```

:::

(latexOsnovnaOkolja_seznami)=

## Seznami

LaTeX ima tri vrste seznamov: _urejene sezname_, _neurejene sezname_ in _opise_.
Sintaksa za vse tri vrste seznamov je podobna.
Začnemo z okoljem, ki ga želimo uporabiti, nato pa vsak element seznama začnemo z ukazom `\item`.
Za urejene sezname uporabimo okolje `enumerate`, za neurejene sezname okolje `itemize`, za opise pa okolje `description`.

:::{prf:example}
:label: latexUvod_seznami

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{enumerate}
\item ena
\item dva
\item tri
\end{enumerate}

\begin{itemize}
\item prva točka neurejena seznama.
\item druga točka neurejena seznama.
\end{itemize}

\begin{description}
\item[Prva:] točka opisa.
\item[Druga:] točka opisa.
\item[Tretja, z daljšim imenom:] točka opisa.
\end{description}
```
````

````{tab-item} PDF
```{figure} ./img/02_eg-seznami.png
:name: seznami
:alt: Seznami v LaTeXu
```
````
`````

:::

Podobno kot pri logičnih enotah, LaTeX samodejno izvede oštevilčenje urejenih seznamov.

:::{exercise}
:label: ex_seznami

1. Napišite urejen seznam lastnosti, ki jih najbolj sovrašite pri svojem trenutnem, bivšem ali bodočem partnerju.
1. Napišite neurejen seznam stvari, ki bi jih vzili če bi morali takoj migrirati iz svoje države.
1. Napišite seznam, kjer opisujete svoje najljubše turistične destinacije v Sloveniji.
:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_seznami
:class: tip, dropdown
Tukaj so moji odgovori.

```latex
\begin{enumerate}
\item Pije barcaffe. %Barcaffe je redflag
\item Gre zelo pozno spat.
\item Konča serijo, ki jo skupaj gledava brez mene.
\end{enumerate}

\begin{itemize}
\item Potni list.
\item Mlinček za kavo.
\item Kitara.
\end{itemize}

\begin{description}
\item[Ljubljana:] Najboljše mesto v državi (edino mesto v državi).
\item[Kranjska gora:] Ker obožujem gore in razglede.
\item[Strunjan:] Najlepša plaža v Sloveniji.
\end{description}
```

:::

Lahko tudi gnezditi sezname, tj. imeti seznam znotraj seznama.

:::{prf:example}
:label: latexUvod_gnezdeniSeznami

`````{tab-set}

````{tab-item} LaTeX
```latex
\begin{enumerate}
\item Različna okolja lahko mešamo
po lastnem okusu:
\begin{itemize}
\item Toda to lahko postane smešno.
\item[-] To se začne s pomišljajem.
\end{itemize}
\item Zapomnite si:
\begin{description}
\item[Neumne] zadeve ne bodo postale pametne,
če so v seznamu.
\item[Pametne] zadeve, za razliko, pa lahko čudovito
prikažemo s seznamom.
\end{description}
\end{enumerate}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-gnezdeniSeznami.png
:name: gnezdeniSeznami
:alt: Gnezdeni seznami v LaTeXu
```
````
`````

:::

Paket [`enumitem`](https://ctan.org/pkg/enumitem?lang=en) (v ang.), nam omogoča prilagoditev videza seznamov.
Na primer, lahko spremenimo oznake neurejenih seznamov ali prilagodimo zamik elementov seznama.
Za uporabo tega paketa ga moramo naložiti v preambuli z ukazom `\usepackage{enumitem}`.
Ko smo naložili paket, lahko uporabimo seznam lastnosti po začetku ustreznega okolja.

Možnosti uporabe tega paketa so ogromne in vključujejo prilagajanje oznak, boljši razmik med seznami, sezname v vrstici, različne sloge za opisne sezname in drugo. Tukaj bomo obravnavali le nekaj osnovnih primerov.

:::{prf:example}
:label: latexUvod_enumitem-1

`````{tab-set}
````{tab-item} LaTeX
```latex
Z uporabo možnosti \texttt{label=\textbackslash alph*)} lahko uporabljamo črke namesto številk:
\begin{enumerate}[label=\alph*)]
\item Z možnostjo \texttt{label=\textbackslash textit\{(\textbackslash roman*)\}}, dobimo \textit{(i)}, \textit{(ii)}, \textit{(iii)} \dots
\item Podobno, z možnostjo \texttt{label=\textbackslash textbf\{\textbackslash Alph*.\}}, dobimo \textbf{A.}, \textbf{B.}, \textbf{C.}...
\end{enumerate}

Lahko spremenimo oznake neurejenih seznamov.
\begin{itemize}[label=\heartsuit]
\item Tukaj uporabljamo \texttt{label=\textbackslash heartsuit}.
\item Z možnostjo \texttt{label=\textbackslash textendash} dobimo pomišljaj.
\item Z možnostjo \texttt{label=\textbackslash textasteriskcentered} dobimo zvezdico.
\end{itemize}

Z uporabo možnosti \texttt{style=nextline} lahko dosežemo, da se opisi začnejo v novi vrstici:
\begin{description}[style=nextline]
\item[Jabolko] Rdeče ali zeleno sadje.
\item[Pomaranča] Okroglo oranžno sadje.
\end{description}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-enumitem-1.png
:name: enumitem-1
:alt: Prilagoditev seznamov z paketom enumitem v LaTeXu, del 1.
```
````
`````

:::

:::{prf:example}
:label: latexUvod_enumitem-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{enumerate}[label=\arabic*.]
\item  Prva točka na prvi stopnji.
\begin{enumerate}[label*=\Alph*.]
\item Prva točka na drugi stopnji.
\item Druga točka na drugi stopnji.
\end{enumerate}
\end{enumerate}

\begin{enumerate}[label=\Roman*., resume]
\item To je drugačen seznam, z rimskimi številkami.
\item Številke pa se nadaljujejo iz prejšnjega seznama.
\item Nikoli ne smete nadaljevati seznama z različnimi oznakami.
\end{enumerate}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-enumitem-2.png
:name: enumitem-2
:alt: Prilagoditev seznamov z paketom enumitem v LaTeXu, del 2.
```
````
`````

:::

Seveda, ročno nastavljanje lastnosti vsakega seznama je nevarno in v nasprotju s [filozofijo LaTeXa](#latex_filozofija).
Globalne lastnosti lahko nastavimo na naslednji način.

:::{prf:example}
:label: latexUvod_enumitem-3

`````{tab-set}
````{tab-item} LaTeX
```latex
% V preambuli:
\usepackage{enumitem}
\setlist[itemize,1]{noitemsep, topsep=0pt, label=\heartsuit}
\setlist[itemize,2]{noitemsep, topsep=0pt, label=\diamondsuit}
\setlist[enumerate,1]{label=\Alph*.}
\setlist[enumerate,2]{label*=\arabic*.}
\setlist[description]{style=nextline}
% V telesu dokumenta:
\begin{itemize}
\item Neurejeni seznami prve stopnje imajo kot oznake srčke.
\item Opazujte, kako je bil razmik nastavljen tudi globalno.
\begin{itemize}
\item Neurejeni seznami na drugi stopnji imajo diamanti.
\end{itemize}
\end{itemize}

\begin{enumerate}
\item  Prav tako smo nastavili oznake urejenih seznamov.
\begin{enumerate}
\item Zdaj tisti na drugi stopnji privzeto podedujejo oznake (e.g. A.1.)
\end{enumerate}
\end{enumerate}

\begin{description}
\item[Opisni seznami] so nastavljeni tako, da se opisi začnejo v novi vrstici.
\item[To je] zelo uporabno, kadar so opisi daljši.
\end{description}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-enumitem-3.png
:name: enumitem-3
:alt: Prilagoditev seznamov z paketom enumitem v LaTeXu, del 3.
```
````
`````

:::

:::{admonition} Opozorilo!
:class: warning
Dejstvo, da lahko sezname močno prilagodimo, še ne pomeni, da bi to morali storiti.
Na splošno bi morali izbrati slog in se ga držati.
Poleg tega je privzeti slog pogosto dovolj dober za mnoge namene.
:::
(latexOsnovnaOkolja_tabele)=

## Tabele

Tabele v LaTeXu so bile obravnavane na več načinov.
LaTeX ima zelo primitivni način obravnavanja navpično poravnanih vsebin, ki jih je mogoče enostavno pretvoriti v tabelo.
Obstaja več paketov, ki razširjajo to funkcionalnost.
Eden od prvih in najpogosteje uporabljanih je paket `array`.
Ta paket morate običajno naložiti, ko delate s tabelami.

:::{admonition} Glej tudi
:class: seealso
Obstaja veliko paketov, ki na različne načine razširjajo paket `array`.
Vsi niso medsebojno združljivi, zato njihovo podrobno raziskovanje presega obseg tega učbenika.
Vendar pa so najpogosteje uporabljane funkcionalnosti za tabele zajete v enem od naslednjih dveh virov (v angleščini):

- [Tabele — Dokumentacija Overleaf](https://www.overleaf.com/learn/latex/Tables).
- [LaTeX wikibooks — tabele](https://en.wikibooks.org/wiki/LaTeX/Tables).
:::

LaTeX uporablja okolje `tabular` za tiskanje vsebine, ki je poravnana tako navpično kot vodoravno, torej nekaj, kar je zelo podobno tabeli.
Sintaksa prva vrstica okolja je

```latex
\begin{tabular}[pos]{<poravnava stolpcev>}
```

kjer je `pos` neobvezna možnost, ki določa navpično poravnavo tabele glede na preostali del besedila (privzeto je `c`, tj. središče, Vendar sta možna tudi `b` (za dno) in `t` (za vrh)).
Argument `<poravnava stolpcev>` je niz, ki določajo številko in poravnavo stolpcev.
Možnosti za ta niz so pojasnjene v [Tabeli %s](#tab-specifikacija-stolpca). Nekatere od njih lahko zahtevajo paket `array`.

:::{list-table} Specifikacija stolpca za okolje `tabular`
:header-rows: 1
:label:tab-specifikacija-stolpca

* - Znak
  - Opis
* - `l`
  - Poravnava besedila v stolpcu na levo.
* - `c`
  - Poravnava besedila v stolpcu na sredino.
* - `r`
  - Poravnava besedila v stolpcu na desno.
* - `p{<širina>}`
  - Besedilo v stolpcu bo zavito, če preseže določeno širino.
* - `m{<širina>}`
  - Kot `p{<širina>}`, vendar bo besedilo navpično poravnano na sredino celice.
* - `b{<širina>}`
  - Kot `p{<širina>}`, vendar bo besedilo navpično poravnano na dno celice.

:::

:::{prf:example}

`````{tab-set}
````{tab-item} LaTeX
```latex
Tabele v \LaTeX u se lahko poravnajo na sredino:
\begin{tabular}{ll} 1&2\\3&4 \end{tabular}
na dno:
\begin{tabular}[b]{ll} 1&2\\3&4 \end{tabular}
ali na vrh:
\begin{tabular}[t]{ll} 1&2\\3&4 \end{tabular}
glede na besedilo okoli njih.
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-tabular-1.png
:name: eg-tabular-1
:alt: Poravnava tabel v LaTeXu
```
````
`````

:::

:::{prf:example}
:label: latexUvod_tabular-poravnava

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{tabular}{ l c r }
\texttt{l} & \texttt{c} & \texttt{r} \\
levo  &
središče &
desno  \\
1 & 2 & 3 \\
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-tables-lcr.png
:name: eg-tabular-4
:alt: Poravnava tabel v LaTeXu
:width: 40%
```
````
`````
:::

:::{prf:example}
``````{tab-set}
````{tab-item} LaTeX
```latex
\begin{tabular}{ l p{2cm} m{2cm} b{2cm}}
\hline
\texttt{l} & \texttt{p\{2cm\}} & \texttt{m\{2cm\}} & \texttt{b\{2cm\}} \\
\hline
Celica &
Vrh besedila je poravnan s celico. &
Središče besedila je poravnan s celico. &
Dno besedila je poravnan s celico. \\\hline
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-tabular-3.png
:name: eg-tabular-3
:alt: Poravnava tabel v LaTeXu
:width: 70%
```
````
```````

:::

Za ločevanje stolpcev v tabeli uporabimo znak `&`, za začetek nove vrstice pa ukaz `\\`.
Če želimo navpično črto med stolpci, uporabimo znak `|` v nizu `<poravnava stolpcev>`.
Za vodoravne črte, ki se raztezajo čez celotno širino tabele, uporabimo ukaz `\hline` na koncu vrstice.
Za vodoravne črte, ki se raztezajo čez določene stolpce, uporabimo ukaz `\cline{i-j}`, kjer `i` in `j` določata začetni in končni stolpec, čez katerega se črta razteza.

:::{prf:example}

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{tabular}{l|c r|}
levo& središče & desno \\ \hline
1 & 2 & 3 \\ \cline{1-1}
4 & 5 & 6 \\ \cline{2-3}
7 & 8 & 9 \\ \hline
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-tabular-2.png
:name: eg-tabular-2
:alt: Poravnava tabel v LaTeXu
:width: 50%
```
````
`````

:::

Zgoraj opisani ukazi so že dovolj za izdelavo kompleksnih tabel v LaTeXu. Vendar pa končni rezultat ni nujno lep in izgleda nekoliko zastarel.

Obstaja veliko paketov, ki razširjajo funkcionalnosti okolja `tabular`. Osredotočili se bomo na paket [`booktabs`](https://ctan.org/pkg/booktabs?lang=en), ki je zasnovan za izdelavo tabel v LaTeXu, ki so primerne za objavo. Ta paket velja za sodoben standard za izdelavo tabel v LaTeXu.

Ta paket ustvarja tabele v skladu z naslednjima dvema konvencijama:

1. Lepe tabele ne potrebujejo navpičnih črt.
2. Lepe tabele ne zlorabljajo vodoravnih črt, zlasti pa nikoli ne smemo uporabljati dvojnih vodoravnih črt.

Vse, kar je izrecno obravnavano v tej knjigi, je združljivo s paketom `booktabs`, vendar lahko nekateri drugi klasični pristopi (zlasti navpične črte na tabelah) povzročijo nepričakovane rezultate.

Najprej moramo naložiti paket z ukazom `\usepackage{booktabs}` v preambuli.
Nato lahko uporabimo ukaze `\toprule`, `\midrule` in `\bottomrule` za ustvarjanje vodoravnih črt na vrhu, sredini in dnu tabele.

:::{prf:example}
:label: eg_booktabs

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{tabular}{c p{.7\textwidth}}
\toprule
Znak & Opis \\
\midrule
\texttt{l} & Poravnava besedila v stolpcu na levo. \\
\texttt{c} & Poravnava besedila v stolpcu na sredino. \\
\texttt{r} & Poravnava besedila v stolpcu na desno. \\
\texttt{p\{<širina>\}} & Besedilo v stolpcu bo zavito, če preseže določeno širino. \\
\texttt{m\{<širina>\}} & Kot \texttt{p\{<širina>\}}, vendar bo besedilo navpično poravnano na sredino celice. \\
\texttt{b\{<širina>\}} & Kot \texttt{p\{<širina>\}}, vendar bo besedilo navpično poravnano na dno celice. \\
\bottomrule
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-booktabs.png
:name: eg-booktabs
:alt: Tabele v LaTeXu s paketom booktabs
```
````
`````

:::

:::{exercise}
:label: ex_booktabs_1
Naslednjo tabelo reproducirajte v LaTeXu.

```{figure} ./img/02_ex-tabular-1.png
:name: ex-tabular-1
:alt: Tabela v LaTeXu s paketom booktabs
:width: 60%
```

:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_booktabs_1
:class: tip, dropdown
Tukaj je koda, ki jo morate uporabiti za ustvarjanje tega izhoda.

```latex
\begin{tabular}{ l c l }
\toprule
Oseba & Obraz & Razpoloženje \\
\midrule
Jaz & :) & Vesel \\
Vi & :| & Zaskrbljen \\
Svoj partner & :( & Žalosten \\
\bottomrule
\end{tabular}
```

:::

Simbol `@{sep}` lahko uporabimo za vstavljanje vsebine _med stolpce_. Tukaj je `sep` niz, ki bo vstavljen med celice ustreznih stolpcev.
Ta sintaksa je uporabna za vstavljanje dodatnega prostora med stolpci z uporabo ukaza `\hspace{<širina>}` kot vrednost za niz `sep`.
Lahko jo uporabimo tudi za vstavljanje posebnih znakov.
Naslednji primer naj pojasni ta koncept.

:::{prf:example}
:label: eg_booktabs-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{tabular}
{ l @{\hspace{1cm}}  r @{,} l @{ €}}
\toprule
Izdelek & \multicolumn{2}{c}{Cena}\\
\midrule
Espresso & 1&50 \\
Kava z mlekom & 2&50 \\
Čaj & 1&80 \\
\bottomrule
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-booktabs-multicolumn.png
:name: eg-booktabs-multicolumn
:alt: Tabele v LaTeXu s paketom booktabs in ukazom multicolumn
:width: 70%
```
````
`````

:::

Ukaz `\multicolumn{n}{<poravnava>}{besedilo}` združi `n` stolpcev v en stolpec, ki vsebuje `besedilo` in je poravnan glede na `<poravnava>`.
Ta ukaz je uporaben, kadar želimo, da se besedilo razteza čez več stolpcev, na primer za naslove stolpcev.

:::{exercise}
:label: ex_booktabs_2
Naredite kopijo tabele, ki ste jo ustvarili v {numref}`vaji {number} <ex_booktabs_1>` in jo uredite tako, da bo izgledala kot spodnja.

```{figure} ./img/02_ex-booktabs-2.png
:name: ex-tabular-2
:alt: Tabela v LaTeXu s paketom booktabs
:width: 60%
```

:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_booktabs_2
:class: tip, dropdown
Tukaj je možna rešitev.

```latex
\begin{tabular}{ l c l }
\toprule
Oseba & Obraz & Razpoloženje \\
\midrule
Jaz & :) & Vesel \\
Vi & :| & Zaskrbljen \\
Svoj partner & \multicolumn{2}{c}{Ni na voljo} \\
\bottomrule
\end{tabular}
```

:::

Delno vodoravno črto iz stolpca `i` v stolpec `j` natisnemo z ukazom `\cmidrule{i-j}`. To je podobno ukazu `\cline`, ki smo ga preučili prej, vendar je del paketa `booktabs`.
Črta, ki jo dobimo, je tanjša in izgleda bolj estetsko.

:::{exercise}
:label: ex_booktabs_3
Naredite kopijo tabele, ki ste jo ustvarili v {numref}`vaji {number} <ex_booktabs_2>` in jo uredite tako, da bo izgledala kot spodnja.

```{figure} ./img/02_ex-booktabs-3.png
:name: ex-tabular-3
:alt: Tabela v LaTeXu s paketom booktabs
:width: 60%
```

:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_booktabs_3
:class: tip, dropdown
Tukaj je možna rešitev.

```latex
\begin{tabular}{ l c l }
\toprule
& \multicolumn{2}{c}{Reakcija} \\\cmidrule{2-3}
Oseba & Obraz & Razpoloženje \\
\midrule
Jaz & :) & Vesel \\
Vi & :| & Zaskrbljen \\
Svoj partner & \multicolumn{2}{c}{Ni na voljo} \\
\bottomrule
\end{tabular}
```

:::

Včasih potrebujemo, da se celica razteza čez več vrstic (v nasprotju z več stolpci). To je mogoče v LaTeXu, ko naložimo paket [`multirow`](https://ctan.org/pkg/multirow?lang=en).
Ta paket nam omogoča uporabo ukaza `\multirow`, ki ima naslednjo sintakso.

```latex
\multirow[np]{<štVrstic>}{<širina>}[nGibanje]{besedilo}
```

kjer je `np` navpična poravnava celice glede na preostali del besedila (privzeto je `c`, tj. središče, vendar sta možna tudi `b` (za dno) in `t` (za vrh)).
Argument `štVrstic` je število vrstic, čez katere se celica razteza, `širina` pa širina celice (lahko uporabimo `*`, da LaTeX sam določi širino ali `=` za enako kot stolpec, v tem primeru, da je stolpec določen z `p{<širina>}`, `m{<širina>}` ali `b{<širina>}`).
Neobvezni argument `nGibanje` določa navpično premikanje besedila v celici (privzeto je `0pt`, kar pomeni, da je besedilo navpično poravnano na sredino celice).
Nazadnje je `besedilo` vsebina celice.

Za razliko od ukaza `\multicolumn`, ukaz `\multirow` ne nadomesti celic v vrsticah, ki jih pokriva. 
To pomeni, da moramo v teh vrsticah pustiti prazne celice (tj. uporabiti `&` za ločevanje stolpcev, vendar brez vsebine med njimi).

:::{exercise}
:label: ex_booktabs_4
Ustvarite še eno kopijo tabele in jo uredite tako, da dobite spodnjo tabelo. Ne pozabite naložiti paketa `multirow`.

```{figure} ./img/02_ex-booktabs-4.png
:name: ex-tabular-4
:alt: Tabela v LaTeXu s paketom booktabs
:width: 60%
```

:::

```{margin}
[Seznam vaj](#latexOsnovnaOkolja_vaje)
```

:::{solution} ex_booktabs_4
:class: tip, dropdown
Tukaj je možna rešitev.

```latex
\begin{tabular}{ l c l }
\toprule
\multirow{2}{*}{Oseba} & \multicolumn{2}{c}{Reakcija} \\\cmidrule{2-3}
& Obraz & Razpoloženje \\
\midrule
\multirow{2}{*}{Mi} & :) & Vesel \\
& :| & Zaskrbljen \\
Svoj partner & \multicolumn{2}{c}{Ni na voljo} \\
\bottomrule
\end{tabular}
```

:::

Ko je treba stolpec oblikovati na določen način, je neprijetno v vsako celico vstaviti iste ukaze.
Poleg tega, če se odločite, da je treba nekaj spremeniti v oblikovanju, bi morali vsako celico urediti posebej.
Da bi se temu izognili, paket array
opredeljuje `>{〈ukazi〉}` in `<{〈ukazi〉}` specifikacije stolpcev, ki se lahko uporabijo
za vstavljanje kode pred in za stolpec.

:::{prf:example}
:label: eg_tables_cmdCols

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{tabular}{ >{ \bfseries } l  >{\mdseries } p{0.6\textwidth} }
\toprule
Krepko besedilo & Navadno besedilo \\
\midrule
Krepko besedilo & Besedilo v prvem stolpcu je krepko. \\
Krepko besedilo & Besedilo v prvem stolpcu je vedno krepko. \\
Krepko besedilo & Res! Besedilo v prvem stolpcu je vedno krepko. \\
\bottomrule
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-tables-cmdCols.png
:name: eg-tables-cmdCols
:alt: Ukazi za stolpce v tabelah v LaTeXu
:width: 80%
```
````
`````

:::

Čeprav je uporaba ukazov `>{...}` in `<{...}` priročna, če imamo samo en tak stolpec, postane hitro neprijetna, ko se v kateri koli tabeli pojavi več stolpcev istega tipa.
V tem primeru je morda zaželeno uporabiti ukaz

```latex
\newcolumntype{<ime>}{<definicija>}
```

za definiranje nove vrste stolpca, ki ga lahko uporabimo v okolju `tabular`.
Tukaj je `<ime>` ime nove vrste stolpca (ena črka), `<definicija>` pa je definicija vrste stolpca, ki lahko vključuje ukaze `>{...}` in `<{...}`.

:::{prf:example}
:label: eg_tables_newCol

`````{tab-set}
````{tab-item} LaTeX
```latex
\newcolumntype{S}{>{\ttfamily} c  <{\normalfont}} % Definicija novega tipa stolpca S
\begin{tabular}{ S p{0.4\textwidth} }
\toprule
Ukaz & Opis \\
\midrule
to je  & S uporaba novega tipa stolpca \texttt{S}\\
vedno v & je besedilo v prvem stolpcu prikazano v  \\
strojepisni pisavi & \texttt{strojepisni} pisavi. \\
\bottomrule
\end{tabular}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-tables-newCol.png
:name: eg-tables-newcol
:alt: Ukazi za stolpce v tabelah v LaTeXu
:width: 80%
```
````
`````

:::

:::{admonition} Glej tudi!
:class: seealso

Ukazi, opisani v tem razdelku, so dovolj za izdelavo lepih tabel v LaTeXu.
Vendar pa obstaja veliko paketov, ki razširjajo funkcionalnosti okolja `tabular`.
Če bralca zanimajo bolj napredne funkcije, naj si ogleda naslednje vire (v angleščini):

- Paket [`longtable`](https://ctan.org/pkg/longtable?lang=en). za tabele, ki se raztezajo čez več strani: [dokumentacija]
- Paket [`colortbl`](https://ctan.org/pkg/colortbl?lang=en) za barvne tabele.
- Paket [`tabularx`](https://ctan.org/pkg/tabularx?lang=en) za tabele, ki se prilagajo širini strani.
:::

(latexOsnovnaOkolja_slike)=

## Slike

LaTeX sam po sebi ne podpira vključevanja slik, vendar pa to omogoča paket [`graphicx`](https://ctan.org/pkg/graphicx?lang=en).
Ta paket moramo naložiti v preambuli z ukazom `\usepackage{graphicx}`.
Nato lahko uporabimo ukaz `\includegraphics` za vključevanje slik v dokument.
Ta ukaz ima naslednjo sintakso.

```latex
\includegraphics[<lastnosti>]{<pot do slike>}
```

kjer je `<pot do slike>` pot do datoteke s sliko (relativna ali absolutna). Datoteka slike je lahko v različnih formatih, vendar so najbolj podprti formati `.png`, `.jpeg` in `.pdf`.
Lahko izpustite končnico datoteke in LaTeX bo poskusil naslednje (v tem vrstnem redu): `.pdf`, `.png`, `.jpg`, `.mps`, `.jpeg`, `.jbig2`, `.jb2`.

Neobvezni argument `<lastnosti>` je seznam lastnosti, ki jih želimo uporabiti pri vključitvi slike.
Najpogosteje uporabljena lastnost sta `width` in `height`, ki določata širino oz. višino slike. Če samo ena od teh lastnosti določi, bo druga samodejno prilagojena, da ohrani razmerje stranic slike.

:::{prf:example}
:label: eg-slike-includegraphics-widthHeight

`````{tab-set}
````{tab-item} LaTeX
```latex
\includegraphics[width=2cm]{./macka.jpeg}
\includegraphics[height=2cm]{./macka.jpeg}
\includegraphics[width=2cm,height=2cm]{./macka.jpeg}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-slike-includegraphics-widthHeight.png
:name: slike-includegraphics-widthHeight
:alt: Vključevanje slik v LaTeXu
```
````
`````

:::

Namesto ročnega določanja širine ali višine slike lahko uporabimo tudi možnosti `scale` za povečanje ali pomanjšanje slike za določen faktor.
Prenos negativnih vrednosti bo zrcalil sliko.

:::{prf:example}
:label: eg-slike-includegraphics-scale

`````{tab-set}
````{tab-item} LaTeX
```latex
\includegraphics[scale=0.2]{./macka.jpeg}
\includegraphics[scale=0.1]{./macka.jpeg}
\includegraphics[scale=-0.1]{./macka.jpeg}
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-slike-includegraphics-scale.png
:name: slike-includegraphics-scale
:alt: Vključevanje slik v LaTeXu
```
````
`````

:::

Če želimo sliko zavrteti, lahko uporabimo možnost `angle`, ki določa kot vrtenja v stopinjah (v nasprotni smeri urinega kazalca).
Privzeto je slika zavrtana okoli svojega spodnjega levega kota, vendar lahko uporabimo možnost `origin`, da spremenimo to točko.
Možne vrednosti za `origin` so `c` (središče), `l` (levo), `r` (desno), `t` (zgoraj), `b` (spodaj) in kombinacije teh vrednosti, kot so `lt` (levo zgoraj), `rb` (desno spodaj) itd.

:::{prf:example}
:label: eg-slike-includegraphics-angle

`````{tab-set}
````{tab-item} LaTeX
```latex
\lipsum[1][3] \includegraphics[width=1cm, angle=45]{./macka.jpeg} \lipsum[1][4]

\lipsum[1][3] \includegraphics[width=1cm,   angle=180]{./macka.jpeg} \lipsum[1][4]

\lipsum[1][3] \includegraphics[width=1cm, angle=180, origin=c]{./macka.jpeg} \lipsum[1][4]

\lipsum[1][3] \includegraphics[width=1cm, angle=180, origin=lt]{./macka.jpeg} \lipsum[1][4]
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-slike-includegraphics-angle.png
:name: slike-includegraphics-angle
:alt: Vključevanje slik v LaTeXu
```
````
`````

:::

## Plavajoči elementi

Če poskusite napisati daljši tekst z več tabelami in slikami, boste kmalu opazili problem: vključitev teh elementov v običajni tekstovni tok bo povzročila veliko praznega prostora.

Poglejmo naslednji primer:

:::{prf:example}
:label: eg-floating-1

`````{tab-set}
````{tab-item} LaTeX
```latex
\lipsum[1-3]
\begin{Center}
\includegraphics[width=5cm]{./macka.jpeg}
\end{Center}
\lipsum[4-6]
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-floating-1.png
:name: fig-floating-1
:alt: Problem z vključitvijo slik v LaTeXu
```
````
`````

:::

V privi strani je veliko praznega prostora, ki ga povzroča slika.
Da bi se temu izognili, LaTeX ponuja koncept plavajočih elementov, ki vključuje slike in tabele.
Plavajoči elementi so lahko postavljeni na najbolj primerno mesto v dokumentu, ne da bi motili besedilo.

LaTeX ponuja dve okolji za plavajoče elemente: `figure` za slike in `table` za tabele.
Ta okolja imajo podobno sintakso.

```latex
\begin{figure}[<pozicija>]
%...Vsebina slike, običajno z ukazom \includegraphics...
\end{figure}

\begin{table}[<pozicija>]
%... Vsebina tabele, običajno z okoljem tabular...
\end{table}
```

kjer je `<pozicija>` neobvezna možnost, ki določa, kje naj LaTeX poskuša postaviti plavajoči element.
Možne vrednosti so v [Tabeli %s](#tab-floating-positions).

:::{list-table} Pozicije plavajočih elementov
:header-rows: 1
:label: tab-floating-positions

* - Oznaka
  - Objekt lahko stoji...
* - `h`
  - tukaj, na mestu, kjer je definiran v besedilu (samo za majhne elemente).
* - `t`
  - na vrhu strani.
* - `b`
  - na dnu strani.
* - `p`
  - na posebni strani, ki vsebuje samo plavajoče elemente.
* - `!`
  - brez upoštevanja večine vgrajenih parametrov, ki bi lahko preprečile, da je objekt postavljen na to mesto.
:::

Na primer, `\begin{table}[!hbp]` pomeni, da naj LaTeX poskuša postaviti tabelo tukaj, če je mogoče (`h`), sicer na dno strani (`b`), če to ni mogoče, pa na posebno stran samo za plavajoče elemente (`p`); to vse pa lahko naredi tudi, če rezultat ni najlepši možen (`!`).
Če ne podamo nobene možnosti, LaTeX privzeto uporabi `tbp`.

Z ukazom `\caption{<pojasnilo>}` lahko dodamo pojasnilo plavajočemu elementu.
Ta ukaz mora biti znotraj okolja `figure` ali `table`.
Oštevilčenje in niz "Table" oziroma "Figure" se dodata samodejno.
Seveda, če smo v preambuli spremenili jezik dokumenta z ukazom `\usepackage[<jezik>]{babel}`, se bosta spremenila tudi ta niza.
Običajno uporabljuamo ukaz `\centering` znotraj okolja `figure` ali `table`, da centriramo vsebino.

:::{prf:example}
:label: eg-floating-2

`````{tab-set}
````{tab-item} LaTeX
```latex
\lipsum[1-3]
\begin{figure}
\centering
\includegraphics[width=5cm]{./macka.jpeg}
\caption{To je lepa mehiška mačka.}
\end{figure}
\lipsum[4-6]
```
````
````{tab-item} PDF
```{figure} ./img/02_eg-floating-2.png
:name: slika-floating-2
:alt: Problem z vključitvijo slik v LaTeXu
```
````
`````

:::

S ukazi `\listoftables` in `\listoffigures` lahko ustvarimo seznam tabel oziroma seznam slik, podobno kot z ukazom `\tableofcontents` za kazalo vsebine.
Če uporabljamo dolga pojasnila, lahko podobno kot pri naslovih logičnih enot kot dodatni argument zapišemo kratko pojasnilo, ki se bo pojavilo v seznamu tabel oziroma seznamu slik:

```latex
\caption[<kratko pojasnilo>]{<dolgo pojasnilo>}
```

Včasih želimo vključiti več slik skupaj. To lahko storimo z uporabo paketa `subcaption`.
Ta paket nam omogoča uporabo okolja `subfigure` znotraj okolja `figure`.
Vsaka podslika lahko ima svoje pojasnilo z ukazom `\caption{<pojasnilo>}`.
Celotna figura lahko ima tudi svoje pojasnilo z ukazom `\caption{<pojasnilo>}` znotraj okolja `figure`.
Okolje `subfigure` ima podobno sintakso kot okolje `figure`, vendar mora imeti tudi obvezni argument, ki določa širino podslike.

:::{prf:example}
:label: eg-floating-3
`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{figure}
\centering
\begin{subfigure}{0.4\textwidth}
\centering
\includegraphics{./macka.jpeg}
\caption{Mačka}
\end{subfigure}
\hfill
\begin{subfigure}{0.4\textwidth}
\centering
\includegraphics{./pes.jpg}
\caption{Kuža}
\end{subfigure}
\caption{Pojaznilo za obe podsliki}
\end{figure}
```
````

````{tab-item} PDF
```{figure} ./img/02_eg-floating-3.png
:name: slika-floating-3
:alt: Podslike v LaTeXu
```
````
`````
:::

Ukaz `\centering` znotraj okolja figure obravnava obe sliki kot eno samo sliko.
Na splošno je dobro uporabiti relativne dolžine za razporeditev slik. V tem primeru določamo, da je vsaka podslika 40 % širine strani.
Ukaz `\hfill` med podslikama vstavi vodoravni prostor, ki se razteza, da zapolni prostor med njima. 
Namesto `\hfill` lahko uporabimo tudi `\hspace{<širina>}`, da vstavimo fiksno širino prostora med podslikama.
Podnaslovi se ne prikažejo pri tiskanju seznama slik (z uporabo ukaza `\listofigures`), temveč le napisi, povezani s sliko.
Okolje `subfigure` ima tudi neobvezni argument, ki določa pozicijo podslike glede na slike okoli nje; množne vrednosti so `t`, `b` in `c` (za vrh, dno, sredino).

Podobno kot podslike lahko ustvarimo tudi podtabele z uporabo okolja `subtable` znotraj okolja `table`. 
Uporaba je enaka kot pri podslikah, ampak ni priporočljiva.
Za razliko od slik, skoraj ni primerov, ko bi imeli dve tabeli pod istim naslovom boljšo berljivost kot pod različnimi naslovi. 


:::{exercise}
:label: ex_plavajoce
1. Uporabite vsaj tri tabele in vsaj dve sliki, ki smo jih danes ustvarili, in jih spremenite v plavajoče elemente. To pomeni, da jih morate vključiti v okolja `figure` ali `table`.
1. Ne pozabite dodati pojasnilo k vsaki od njih.
1. Uporabite ukaz `\lipsum`, da dodate lažno besedilo okoli njih (pazite, to ne pomeni znotraj okolij `figure` ali `table`, ampak pred in po njih).
1. Po potrebi vključite nekaj razdelki in podrazdelki.
Natisnite kazalo, pa tudi seznam slik in tabel.
1. Na koncu bi morali dobiti dokument, ki izgleda zelo profesionalno, čeprav je njegova vsebina večinoma lažno besedilo.
:::



(latexOsnovnaOkolja_vaje)=
## Vaje


- [Vaja %s](#ex_razdelki): Ustvarite dokument z več razdelki in podrazdelki.
- [Vaja %s](#ex_poravnava): Ustvarite tabelo z različnimi poravnavami stolpcev in vrstic.
- [Vaja %s](#ex_seznami): Ustvarite različne vrste seznamov (oštevilčene, neoštevilčene, opisne).
- [Vaja %s](#ex_booktabs_1): Ustvarite tabelo s paketom `booktabs`.
- [Vaja %s](#ex_booktabs_2): Uredite tabelo iz prejšnje vaje z uporabo ukaza `\multicolumn`.
- [Vaja %s](#ex_booktabs_3): Uredite tabelo iz prejšnje vaje z uporabo ukaza `\cmidrule`.
- [Vaja %s](#ex_booktabs_4): Uredite tabelo iz prejšnje vaje z uporabo ukaza `\multirow`. 
- [Vaja %s](#ex_plavajoce): Ustvarite dokument z vsaj tremi tabelami in dvema slikama kot plavajoče elemente.


<!-- :::{exercise} Domača naloga
:nonumber: 

::: -->
