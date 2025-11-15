(03_latex_literatura)=
# Sklicevanje in literatura

Z LaTeXom lahko oblikujemo ne le dokumente, ki so visoke kakovosti za tiskanje. Vendar pa je danes veliko dokumentov prebrati na zaslonu računalnika ali mobilne naprave. 
Paket [`hyperref`](https://ctan.org/pkg/hyperref) omogoča ustvarjanje dokumentov PDF z aktivnimi povezavami oz. _hiperpovezavami_.
To pomeni, da lahko kliknemo na sklic in nas ta pripelje do ustreznega dela dokumenta ali na zunanjo spletno stran.
Paket `hyperref` omogoča tudi ustvarjanje kazal, ki so interaktivni in omogočajo enostavno navigacijo po dokumentu.

Za zdaj bomo uporabili paket `hyperref` za sklicevanje na literaturo v našem dokumentu. 
Seveda, najprej moramo nalovziti paket v preambuli našega dokumenta:

```latex
\usepackage{hyperref}
``` 

:::{admonition} Pazite!
:class: warning
Paket `hyperref` mora biti naložen kot zadnji paket v preambuli, saj lahko povzroči konflikte z drugimi paketi, če ni naložen na koncu.
:::

:::{exercise} 
:label: ex_hyperref
1. Napišite minimalni dokument LaTeX, ki vsebuje vsaj tri razdelki in nekaj podrazdelkov v vsakem razdelki. **Ne naložite še paketa `hyperref`.**
2. Dodajte nekaj besedila v dokument, tako da se naslovi razdelkov in podrazdelkov raztezajo čez več strani. Lahko uporabite ukaz `\lipsum` iz paketa `lipsum` za generiranje lažnega besedila.
3. Natisnite kazalo vsebine z ukazom `\tableofcontents`. 
4. Dodajte paket `hyperref` v preambulo (na koncu) in ponovno shranite dokument. Poglej kazalo.
:::


```{margin}
[Seznam vaj](#latexLiteratura_vaje)
```

:::{solution} ex_razdelki
:class: tip, dropdown
Tukaj je primer, kako bi lahko izgledal vaš dokument po vseh korakih.

```latex
\documentclass{article}
\usepackage[slovene]{babel}
\usepackage{hyperref} % Hiperpovezave
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

<!-- TODO: write about \hypersetup{...} options for customizing link colors, etc. -->
<!-- TODO: write about \footnote options for customizing link colors, etc. -->



:::
## Sklicevanje

V dokumentu lahko sklicujemo na različne elemente, kot so slike, tabele, enačbe, razdelki, itd. 
Za sklicevanje uporabimo ukaza `\label{<oznaka>}` in `\ref{<oznaka>}`.
Ukaz `\label{<oznaka>}` postavimo takoj za element, na katere se želimo sklicevati. Ukaz `\ref{<oznaka>}` pa uporabimo na mestu, kjer želimo vstaviti sklic. Argument `<oznaka>` je poljuben niz znakov, ki ga izberemo sami, vendar mora biti edinstven v celotnem dokumentu.

:::{prf:example}
:label: eg_sklici_1
`````{tab-set}  
````{tab-item} LaTeX
```latex
\documentclass{article}\documentclass{article}
\usepackage[slovene]{babel}

\usepackage{hyperref} % Hiperpovezave


\begin{document}

\section{Sklicevanje}
\label{sec:sklicevanje}

S uporabo ukaza \texttt{\textbackslash label\{sec:sklicevanje\}} 
smo označili ta razdelek, nanj pa se lahko sklicujemo 
z ukazom \texttt{\textbackslash ref\{sec:sklicevanje\}}. 

Na primer, v razdelku \ref{sec:sklicevanje} smo 
predstavili sklicevanje na različne elemente v dokumentu.

\end{document}

```
```` 
````{tab-item} PDF
``` {figure} ./img/03_eg-sklici-1.png
:label: fig:sklici_1
```
```` 
`````
:::


:::{admonition} Nasvet
:class: tip
Oznake je priporočljivo oblikovati tako, da so opisne ampak kratke. Na primer, za razdelek o sklicevanju,`sec:sklicevanje`, je boljša oznaka kot `s1` ali `razdelek1`.

Dobra praksa je tudi, da uporabljamo predpone za različne vrste elementov, kot so `sec:` za razdelke, `fig:` za slike, `tab:` za tabele in `eq:` za enačbe.
:::

:::{admonition} Opomba
:class: note
Ukaz `\ref` vrne le številko elementa, na primer številko razdelka ali slike. Potrebno je, da ročno dodamo besedilo, kot je "Razdelek", "Slika" ali "Tabela", pred številko.

Obstajajo paketi, kot je [`cleveref`](https://ctan.org/pkg/cleveref?lang=en), ki omogočajo samodejno dodajanje besedila pred številko. Na žalost, paket `cleveref` ni podpira slovenskega jezika, in čeprav je mogoče definirati nove jezike, je trenutno slovenski jezik težko implementirati zaradi sklanjatev (prim. „glej  Slik**o** 1” v „na Slik**i** 1”).
:::

Če uporabimo ukaz `\ref{<oznaka>}` z razdelki "z zvezdico" (npr. `\section*{...}`), ki niso oštevilčeni, bo ukaz vrnil nič ali nepričakovano vrednost, saj ti razdelki nimajo številk.
Zato je priporočljivo, da se na razdelke "z zvezdico" ne sklicujemo z ukazom `\ref`.
Možna alternativa je uporaba ukaza `\nameref{<oznaka>}`, ki vrne ime razdelka.

Ukaz `\pageref{<oznaka>}` vrne številko strani, na kateri se nahaja element z dano oznako. 
Ta ukaz lahko uporabimo z razdelki "z zvezdico", saj nam ni treba pridobiti številke razdelka, ampak le številko strani.

Za plavajoče elemente, kot so slike in tabele, je priporočljivo, da oznako dodamo znotraj okolja `figure` ali `table`, takoj po ukazu `\caption{...}`.
To zagotavlja, da se oznaka nanaša na pravilno številko slike ali tabele.


:::{prf:example}
:label: eg_sklici_2
`````{tab-set}  
````{tab-item} LaTeX
```latex
\begin{figure}
\centering
\includegraphics{macka}
\caption{Slika čudovite mačke.}
\label{fig:macka}
\end{figure}
%...
Na sliki \ref{fig:macka} na strani \pageref{fig:macka} vidimo lepo mačko.
```
```` 
````{tab-item} PDF
``` {figure} ./img/03_eg-sklici-2.png
:label: fig:sklici_2
```
```` 
`````
::: 

Označujmo in sklicujmo lahko vse, čemur LaTeX dodeli številko. Na primer, točke v seznamih.

:::{prf:example}
:label: eg_sklici_3
`````{tab-set}  
````{tab-item} LaTeX  
```latex
\begin{enumerate}
\item Oblecite nogavice.
\item \label{itm:cevlje} Obujte čevlje.
\item Pojdite na sprehod.
\end{enumerate}
%...
V koraku \ref{itm:cevlje} ne poszabite zavezati vezalk.
```
```` 
````{tab-item} PDF
``` {figure} ./img/03_eg-sklici-3.png
:label: fig:sklici_3
:width: 60%
:align: left
```
````
`````
:::

:::{exercise}
:label: ex_sklici
1. V dokumentu, ki ste ga napisali v [Vaji %s](#ex_hyperref), dodajte slike in tabele z oznakami.
2. Lahko uporabite tabele in slike, ki ste jih ustvarili v poglavju [](./02_latexOsnovnaOkolja).
:::

```{margin}
[Seznam vaj](#latexLiteratura_vaje)
```

## Literartura

**Klasični način**

Za vključitev literature v dokument LaTeX, lahko uporabimo okolje `thebibliography`.
To je le poseben seznam, kjer vsaka referenca dobi svojo oznako z ukazom `\bibitem{<oznaka>}`.
Nato se na referenco sklicujemo z ukazom `\cite{<oznaka>}`.

:::{prf:example}
:label: eg_literatura_1
`````{tab-set}  
````{tab-item} LaTeX
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
```` 
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-1.png
:label: fig:literatura_1
```
```` 
`````
:::

Ta način je enostaven in hiter, vendar ima nekaj pomanjkljivosti:
- Ročno moramo vnašati vse podatke o referencah, kar je lahko zamudno in nagnjeno k napakam.
- Ni standardiziranega formata za vnos referenc, kar lahko vodi do neenotnosti v slogu citiranja.
- Enostavne spremembe sloga citiranja so težavne, saj moramo ročno prilagoditi vsako referenco.
- Ni ločnega/struturnega označevanja, ki bi nakazovalo, kateri del bibliografskega vnosa je avtor, naslov, leto izdaje itd.
- Sortiranje referenc je ročno in lahko vodi do napak. Urejanje (npr. po letu izdaje namesto po priimku avtorja) je prav tako ročno in zamudno.
- Na splošno to ni pristop, ki bi bil značilen za LaTeX.

Zaradi teh razlogov je priporočljivo uporabiti bolj napredne metode za upravljanje literature v LaTeX dokumentih, kot je BibTeX ali/in BibLaTeX.

**BibLaTeX način**

BibTex je orodje za upravljanje bibliografskih podatkov, ki deluje skupaj z LaTeXom.
Omogoča nam, da shranimo vse naše reference v ločeno datoteko `.bib`, kar olajša upravljanje in ponovno uporabo referenc v različnih dokumentih.
BibLaTeX je sodobnejša alternativa BibTeX-u, ki ponuja več funkcionalnosti in prilagodljivosti. 

Uporaba BibLaTeX-a vključuje naslednje korake:
1. Ustvarimo datoteko z bibliografskimi podatki z razširitvijo `.bib`. V tej datoteki so reference shranjene v posebnem formatu.
2. V preambulo našega LaTeX dokumenta vključimo paket `biblatex` in določimo slog citiranja ter datoteko z bibliografskimi podatki.

Datoteka `.bib` je sestavljena iz vnosa, kjer vsak vnos predstavlja eno referenco.
Vsak vnos ima svoj edinstven ključ, ki ga uporabimo za sklicevanje na to referenco v našem dokumentu.
Vsak vnos vsebuje različna polja, kot so avtor, naslov, leto izdaje, itd. in izgledajo nekako takole:

:::bibtex
@<vrsta_Vnosa>{<kjluč>,
<polje1>    = {vrednost1},
<polje2>    = {vrednost2},
<polje3>    = {vrednost3}, 
<poljeN>    = {vrednostN}, 
}
:::

kjer je `<vrsta_Vnosa>` lahko `book`, `article`, `inproceedings`, `misc`, itd., odvisno od vrste reference.
`<ključ>` je edinstven identifikator za ta vnos, ki ga bomo uporabili v ukazu `\cite{<ključ>}` v našem LaTeX dokumentu.
`<polje1>`, `<polje2>`, itd. so različna polja, ki vsebujejo informacije o referenci, kot so avtor, naslov, leto izdaje, itd. Npr. za knjigo _Harry Potter in kamen modrosti_ bi bil vnos videti takole:

```bibtex
@book{hp1,
author    = {J. K. Rowling},
title     = {Harry Potter in kamen modrosti},
publisher = {Založba EPTA},
year      = {1997}
}
```

Polja so odvisna od vrste vnosa in slog bibligrafije, ki ga uporabljamo (več o tem kasneje). Za knjige so običajna polja `author`, `title`, `publisher` in `year`. Za članke v revijah bi lahko uporabili polja, kot so `journal`, `volume`, `number` in `pages`. Za spletne vire je pogosto uporabno polje `url` in `note`.
Celoten seznam vrst vnosov in polj najdete v dokumentaciji paketa [BibLaTeX](https://ctan.org/pkg/biblatex?lang=en) ali tem članku na [wikibooks](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#Entry_and_field_types_in_.bib_files).

Dobra novica je, da običajno ni potrebno ročno pisati datoteke `.bib`, saj obstajajo številna orodja in spletne strani, ki lahko samodejno generirajo vnose v pravilnem formatu.
Nekatera orodja, ki jih lahko uporabite za ustvarjanje in upravljanje datotek `.bib`, vključujejo:

- [Google Scholar](https://scholar.google.com/): omogoča izvoz posameznih referenc v format `.bib`.
- [COBISS](https://www.cobiss.si/): slovenski sistem za iskanje in izposojo knjižničnih gradiv, ki omogoča izvoz bibliografskih podatkov v format `.bib`.
- [ZoteroBib](https://zbib.org/): spletno orodje za hitro ustvarjanje bibliografij, ki podpira izvoz v format `.bib`.
- [MathSciNet](https://mathscinet.ams.org/mathscinet): spletna baza podatkov za matematiko.
- [DBLP](https://dblp.org/): baza podatkov za računalništvo.

Ko smo pripravili našo bazo podatkov referenc (tj. našo datoteko `.bib`, recimo `literatura.bib`), moramo v našem LaTeX dokumentu naložiti paket `biblatex` in povezati datoteko z bibliografskimi podatki.
To storimo z naslednjimi ukazi v preambuli:

```latex
\usepackage{biblatex} % Naloži paket biblatex
\addbibresource{literatura.bib} % Poveže datoteko z bibliografskimi podatki, recimo literatura.bib
```

V besedilu našega dokumenta se na reference sklicujemo z ukazom `\cite{<ključ>}`, kjer je `<ključ>` ključ vnosa v naši datoteki `.bib`.
Parameter `<ključ>` lahko je tudi seznam ključev, ločenih z vejico, če želimo sklicevati na več referenc hkrati.

Na koncu dokumenta (ali, kjerkoli  že želimo natisniti seznam referenc), dodamo ukaz `\printbibliography`, ki natisne seznam vseh referenc, na katere smo se sklicevali v besedilu.
Upoštevajte, da čeprav nismo uporabili vseh referenc iz datoteke `.bib`, bo `\printbibliography` natisnil le tiste, na katere smo se sklicevali z ukazom `\cite{<ključ>}`.


:::{exercise}
:label: ex_biblatex
1. V svojem projektu v Overleafu, stvarite datoteko z imenom `literatura.bib` in vanjo dodajte vsaj tri vnose različnih vrst (npr. knjiga, članek, spletna stran).
2. V vašem LaTeX dokumentu naložite paket `biblatex` z ukazom `\usepackage{biblatex}` v preambuli.
3. Dodajte ukaz `\addbibresource{literatura.bib}` v preambulo, da povežete datoteko z bibliografskimi podatki.
4. V besedilu uporabite ukaz `\cite{<ključ>}` za sklicevanje na vsako od referenc, ki ste jih dodali v datoteko `.bib` razen ene.
5. Na koncu dokumenta dodajte ukaz `\printbibliography`, da natisnete seznam referenc.
:::

```{margin}
[Seznam vaj](#latexLiteratura_vaje)
```

Z uporabo BibLaTeX lahko na nadzorovan način prilagodimo videz naših citatov in sklicev. To storimo z izbiro sloga citiranja, ki ga določimo kot možnost pri nalaganju paketa `biblatex`.
Na primer, 
```latex
\usepackage[style=alphabetic]{biblatex}
``` 
naloži slog `alphabetic`, ki uporablja črke iz imen avtorjev in leto izdaje za označevanje citatov v besedilu. Privzeto je slog `numeric`, ki uporablja številke za označevanje citatov.
Obstaja veliko različnih slogov citiranja, ki jih lahko uporabimo, odvisno od naših potreb in preferenc. 
Obsežen seznam slogov najdete v dokumentaciji paketa [BibLaTeX](https://ctan.org/pkg/biblatex?lang=en) ali na [Overleaf](https://www.overleaf.com/learn/latex/Biblatex_bibliography_styles).

:::{admonition} Pazite!
:class: warning
Slog citatov lahko spreminjamo neodvisno, to pomeni, da lahko spreminjamo, kaj ukaz `\cite` natisne v našem besedilu in kako se natisnejo oznake, ko natisnemo bibliografijo, vendar je dobro ohraniti enak slog.
:::

Če damo možnost `sorting=ynt` razvrsti bibliografijo po letu izdaje (`y`), nato po imenu avtorja (`n`) in nato po naslovu (`t`). Privzeto je `sorting=nty`, kar pomeni, da se najprej razvrsti po imenu avtorja, nato po naslovu in nato po letu izdaje.

Celoten seznam možnosti za razvrščanje najdete v dokumentaciji paketa [`BibLaTeX`](https://ctan.org/pkg/biblatex?lang=en) ali na [BibLaTeX cheat sheet](https://tug.org/biblatex-cheatsheet/biblatex-cheatsheet.pdf).


Kot smo že omenili, ukaz `\printbibliography` natisne seznam vseh referenc, na katere smo se sklicevali v besedilu. 
Če želimo natisniti reference, na katere se nismo sklicevali, lahko uporabimo ukaz `\nocite{<ključ>}`.
Ta ukaz nam omogoča, da vključimo določene vnose v bibliografijo, tudi če se nanje nismo sklicevali v besedilu.
Če želimo vključiti vse vnose iz naše datoteke `.bib`, lahko uporabimo ukaz `\nocite{*}`. 

Ukaz `\printbibliography` lahko sprejme različne možnosti, ki nadzorujejo videz bibliografije.
Na primer, lahko uporabimo možnost `title`, da spremenimo naslov bibliografije, kot je prikazano spodaj:


:::{prf:example}
:label: eg_literatura_2
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Viri in literatura}]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-2.png
:label: fig:literatura_2
```
````
`````
:::

Referenca lahko organizirate z uporabo filtrov.
Na primer, lahko natisnemo samo knjige z uporabo možnosti `type=book`:




:::{prf:example}
:label: eg_literatura_3
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[type=article,title={Samo članki}]
\printbibliography[type=book,title={Vse knjige}]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-3.png
:label: fig:literatura_3
```
````
`````
:::

Na voljo so filtri `type`, `keywords` in `category` in lahko uporabimo tudi njihove negacije. Z ukazom `\defbibfilter{<ime_filtra>}` lahko definiramo tudi svoje filtre.

:::{prf:example}
:label: eg_literatura_4
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[keyword={physics},title={Reference, povezane s fiziko}]
\printbibliography[notkeyword={latex}, title={Vse, razen tistih, povezane z LaTeX-om}]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-4.png
:label: fig:literatura_4
```
````
`````
:::



:::{prf:example}
:label: eg_literatura_5
`````{tab-set}  
````{tab-item} LaTeX
```latex
\defbibfilter{custom}{keyword=physics or keyword=latex}     
\printbibliography[filter=custom,title={Reference, povezane s fiziko ali \LaTeX-om}]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-5.png
:label: fig:literatura_5
```
````
`````
:::




Privzeto se bibliografija ne prikaže v kazalu vsebine. Če želimo, da se prikaže, lahko uporabimo možnost `heading`. 
Različen vrednosti za možnost `heading` so v  [Tabeli %s](#tab:heading_options)`.

:::{list-table} Naslov bibliografije v kazalu.
:header-rows: 1
:label: tab:heading_options

* - Vrednost
  - Opis
* - `bibliography`
  - privzeto, kot je razdelek »z zvezdico«.
* - `bibintoc`
  - kot razdelek z zvezdico, vendar se bo pojavil v kazalu.
* - `subbibliography`
  - bo bibliografija padla za eno stopnjo v hierarhiji (`\section*` namesto `\chapter*`, `\subsection*` namesto `\section*` in tako naprej).
* - `bibnumbered`
  - naraven razdelek (brez zvezdice), torej s številko in v kazalu.
* - `subbibintoc`
  - podobno kot subbibliography, vendar bo prikazana v kazalu.
* - `subbibnumbered`
  - podobno kot subbibliography, vendar brez zvezdice.
* - `none`
  - ne bo natisnil naslova.
:::


:::{prf:example}
:label: eg_literatura_heading_1
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Literatura, privzeto}]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-1.png
:label: fig:literatura_
```
````
`````
:::

:::{prf:example}
:label: eg_literatura_heading_2
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Literatura, v kazalu}, heading=bibintoc]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-2.png
:label: fig:literatura_heading_2
```
````
`````
:::
:::{prf:example}
:label: eg_literatura_heading_3
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Literatura, kot podrazdelek -- z zvezdico --}, heading=subbibliography]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-3.png
:label: fig:literatura_heading_3
```
````
`````
:::

:::{prf:example}
:label: eg_literatura_heading_4
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Literatura kot razdelek, s številko}, heading=bibnumbered]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-4.png
:label: fig:literatura_heading_4
```
````
`````
:::
:::{prf:example}
:label: eg_literatura_heading_5
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Literatura kot podrazdelek, brez št.-a, v kazalu}, heading=subbibintoc]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-5.png
:label: fig:literatura_heading_5
```
````
`````
:::
:::{prf:example}
:label: eg_literatura_heading_6
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Literatura kot podrazdelek, s št.-o, v kazalu}, heading=subbibnumbered]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-6.png
:label: fig:literatura_heading_6
```
````
`````
:::

