<!-- TODO: slike, ki jih je treba ponovno ustvariti
- img/03_eg-sklici-1.png: "S uporabo" -> "Z uporabo"
- img/03_eg-sklici-3.png: "poszabite" -> "pozabite"
- img/03_eg-literatura-4.png: naslov "s Fiziko" -> "s fiziko"; drugi naslov zdaj "povezanih z \LaTeX-om"
- img/03_eg-literatura-heading-7.png: odstavek mora ustrezati kodi ("Ta besedilo", "uporabljam" sta napačna)
-->

(03_latex_literatura)=
# Sklicevanje in literatura

:::{admonition} Cilji poglavja
:class: tip
Po tem poglavju boste znali:

- s paketom `hyperref` spremeniti kazalo in sklice v klikljive povezave,
- z ukazi `\label`, `\ref`, `\pageref` in `\nameref` se sklicevati na razdelke, slike, tabele in točke seznamov,
- sestaviti datoteko `.bib` in literaturo urediti s paketom `biblatex`,
- izbrati slog citiranja ter prilagoditi naslov, razvrščanje in filtre seznama literature.

Predvideni čas: 2 do 3 pedagoške ure.
:::

Z LaTeXom lahko oblikujemo dokumente visoke kakovosti za tisk. Vendar pa danes veliko dokumentov beremo na zaslonu računalnika ali mobilne naprave. 
Paket [`hyperref`](https://ctan.org/pkg/hyperref) omogoča ustvarjanje dokumentov PDF z aktivnimi povezavami oz. _hiperpovezavami_.
To pomeni, da lahko kliknemo na sklic in nas ta pripelje do ustreznega dela dokumenta ali na zunanjo spletno stran.
Paket `hyperref` poskrbi tudi, da so vnosi v kazalu klikljivi, in v datoteko PDF doda zaznamke (ang. _bookmarks_), ki omogočajo enostavno navigacijo po dokumentu.

V tem poglavju bomo paket `hyperref` uporabili za klikljive sklice na razdelke, slike, tabele in literaturo. 
Seveda moramo paket najprej naložiti v preambuli našega dokumenta:

```latex
\usepackage{hyperref}
``` 

:::{admonition} Pazite!
:class: warning
Paket `hyperref` naložimo kot zadnji paket v preambuli. Spreminja namreč ukaze mnogih drugih paketov, zato lahko povzroči konflikte, če ga naložimo prej.
Redki paketi (npr. [`cleveref`](https://ctan.org/pkg/cleveref)) morajo biti naloženi za njim, kar je vedno zapisano v njihovi dokumentaciji.
:::

:::{exercise} 
:label: ex_hyperref
1. Napišite minimalni dokument LaTeX, ki vsebuje vsaj tri razdelke in v vsakem razdelku nekaj podrazdelkov. **Paketa `hyperref` še ne nalagajte.**
2. Dodajte v dokument dovolj besedila, da bo obsegal več strani in bodo razdelki na različnih straneh. Uporabite lahko ukaz `\lipsum` iz paketa `lipsum`, ki ustvari nadomestno besedilo.
3. Natisnite kazalo vsebine z ukazom `\tableofcontents`. 
4. Na konec preambule dodajte paket `hyperref` in dokument ponovno prevedite. Poglejte kazalo in kliknite na enega od vnosov. Kaj se zgodi?
:::


:::{margin}
[Seznam nalog](#latexLiteratura_vaje)
:::

:::{solution} ex_hyperref
:class: tip dropdown
Tukaj je primer, kako bi lahko bil videti vaš dokument po vseh korakih.

```latex
\documentclass{article}
\usepackage[slovene]{babel}
\usepackage{lipsum}
\usepackage{hyperref} % Hiperpovezave, naložen kot zadnji

\begin{document}

\tableofcontents

\section{Drugi razdelek}
\lipsum[4-6]
\subsection{A je to podrazdelek?}
\lipsum[7]
\subsection{Ja, to je podrazdelek!}
\lipsum[8-10]

\section{Prvi razdelek}
\lipsum[1-3]
\subsection*{Podrazdelek brez številke}
\lipsum[11-13]

\section[Tretji razdelek]{Tretji razdelek z dolgim naslovom, ki se razteza čez več vrstic}
\lipsum[14-15]


\end{document}
```

<!-- TODO: write about \hypersetup{...} options for customizing link colors, etc. -->
<!-- TODO: write about \footnote options for customizing link colors, etc. -->



:::

## Sklicevanje

V dokumentu se lahko sklicujemo na različne elemente, kot so slike, tabele, enačbe, razdelki itd. 
Za sklicevanje uporabimo ukaza `\label{<oznaka>}` in `\ref{<oznaka>}`.
Ukaz `\label{<oznaka>}` postavimo takoj za ukaz, ki elementu dodeli številko (npr. za `\section{...}`). Ukaz `\ref{<oznaka>}` pa uporabimo na mestu, kjer želimo vstaviti sklic. Argument `<oznaka>` je poljuben niz znakov, ki ga izberemo sami, vendar mora biti edinstven v celotnem dokumentu.

::::::{prf:example}
:label: eg_sklici_1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass{article}
\usepackage[slovene]{babel}

\usepackage{hyperref} % Hiperpovezave


\begin{document}

\section{Sklicevanje}
\label{sec:sklicevanje}

Z uporabo ukaza \texttt{\textbackslash label\{sec:sklicevanje\}} 
smo označili ta razdelek, nanj pa se lahko sklicujemo 
z ukazom \texttt{\textbackslash ref\{sec:sklicevanje\}}. 

Na primer, v razdelku~\ref{sec:sklicevanje} smo 
predstavili sklicevanje na različne elemente v dokumentu.

\end{document}
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-sklici-1.png
:label: fig:sklici_1
:alt: Razdelek 1 z naslovom Sklicevanje in dvema odstavkoma, v drugem je sklic na razdelek izpisan kot številka 1 v rdečem okvirju.
:::
::::
:::::

::::::

Rdeči okvir okoli številke je privzeti videz povezav paketa `hyperref`. Na zaslonu nas opozori, da lahko na sklic kliknemo, v natisnjenem dokumentu pa se ne vidi.

:::{admonition} Opomba
:class: note
LaTeX številke sklicev izve šele med prevajanjem, zato je treba dokument prevesti dvakrat: ob prvem prevajanju oznake zbere, ob drugem jih vstavi na pravo mesto. Do takrat se namesto številke izpiše `??`.
Če `??` ostane tudi po ponovnem prevajanju, smo se v oznaki zatipkali ali pa je sploh nismo definirali. Na to nas opozori tudi opozorilo `LaTeX Warning: Reference ... undefined`.
:::

:::{admonition} Nasvet!
:class: tip
Oznake je priporočljivo oblikovati tako, da so opisne, a kratke. Na primer, za razdelek o sklicevanju je `sec:sklicevanje` boljša oznaka kot `s1` ali `razdelek1`.

Dobra praksa je tudi, da uporabljamo predpone za različne vrste elementov, kot so `sec:` za razdelke, `fig:` za slike, `tab:` za tabele in `eq:` za enačbe.
:::

:::{admonition} Opomba
:class: note
Ukaz `\ref` vrne le številko elementa, na primer številko razdelka ali slike. Besedilo, kot je "razdelek", "slika" ali "tabela", moramo pred številko dodati ročno.
Med besedo in ukazom `\ref` uporabimo nedeljivi presledek `~`, ki smo ga spoznali v poglavju [](./01_latexUvod.md), npr. `na sliki~\ref{fig:macka}`. Tako številka ne bo ostala sama na začetku nove vrstice.

Obstajajo paketi, kot je [`cleveref`](https://ctan.org/pkg/cleveref), ki besedilo pred številko dodajo samodejno. Paket `cleveref` na žalost ne podpira slovenskega jezika. Nove jezike je sicer mogoče definirati, vendar je slovenščino težko podpreti zaradi sklanjatev (prim. "glej slik**o** 1" in "na slik**i** 1").
:::

Če ukaz `\ref{<oznaka>}` uporabimo za razdelek "z zvezdico" (npr. `\section*{...}`), ki nima svoje številke, bo ukaz vrnil številko zadnjega oštevilčenega elementa pred njim ali pa nič.
Zato se na razdelke "z zvezdico" ne sklicujemo z ukazom `\ref`.
Namesto njega lahko uporabimo ukaz `\nameref{<oznaka>}`, ki vrne naslov razdelka. Ukaz `\nameref` nam da paket `hyperref`, zato deluje le, če je ta naložen.

Ukaz `\pageref{<oznaka>}` vrne številko strani, na kateri se nahaja element z dano oznako. 
Ta ukaz lahko uporabimo tudi z razdelki "z zvezdico", saj ne potrebujemo številke razdelka, ampak le številko strani.

Pri plavajočih elementih, kot so slike in tabele, oznako vedno postavimo znotraj okolja `figure` ali `table`, takoj za ukaz `\caption{...}`.
Številko slike ali tabele namreč ustvari šele ukaz `\caption`. Če oznako postavimo pred njim, se bo `\ref` skliceval na številko trenutnega razdelka in ne na sliko.


::::::{prf:example}
:label: eg_sklici_2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{figure}
\centering
\includegraphics{macka}
\caption{Slika čudovite mačke.}
\label{fig:macka}
\end{figure}
%...
Na sliki~\ref{fig:macka} na strani~\pageref{fig:macka} vidimo lepo mačko.
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-sklici-2.png
:label: fig:sklici_2
:alt: Mačka s sombrerom in podnapisom Slika 1, pod njo stavek, v katerem sta številka slike in številka strani izpisani v rdečih okvirjih.
:::
::::
:::::

::::::

Označimo in se sklicujemo lahko na vse, čemur LaTeX dodeli številko, na primer na točke v oštevilčenih seznamih ali na enačbe (več o tem v poglavju [](./04_latexMatematika.md)).

::::::{prf:example}
:label: eg_sklici_3

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\begin{enumerate}
\item Oblecite nogavice.
\item \label{itm:cevlje} Obujte čevlje.
\item Pojdite na sprehod.
\end{enumerate}
%...
V koraku~\ref{itm:cevlje} ne pozabite zavezati vezalk.
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-sklici-3.png
:label: fig:sklici_3
:alt: Oštevilčen seznam treh korakov in stavek, ki se na drugi korak sklicuje s številko 2 v rdečem okvirju.
:width: 60%
:align: left
:::
::::
:::::

::::::

:::{exercise}
:label: ex_sklici
1. V dokument, ki ste ga napisali v [Nalogi %s](#ex_hyperref), dodajte slike in tabele z oznakami. Uporabite lahko tabele in slike, ki ste jih ustvarili v poglavju [](./02_latexOsnovnaOkolja.md).
2. V besedilu se na vsako sliko in tabelo sklicujte z ukazom `\ref`, na vsaj eno pa tudi z ukazom `\pageref`.
3. Na razdelek "z zvezdico" se sklicujte z ukazom `\nameref`.
:::

:::{margin}
[Seznam nalog](#latexLiteratura_vaje)
:::

## Literatura

### Klasični način

Za vključitev literature v dokument LaTeX lahko uporabimo okolje `thebibliography`.
To je le poseben seznam, kjer vsaka referenca dobi svojo oznako z ukazom `\bibitem{<oznaka>}`.
Nato se na referenco sklicujemo z ukazom `\cite{<oznaka>}`.
Argument okolja (v spodnjem primeru `{9}`) pove, kako široka je najširša številka v seznamu: `9` pomeni eno števko, za 10 ali več referenc napišemo `99`.

::::::{prf:example}
:label: eg_literatura_1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
Prva knjiga, ki sem jo prebral, je bila \cite{hp1}. 
% ...
\begin{thebibliography}{9}
\bibitem{hp1} J. K. Rowling, \textit{Harry Potter in kamen modrosti}, 
Založba EPTA, 1997.
\bibitem{hp2} J. K. Rowling, \textit{Harry Potter in dvorana skrivnosti}, 
Založba EPTA, 1998.
\end{thebibliography}
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-1.png
:label: fig:literatura_1
:alt: Stavek s citatom [1] in pod njim seznam Literatura z dvema knjigama o Harryju Potterju, oštevilčenima z [1] in [2].
:::
::::
:::::

::::::

Ta način je enostaven in hiter, vendar ima nekaj pomanjkljivosti:

- Ročno moramo vnašati vse podatke o referencah, kar je lahko zamudno in nagnjeno k napakam.
- Ni standardiziranega formata za vnos referenc, kar lahko vodi do neenotnosti v slogu citiranja.
- Enostavne spremembe sloga citiranja so težavne, saj moramo ročno prilagoditi vsako referenco.
- Podatki niso strukturirani: nič ne označuje, kateri del vnosa je avtor, naslov, leto izdaje itd.
- Reference se izpišejo v vrstnem redu, v katerem smo jih napisali. Če jih želimo urediti drugače (npr. po letu izdaje namesto po priimku avtorja), moramo to storiti ročno.
- Vsebina (podatki o referenci) in oblika (način izpisa) sta pomešani, kar je v nasprotju z idejo LaTeXa, da vsebino ločimo od oblike.

Zaradi teh razlogov je priporočljivo uporabiti bolj napredne metode za upravljanje literature v dokumentih LaTeX, kot sta BibTeX in BibLaTeX.

### Paket `biblatex`

BibTeX je program za upravljanje bibliografskih podatkov, ki deluje skupaj z LaTeXom.
Omogoča nam, da shranimo vse naše reference v ločeno datoteko `.bib`, kar olajša upravljanje in ponovno uporabo referenc v različnih dokumentih.
BibLaTeX (paket `biblatex`) je sodobnejša alternativa BibTeXu, ki ponuja več funkcionalnosti in prilagodljivosti. 
Uporablja enake datoteke `.bib`, le da reference namesto programa `bibtex` obdela program `biber`, za obliko izpisa pa poskrbi LaTeX sam.

Uporaba BibLaTeXa vključuje naslednje korake:

1. Ustvarimo datoteko z bibliografskimi podatki z razširitvijo `.bib`. V tej datoteki so reference shranjene v posebnem formatu.
2. V preambuli našega dokumenta LaTeX naložimo paket `biblatex` in določimo slog citiranja ter datoteko z bibliografskimi podatki.
3. V besedilu se na reference sklicujemo z ukazom `\cite` in na želenem mestu natisnemo seznam literature.

Datoteka `.bib` je sestavljena iz vnosov, kjer vsak vnos predstavlja eno referenco.
Vsak vnos ima svoj edinstven ključ, ki ga uporabimo za sklicevanje na to referenco v našem dokumentu.
Vsak vnos vsebuje različna polja, kot so avtor, naslov, leto izdaje itd., in je videti nekako takole:

```bibtex
@<vrsta_vnosa>{<ključ>,
<polje1>    = {vrednost1},
<polje2>    = {vrednost2},
<polje3>    = {vrednost3}, 
<poljeN>    = {vrednostN}, 
}
```

kjer je `<vrsta_vnosa>` lahko `book`, `article`, `inproceedings`, `online`, `misc` itd., odvisno od vrste reference.
`<ključ>` je edinstven identifikator za ta vnos, ki ga bomo uporabili v ukazu `\cite{<ključ>}` v našem dokumentu LaTeX.
`<polje1>`, `<polje2>` itd. so različna polja, ki vsebujejo informacije o referenci, kot so avtor, naslov, leto izdaje itd. Npr. za knjigo _Harry Potter in kamen modrosti_ bi bil vnos videti takole:

```bibtex
@book{hp1,
author    = {J. K. Rowling},
title     = {Harry Potter in kamen modrosti},
publisher = {Založba EPTA},
year      = {1997}
}
```

Polja so odvisna od vrste vnosa in sloga bibliografije, ki ga uporabljamo (več o tem kasneje). Za knjige so običajna polja `author`, `title`, `publisher` in `year`. Za članke v revijah bi lahko uporabili polja, kot so `journal`, `volume`, `number` in `pages`. Za spletne vire ima BibLaTeX posebno vrsto vnosa `online`, pri kateri sta uporabni polji `url` in `urldate` (datum obiska).
Celoten seznam vrst vnosov in polj najdete v dokumentaciji paketa [BibLaTeX](https://ctan.org/pkg/biblatex) ali v tem članku na [wikibooks](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#Entry_and_field_types_in_.bib_files).

Dobra novica je, da običajno ni treba ročno pisati datoteke `.bib`, saj obstajajo številna orodja in spletne strani, ki lahko samodejno ustvarijo vnose v pravilnem formatu.
Nekatera orodja, ki jih lahko uporabite za ustvarjanje in upravljanje datotek `.bib`, so:

- [Google Scholar](https://scholar.google.com/): omogoča izvoz posameznih referenc v format `.bib`.
- [COBISS](https://www.cobiss.si/): slovenski sistem za iskanje in izposojo knjižničnih gradiv, ki omogoča izvoz bibliografskih podatkov v format `.bib`.
- [ZoteroBib](https://zbib.org/): spletno orodje za hitro ustvarjanje bibliografij, ki podpira izvoz v format `.bib`.
- [MathSciNet](https://mathscinet.ams.org/mathscinet): spletna baza podatkov za matematiko, ki omogoča izvoz v format `.bib`.
- [DBLP](https://dblp.org/): baza podatkov za računalništvo, ki prav tako omogoča izvoz v format `.bib`.

Samodejno ustvarjene vnose vedno preverite, saj so pogosto nepopolni ali vsebujejo napake (to še posebej velja za Google Scholar).

Ko smo pripravili našo bazo podatkov referenc (tj. našo datoteko `.bib`, recimo `literatura.bib`), moramo v našem dokumentu LaTeX naložiti paket `biblatex` in povezati datoteko z bibliografskimi podatki.
To storimo z naslednjimi ukazi v preambuli:

```latex
\usepackage{csquotes} % Narekovaji, prilagojeni jeziku
\usepackage{biblatex} % Naloži paket biblatex
\addbibresource{literatura.bib} % Poveže datoteko z bibliografskimi podatki
```

:::{admonition} Nasvet!
:class: tip
Paket `csquotes` ni nujen, vendar ga BibLaTeX priporoča, kadar uporabljamo paket `babel`. Brez njega so naslovi člankov v seznamu literature v angleških narekovajih (“…”), prevajanje pa javi opozorilo `'babel/polyglossia' detected but 'csquotes' missing`. Z njim dobimo slovenske narekovaje (»…«).
:::

V besedilu našega dokumenta se na reference sklicujemo z ukazom `\cite{<ključ>}`, kjer je `<ključ>` ključ vnosa v naši datoteki `.bib`.
Argument `<ključ>` je lahko tudi seznam ključev, ločenih z vejico (npr. `\cite{hp1,hp2}`), če se želimo sklicevati na več referenc hkrati.

Na koncu dokumenta (ali kjerkoli že želimo natisniti seznam referenc) dodamo ukaz `\printbibliography`, ki natisne seznam vseh referenc, na katere smo se sklicevali v besedilu.
Upoštevajte, da `\printbibliography` natisne le reference, na katere smo se sklicevali z ukazom `\cite{<ključ>}`, ne pa vseh vnosov iz datoteke `.bib`.

:::{admonition} Opomba
:class: note
Za literaturo z BibLaTeXom poleg LaTeXa potrebujemo še program `biber`, ki prebere datoteko `.bib` in reference razvrsti. Overleaf ga zažene samodejno.
Če dokument prevajamo na svojem računalniku, moramo zagnati zaporedje `pdflatex`, `biber`, `pdflatex` (ali pa to prepustimo orodju `latexmk`).
Če se namesto številke citata izpiše ključ v krepki pisavi, npr. [**hp1**], `biber` še ni bil zagnan ali pa ključa ni v datoteki `.bib`.
:::

:::{exercise}
:label: ex_biblatex
1. V svojem projektu v Overleafu ustvarite datoteko z imenom `literatura.bib` in vanjo dodajte vsaj tri vnose različnih vrst (npr. knjigo, članek in spletno stran).
2. V svojem dokumentu LaTeX naložite paket `biblatex` z ukazom `\usepackage{biblatex}` v preambuli.
3. Dodajte ukaz `\addbibresource{literatura.bib}` v preambulo, da povežete datoteko z bibliografskimi podatki.
4. V besedilu uporabite ukaz `\cite{<ključ>}` za sklicevanje na vsako od referenc, ki ste jih dodali v datoteko `.bib`, razen na eno.
5. Na koncu dokumenta dodajte ukaz `\printbibliography`, da natisnete seznam referenc. Ali se v njem pojavi referenca, ki je niste citirali?
:::

:::{margin}
[Seznam nalog](#latexLiteratura_vaje)
:::

### Slogi citiranja in razvrščanje

Z BibLaTeXom lahko na nadzorovan način prilagodimo videz naših citatov in seznama literature. To storimo z izbiro sloga citiranja, ki ga določimo kot možnost pri nalaganju paketa `biblatex`.
Na primer, 
```latex
\usepackage[style=alphabetic]{biblatex}
``` 
naloži slog `alphabetic`, ki uporablja črke iz imen avtorjev in leto izdaje za označevanje citatov v besedilu. Privzeto je slog `numeric`, ki uporablja številke za označevanje citatov.
Obstaja veliko različnih slogov citiranja, ki jih lahko uporabimo, odvisno od naših potreb in preferenc. 
Obsežen seznam slogov najdete v dokumentaciji paketa [BibLaTeX](https://ctan.org/pkg/biblatex) ali na [Overleaf](https://www.overleaf.com/learn/latex/Biblatex_bibliography_styles).

:::{admonition} Pazite!
:class: warning
Možnost `style` hkrati določi slog citatov v besedilu (`citestyle`) in slog seznama literature (`bibstyle`). Oba lahko nastavimo tudi ločeno, vendar je dobro, da sta usklajena, sicer se oznake v besedilu ne ujemajo z oznakami v seznamu literature.
:::

Poleg ukaza `\cite` nam BibLaTeX ponuja še nekaj ukazov za citiranje. Kaj natisnejo, je odvisno od sloga, zato v oklepajih navajamo izpis pri slogu `numeric` in pri slogu `authoryear` (avtor in leto):

- `\cite{einstein}` natisne le oznako citata: [1] oz. Einstein 1905.
- `\parencite{einstein}` natisne citat v oklepaju: [1] oz. (Einstein 1905). Pri številčnih slogih je enak ukazu `\cite`.
- `\textcite{einstein}` natisne ime avtorja kot del stavka, oznako pa za njim: Einstein [1] oz. Einstein (1905). Uporabimo ga, ko je avtor osebek stavka, npr. `Kot je pokazal \textcite{einstein}, ...`.
- `\autocite{einstein}` izbere obliko citata glede na slog: pri slogih `numeric` in `authoryear` deluje kot `\parencite`, pri nekaterih drugih slogih (npr. `verbose`) pa citat postavi v opombo pod črto. Če dosledno uporabljamo `\autocite`, se ob zamenjavi sloga vsi citati samodejno prilagodijo.
- Vsi ti ukazi sprejmejo tudi neobvezni argument, s katerim navedemo npr. stran: `\parencite[str.~12]{einstein}` natisne [1, str. 12] oz. (Einstein 1905, str. 12).

Možnost `sorting=ynt` (npr. `\usepackage[sorting=ynt]{biblatex}`) razvrsti bibliografijo po letu izdaje (`y`), nato po avtorju (`n`) in nato po naslovu (`t`). Privzeto je `sorting=nty`, kar pomeni, da se najprej razvrsti po avtorju, nato po naslovu in nato po letu izdaje.
Z možnostjo `sorting=none` pa so reference v seznamu v vrstnem redu, v katerem smo jih prvič citirali.

Celoten seznam možnosti za razvrščanje najdete v dokumentaciji paketa [BibLaTeX](https://ctan.org/pkg/biblatex) ali na [BibLaTeX cheat sheet](https://mirrors.ctan.org/info/biblatex-cheatsheet/biblatex-cheatsheet.pdf).

### Prilagajanje seznama literature

Kot smo že omenili, ukaz `\printbibliography` natisne seznam vseh referenc, na katere smo se sklicevali v besedilu. 
Če želimo natisniti reference, na katere se nismo sklicevali, lahko uporabimo ukaz `\nocite{<ključ>}`.
Ta ukaz nam omogoča, da vključimo določene vnose v bibliografijo, tudi če se nanje nismo sklicevali v besedilu.
Če želimo vključiti vse vnose iz naše datoteke `.bib`, lahko uporabimo ukaz `\nocite{*}`. 

Ukaz `\printbibliography` lahko sprejme različne možnosti, ki nadzorujejo videz bibliografije.
Na primer, lahko uporabimo možnost `title`, da spremenimo naslov bibliografije, kot je prikazano spodaj:

::::::{prf:example}
:label: eg_literatura_2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\nocite{*} % vsi vnosi iz datoteke .bib
\printbibliography[title={Viri in literatura}]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-2.png
:label: fig:literatura_2
:alt: Seznam literature z naslovom Viri in literatura, ki vsebuje devet oštevilčenih vnosov, med njimi knjige, članke in spletni vir.
:::
::::
:::::

::::::

Reference lahko z uporabo filtrov razdelimo v več seznamov.
Na primer, lahko natisnemo samo knjige z uporabo možnosti `type=book`:

::::::{prf:example}
:label: eg_literatura_3

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[type=article,title={Samo članki}]
\printbibliography[type=book,title={Vse knjige}]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-3.png
:label: fig:literatura_3
:alt: Dva seznama literature, Samo članki z dvema člankoma in Vse knjige s šestimi knjigami. Vnosi ohranijo svoje številke iz skupnega seznama.
:::
::::
:::::

::::::

Na voljo so filtri `type`, `keyword` in `category` ter njihove negacije `nottype`, `notkeyword` in `notcategory`.
Ključne besede vnosu določimo s poljem `keywords` v datoteki `.bib`, npr. `keywords = {physics}`.
Z ukazom `\defbibfilter{<ime_filtra>}{<pogoj>}` lahko definiramo tudi svoje filtre.

::::::{prf:example}
:label: eg_literatura_4

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[keyword={physics},title={Reference, povezane s fiziko}]
\printbibliography[notkeyword={latex}, title={Vse, razen tistih, povezanih z \LaTeX-om}]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-4.png
:label: fig:literatura_4
:alt: Dva seznama literature, prvi s štirimi referencami s ključno besedo physics, drugi z vsemi referencami razen tiste s ključno besedo latex.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_5

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\defbibfilter{custom}{keyword=physics or keyword=latex}     
\printbibliography[filter=custom,title={Reference, povezane s fiziko ali \LaTeX-om}]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-5.png
:label: fig:literatura_5
:alt: Seznam literature s petimi referencami, ki imajo ključno besedo physics ali latex.
:::
::::
:::::

::::::

Privzeto se bibliografija ne prikaže v kazalu vsebine. Če želimo, da se prikaže, lahko uporabimo možnost `heading`. 
Različne vrednosti za možnost `heading` so v [Tabeli %s](#tab:heading_options).

:::{list-table} Naslov bibliografije v kazalu.
:header-rows: 1
:label: tab:heading_options

* - Vrednost
  - Opis
* - `bibliography`
  - privzeto, kot razdelek "z zvezdico" (v razredu `article` `\section*`, v razredih `book` in `report` `\chapter*`).
* - `bibintoc`
  - kot razdelek "z zvezdico", vendar se pojavi v kazalu.
* - `subbibliography`
  - naslov je za eno raven nižje v hierarhiji (`\section*` namesto `\chapter*`, `\subsection*` namesto `\section*` in tako naprej).
* - `bibnumbered`
  - običajen razdelek (brez zvezdice), torej s številko in v kazalu.
* - `subbibintoc`
  - podobno kot `subbibliography`, vendar se pojavi v kazalu.
* - `subbibnumbered`
  - podobno kot `subbibliography`, vendar brez zvezdice, torej s številko in v kazalu.
* - `none`
  - naslov se ne natisne.
:::

V spodnjih primerih ima dokument kazalo ter razdelka _Sklicevanje_ in _Literatura_, v katerih z ukazom `\nocite{*}` izpišemo vse vnose iz datoteke `.bib`. Prikazan je le ukaz `\printbibliography`.

::::::{prf:example}
:label: eg_literatura_heading_1

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[title={Literatura, privzeto}]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-1.png
:label: fig:literatura_heading_1
:alt: Kazalo z razdelkoma 1 in 2, pod njim seznam literature z neoštevilčenim naslovom, ki ga v kazalu ni.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_heading_2

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[title={Literatura, v kazalu}, heading=bibintoc]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-2.png
:label: fig:literatura_heading_2
:alt: Kazalo, v katerem je poleg razdelkov 1 in 2 tudi neoštevilčen vnos Literatura, v kazalu.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_heading_3

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[title={Literatura, kot podrazdelek -- z zvezdico --}, heading=subbibliography]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-3.png
:label: fig:literatura_heading_3
:alt: Seznam literature z neoštevilčenim naslovom v velikosti podrazdelka, ki ga v kazalu ni.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_heading_4

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[title={Literatura kot razdelek, s številko}, heading=bibnumbered]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-4.png
:label: fig:literatura_heading_4
:alt: Seznam literature kot oštevilčen razdelek 3, ki se pojavi tudi v kazalu.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_heading_5

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[title={Literatura kot podrazdelek, brez št.-a, v kazalu}, heading=subbibintoc]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-5.png
:label: fig:literatura_heading_5
:alt: Seznam literature z neoštevilčenim naslovom podrazdelka, ki se v kazalu pojavi zamaknjen pod razdelkom 2.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_heading_6

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\printbibliography[title={Literatura kot podrazdelek, s št.-o, v kazalu}, heading=subbibnumbered]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-6.png
:label: fig:literatura_heading_6
:alt: Seznam literature kot oštevilčen podrazdelek 2.1, ki se pojavi tudi v kazalu.
:::
::::
:::::

::::::

::::::{prf:example}
:label: eg_literatura_heading_7

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\section{Literatura}
To besedilo je del razdelka Literatura. Seznam referenc je natisnjen 
spodaj, vendar brez naslova, saj smo uporabili možnost 
\texttt{heading=none}.

\printbibliography[title={Čeprav napišem naslov, se nič ne natisne}, heading=none]
```
::::

::::{tab-item} PDF
:::{figure} ./img/03_eg-literatura-heading-7.png
:label: fig:literatura_heading_7
:alt: Razdelek 2 Literatura s kratkim odstavkom, ki mu sledi seznam literature brez lastnega naslova.
:::
::::
:::::

::::::


(latexLiteratura_vaje)=
## Naloge

Tukaj so naloge tretjega poglavja:

- [ ] [Naloga %s](#ex_hyperref): Kazalo s paketom `hyperref`.
- [ ] [Naloga %s](#ex_sklici): Sklicevanje na slike, tabele in razdelke.
- [ ] [Naloga %s](#ex_biblatex): Seznam literature z BibLaTeXom.


:::{exercise} Domača naloga
:label: dn_recept
:nonumber: 
1. Ustvarite nov projekt v Overleafu in v njem datoteko z imenom `DN2.tex`.
1. V njej napišite dokument LaTeX, ki vsebuje recept vaše najljubše jedi.
1. Uporabite sezname, tabele ali celo slike.
1. Uporabite sklice z ukazi `\label`, `\ref`, `\nameref` in `\pageref`. Ne pozabite naložiti paketa `hyperref`.
1. Ne pozabite, da morate tabele in slike vstaviti v plavajoče elemente in jim dodati pojasnila.
1. Z BibLaTeXom dodajte seznam literature z vsaj dvema viroma (npr. kuharsko knjigo ali spletno stran, od koder je recept) in ju v besedilu citirajte.
1. Poskusite, da bo dokument videti čim bolj profesionalno.
1. Domačo nalogo oddajte kot datoteko `.zip` prek spletne učilnice. Če ne veste, kako pridobiti datoteko `.zip` iz Overleafa, poglejte [](./B_izvozIzOverleaf.md).
:::