:::{prf:example}
:label: eg_literatura_heading_7
`````{tab-set}  
````{tab-item} LaTeX
```latex
\printbibliography[title={Čeprav napišem naslov, se nič ne natisne}, heading=none]
```
````
````{tab-item} PDF
``` {figure} ./img/03_eg-literatura-heading-7.png
:label: fig:literatura_heading_7
```
````
`````
:::




(latexLiteratura_vaje)=
## Vaje

- [Vaja %s](#ex_hyperref): Sklicevanje z uporabo paketa `hyperref`.
- [Vaja %s](#ex_sklici): Sklicevanje na različne elemente v dokumentu.
- [Vaja %s](#ex_biblatex): Uporaba BibLaTeX-a za upravljanje literature.

<!-- - [ ] {numref}`Vaja {number} <ex_hyperref>`
- [ ] {numref}`Vaja {number} <ex_sklici>`
- [ ] {numref}`Vaja {number} <ex_biblatex>` -->


:::{exercise} Domača naloga
:nonumber: 
1. Ustvarite novi projekt v Overleafu z imenom `DN2.tex`.
1. V tem projektu, napišite en dokument LaTeX, ki vsebuje recept vaše najljubše jedi.
1. Uporabite sezname, tabele ali celo slike.
1. Uporabite reference z uporabo ukazov `\label`, `\ref`, `\nameref`, `\pageref`. Ne pozabite naložiti paketa `hyperref` (glede na vaše potrebe).
1. Ne pozabite, da morate tabele in slike vstaviti v plavajoče elemente in jim dodati pojasnile.
1. Poskusite, da bo izgledalo čim bolj profesionalno.
:::
