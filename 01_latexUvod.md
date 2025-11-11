(latexUvod)=
# Uvod v LaTeX

(latexUvod_kajJeLaTeX)=
## Kaj je LaTeX?

LaTeX je program za oblikovanje besedil.
LaTeX je nadgradnja programa TeX, ki je razvil Donald E. Knuth. leta 1997.
Prvo verzijo LaTeX-a je napisal Leslie Lamport (1980). LaTeX je paket dodatnih ukazov za TeX, ki avtorjem omogočajo oblikovanje in izpisovanje dokumentov v najvišji kvaliteti s pomočjo že pripravljenih profesionalnih vzorcev.

Trenutna standardna verzija je LaTeX2e (1994), zanj pa je odgovoren Frank Mittelbach. LaTeX se izgovori 'láteh', po angleško pa običajno rečemo 'lejteh'.

Ko želi _avtor_ kaj objaviti, pošlje svoj rokopis založniku.
Tam _knjiži opremljevalec_ določi obliko dokumenta (širino stolpcev, obliko črk, velikost presledkov pred in po naslovih ... ).
Opremljevalec svoja navodila skupaj z rokopisom preda _črkostavcu_, ki na podlagi teh podatkov stavi knjigo.
V LaTeX-u prevzame vlogi knjižnega oblikovalca in črkostavca, da se avtor osredotoči na vsebino [](#kaj-je-latex).



```{figure} ./img/01_osnovne.png
---
width: 80%
name: kaj-je-latex
class: dark-light
---
Kaj je LaTeX?
```

(latex_filozofija)=
:::{admonition} Pomebno: Filozofija LaTeXa
:class: important
Oblikovanje dokumentov z LaTeXom sledi naslednjemu načelu: 
> mi (avtorji) se ukvarjamo z **vsebino** dokumenta, LaTeX pa poskrbi za **oblikovanje**. 

Ali, enakovredno, 

>ne skrbimo za **oblikovanje**, zato se lahko osredotočimo na **vsebino**.
:::



(latexUvod_KajZmoreLaTeX)=
## Kaj zmore LaTeX?

LaTeX zmore skoraj vse, kar zmorejo drugi urejevalniki besedil.
Vendar pa je LaTeX posebej primeren za pisanje znanstvenih in tehničnih besedil, ki vsebujejo veliko matematičnih formul in simbolov.
LaTeX omogoča tudi enostavno ustvarjanje tabel, grafov in drugih elementov, ki so pogosto potrebni v tehničnih besedilih.
Poleg tega LaTeX omogoča enostavno ustvarjanje kazal, bibliografij in drugih elementov, ki so pomembni za znanstvena besedila.

Čeprav je LaTeX optimiziran za izdelavo znanstvenih in tehničnih besedil, ni omejen samo na to. Danes uporabljam LaTeX za pisanje vseh dokumentov, ki naj izgledajo profesionalno ali lepo.
To sega od osebnih in poslovnih pisem do pesmarice za igranje kitare.

Vprašal sem moje sodelavce, kaj delajo z LaTeXom. 
Tukaj je nekaj zanimivih odgovorov:

- Knjnige, članke, in zapiski predavanj;
- Predstavitve, s pomočjo Beamer-ja [](./06_latexBeamer);
- Profesionalna dokumentacija (npr CV, projekte vloge);
- Pogodbe za stanovanje;
- Pisma;
- Pravila za družabne igre
- Note (za glasbo)
- Facebook, SMS, Instagram (da, res je!).
- **Zaključna dela (diplome, magistrska, doktorat)**

Če vas zanima, si lahko tukaj ogledate [mojo doktorsko disertacijo](https://anteromontonio.github.io/assets/pdf/2019_Mon_phDThesis.pdf), ki je bila napisana izključno z uporabo programa LaTeX.

(latexUvod_latexNiWord)=
## LaTeX ni Word

MS Word, Google Docs, LibreOffice, so WYSIWYG (kar vidiš, to tudi dobiš).
V teh programih avtor obliko dokumenta določi interaktivno med samim vnosom besedila v računalnik. Med celotnim procesom na zaslonu vidi, kakšna bo končna oblika, ko bo dokument natisnjen.

Pri LaTeXu ni možno videti končne oblike med samim tipkanjem besedila.
Lahko pa vidimo končno obliko na zaslonu, potem ko datoteko prevedemo z LaTeXom.
Tako lahko popravke naredimo še preden dokument izpišemo s tiskalnikom.
V urejevalnikih WYSIWYG strukturo in obliko urejate hkrati z pisanjem besedila.
Zlasti pri dolgih projektih se je zelo lahko izgubiti.
LaTeX sili avtorja, da določi logično strukturo besedila, LaTeX pa potem izbere najprimernejšo obliko.

(latexUvod_zakaj)=
### Zakaj LaTeX?

Predstavljajmo si, da pišete roman v svojem najljubšem urejevalniku WYSIWYG.
V tej knjigi se odvijata dve vzporedni zgodbi v
različnih dimenzijah.
Da bi bralcu sporočili, katera od dimenzij je trenutno opisana, ste se odločili, da boste za obe uporabili različne barve.
Vaša knjiga bi tako lahko izgledala takole:

:::{div} 
:class: latex-block text-blue
„Ne, ne moreš me zapustiti!“ je zaklical  Peredur Lancelotu.\
„Moram,“ je odgovoril. „Usoda me kliče. Toda ponovno se bova srečala. Obljubim.“
:::

```{div} 
:class: latex-block text-green
Shao je občutila nepojasnjeno žalost, kot da bi pravkar izgubila nekaj ali nekoga, ki ji je bil pomemben.\
„Si v redu?“ je vprašala Ashby, medtem ko je jedla svojo kašo.\
„Ne izgledaš dobro.“\
„V redu sem, samo utrujena.“
```

Ko ste končali prvi osnutek (ki obsega 300 strani), ste se odločili, da ga pošljete po e-pošti prijatelju, da vam bo povedal svoje mnenje.
Vendar se je izkazalo, da lahko tiskalnik vašega prijatelja tiska samo črno-belo, zato ne more natisniti datoteke, ki ste mu jo poslali.

Enostavna rešitev! Vse zeleno besedilo spremenite v kursivno pisavo, ostalo pa pustite v pisavi upright front.
Po ročni spremembi vsakega odstavka prvih 120 strani knjige ste se spomnili, da v nekaterih primerih za poudarjanje uporabljate kursivno pisavo:
[Ali boš *to* jedla?]{.latex-line .text-green}
Sedaj boste morali preveriti vsak odstavek za kurzivo in ga spremeniti v drug slog, preden spremenite vse zeleno besedilo v kurzivo.

**Vidite neskončni problem?**.

LaTeX rešuje ta problem tako, da avtorju omogoča, da se osredotoči na vsebino in logično strukturo besedila, medtem ko LaTeX poskrbi za oblikovanje.


(latexUvod_kakoDeluje)=
## Kako deluje LaTeX?

Klasična razlaga delovanja LaTeX-a je naslednja:

1. Avtor napiše besedilo in ukaze LaTeX v datoteko `.tex` (npr. `ime_datoteke.tex`).
2. Datoteka `.tex` prevedemo z LaTeX-om, ki ustvari datoteko `.dvi` (npr. `ime_datoteke.dvi`).
3. Datoteke `.dvi` niso standardne, zato je treba datoteka `.dvi` pogosto spremeniti v datoteko `.pdf`; na koncu dobimo datoteko `ime_datoteke.pdf`, ki jo lahko natisnemo ali delimo z drugimi.

V sodobnem času pogosto gremo iz `ime_datoteke.tex` datoteke neposredno v `ime_datoteke.pdf`} npr. z pomočijo programa `pdflatex`.

```{figure} ./img/01_datoteke.png
---
width: 80%
name: kako-deluje-latex
class: dark-light
---
Kajo deluje LaTeX?
```


(latexUvod_kakoZaceti)=
## Kako začeti z LaTeXom?


Lahko namestite na svoj računalnik.
Če vas to želite, poglejte [](./A_namescanjeLatexa).

Uporabili bomo drugačen pristop in delali z LaTeXom na spletu. 
To bomo storili prek Overleaf, ki je platforma za delo z LaTeX projekti na spletu. 
Najprej morate ustvariti račun.


:::{exercise} 
:label: ex-overleafRacun

Ustvarite si Overleaf račun.
:::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

::: {solution} ex-overleafRacun
:class: dropdown
1. Pojdite na [Overleaf](https://www.overleaf.com/).
2. Kliknite na gumb "Register" v zgornjem desnem kotu strani.
3. Odprla se bo stran, na kateri lahko ustvarite račun na različne načine, med drugim z uporabo e-poštnega ali Google računa.
4. Če izberete možnost registracije z e-pošto, morate vnesti svoje ime, e-poštni naslov in ustvariti geslo. Nato kliknite na gumb "Register". V tem primeru boste morda morali potrditi svoj e-poštni naslov.
:::




(latexUvod_ukaziOkolja)=
<!-- ## Prva datoteka v LaTeXu -->

## Ukazi in okolja

Kot smo [že omenili](#latex_filozofija), se moramo pri delu z LaTeXom osredotočiti na vsebino, oblikovanje pa prepustiti LaTeXu.
Ker pa je LaTeX "samo" računalniški program, potrebuje
več vodenja.
Avtor mora navesti dodatne informacije, ki opisujejo logično strukturo njegovega dela.
Te informacije se navedejo prek _ukazov_ in _okolij_, ki se vpišejo okoli besedila.

Ukazi v LaTeXu imajo splošno obliko:
```latex
\imeUkaza[neobvezni argument]{argument}
```
in se običajno uporablja za dajanje LaTeXu določenih navodil.

- Ukaz *vedno* se začne z znakom `\`.
- Argumentov je lahko več, npr. `{prvi}{drugi}...{zadnji}` ali  nobenega (npr. ukaz `\tiny`, vendar je to redko).

- Lahko je več neobveznih argumentov: `[prvi, drugi, ..., zadnji]`  ali noben (in potem ne napišemo ničesar). Pazite razliko z `obveznimi argumenti`.

Okolje je posebna vrsta ukaza z naslednjo strukturo:
``` latex
\begin{okolje}
  Vsebina okolja: ukazi in besedilo
\end{okolje}
```
Okolja običajno nadzorujejo, kako se bo del besedila/kode obnašal, ko bo natisnjen v dokument.

Zaenkrat vam ni treba skrbeti, kako delujejo ukazi in okolja. 
To bomo spoznavali sproti. 
V poglavju [](./02_latexOsnovnaOkolja.md)  bomo podrobneje pogledali nekatera najpomembnejša okolja.

(latexUvod_preambulaTelo)=
## Preambula in telo datoteke

Vsaka datoteka LaTeX ima naslednjo obliko:

``` latex
%Preambula
\documentclass{...}
\usepackage{...}
%... 
% Telo
\begin{document}
  Vsebina dokumenta.
\end{document} 
```

Najpomembnejše okolje v lateksu je okolje `document`.
To okolje se lahko uporabi največ enkrat na dokument in v tem okolju pa napišemo dejansko vsebino našega dokumenta.
Vse, kar je znotraj tega okolja, se imenuje _telo_ dokumenta.

Če je najpomembnejše okolje `document`, mora biti najpomembnejši ukaz `\documentclass`.
Vse, kar je med ukazom `\documentclass` in začetkom okolja `document`, se imenuje _preambula_ dokumenta.
Tukaj nadzorujemo splošno delovanje LaTeXa. 

:::{admonition} Opozirilo!
:class: warning
Preambula običajno vsebuje samo ukaze (v nasprotju z običajnim besedilom) in obstajajo ukazi, ki se lahko uporabljajo samo v preambuli. 
Pogosta napaka v LaTeXu je, da se del kode napiše na napačno mesto.
:::

Ukaz `\documentclass` določa vrsto dokumenta, ki ga želimo ustvariti.
Uporabljamo ga tako
``` latex 
\documentclass[možnosti]{razred}
``` 

Tu `razred` določa vrsto dokumenta, ki ga želimo ustvariti (npr. članek, knjiga, poročilo ...), `možnosti` pa so dodatne nastavitve, ki vplivajo na videz dokumenta (npr. velikost pisave, velikost papirja ...). V [Tabeli %s](#tab_latex_razredi) so prikazani različni razredi dokumentov v LaTeXu.

:::{list-table} Razredi LaTeX dokumentov
:header-rows: 1
:label: tab_latex_razredi

* - Razred
  - Opis
* - `article`
  - za članke v znanstvenih revijah, kratka poročila in druge krajše dokumente.
* - `proc`
  - razred za zbornike, ki temelji na razredu *article*.
* - `report`
  - za daljša poročila, ki vsebujejo več poglavij, manjše knjige, doktorske disertacije, …
* - `book`
  - za prave knjige.
* - `beamer`
  - za predstavitve.
* - `letter`
  - za pisma.
:::

V tem učbeniku bomo obravnavali le razreda `article` in `beamer` (glej [](./06_latexBeamer), vendar bo večio tega, kar se bomo naučili, mogoče brez težav uporabiti tudi v drugih razredih.

Nekatere od uporabnih `možnosti` so `10pt` (prim. `11pt`, `12pt`), `a4paper` (prim. `letterpaper`), `onecolumn` (prim. `twocolumn`).
Privzete možnosti za `article` razred so `[letterpaper, 10pt, oneside, onecolumn, final]`.

:::{exercise} 
:label: ex_latex_prvaDatoteka

Napišite svoji prvi dokument z LaTeXom:
1. Najprej na Overleafu kliknite "new project" (nov projekt, na levi), potem "blank project" ga poimenujte (npr. MatTeh_latexUvod).
2. Izbrišite datoteko `main.tex`.
3. Kliknite "new file" (nova datoteka,  na levi) in ga poimenujete (npr. `prvaDatoteka.tex`).
4. Napišite vrstico `\documentclass[10pt]{article}`.
5. Napišite vrstici `\begin{document}` in `\end{document}`.
6. V svoj dokument, napišite nekaj besedila in shranite (<kbd>Ctrl</kbd>+<kbd>S</kbd>)
7. Zamenjajte vrstico `\documentclass[10pt]{article}` za vrstico `\documentclass[12pt]{article}` in spet shranite. 
:::
```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

:::{solution} ex_latex_prvaDatoteka
:class: dropdown
Tukaj je primer, kako bi lahko izgledala vaša datoteka `prvaDatoteka.tex`:

`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass[12pt]{article}
\begin{document}
  To je moja prva datoteka v LaTeXu. V tem bom napisal ljubezensko pismo Juliji.
\end{document}
```
````

````{tab-item} 10pt
```{figure} ./img/01_prvaDatoteka10pt.png
:name: prvaDatoteka_10pt
:alt: prvaDatoteka.tex 10pt
```
````

````{tab-item} 12pt
```{figure} ./img/01_prvaDatoteka12pt.png
:name: prvaDatoteka_12pt
:alt: prvaDatoteka.tex 12pt
```
````
````` 



- Ko shranite datoteko, bo Overleaf samodejno prevedel vaš dokument in prikazal rezultat na desni strani zaslona.
- Če ne, kliknite na gumb "Recompile" (prevedi znova) na vrhu desnega okna, da ročno prevedete dokument.
- Če spremenite velikost pisave iz `10pt` v `12pt`, boste opazili, da se bo besedilo na desni strani povečalo.
- Če ne vidite spremembe, znova kliknite na gumb "Recompile". Morda boste morali napisati več besedila, da boste opazili spremembo. 
:::

(latexUvod_avtorNaslovDatum)=
## Avtor, naslov in datum

Z ukazi `\title`, `\author` in `\date` lahko določimo naslov, avtorja in datum dokumenta.
Ti ukazi se običajno uporabljajo v preambuli, vendar jih lahko uporabimo tudi v telesu dokumenta.
Ti ukazi ne ustvarijo ničesar, dokler ne uporabimo ukaza `\maketitle`, ki ustvari naslovno stran z informacijami, ki smo jih določili z zgornjimi ukazi. Poglejte [Primer %s](#eg-avtorNaslovDatum).

::::{prf:example}
:label:eg-avtorNaslovDatum
``` latex 
% Preambula
% ...
\author{France Prešeren}
\title{Zdravljica}
\date{26.04.1848}    
% ... 
% Telo
\begin{document}
\maketitle
V tem dokumentu bom napisal ljubezensko pismo Juliji.
\end{document} 
```
::::

:::{exercise}
:label: ex_latex_avtorNaslovDatum
1. Z uporabo ukazov `\author`, `\title` in `\date`, dodajte avtorja, naslov in datum v vašo prvo datoteko LaTeX.
2. Shranite (<kbd>Ctrl</kbd>+<kbd>S</kbd>).
3. Na vrh telesa dokumenta napišite ukaz `\maketitle` in spet shranite.
4. Zamenjajte datum z svojim rojstnim dnem in spet shranite.
5. Zamenjajte argument ukaza `\date` z ukazom `\today` in spet shranite.
:::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

::: {solution} ex_latex_avtorNaslovDatum
:class: dropdown tip
Tukaj je primer, kako bi lahko izgledala vaša datoteka `prvaDatoteka.tex`:

:::::{tab-set}

````{tab-item} LaTeX
```latex
\documentclass[12pt]{article}
\author{France Prešeren}
\title{Zdravljica}
\date{26.04.1848}    
\begin{document}
\maketitle
  To je moja prva datoteka v LaTeXu. V tem bom napisal ljubezensko pismo Juliji.
\end{document}
```
````

````{tab-item} PDF
```{figure} ./img/01_avtorNaslovDatum_1.png
:name: avtorNaslovDatum_1 
:alt: brez ukaza `\maketitle`
```
````

````{tab-item} PDF
```{figure} ./img/01_avtorNaslovDatum_2.png
:name: avtorNaslovDatum_2
:alt: z ukazom `\maketitle`
```
````

````{tab-item} PDF
```{figure} ./img/01_avtorNaslovDatum_3.png
:name: avtorNaslovDatum_3
:alt: brez ukazom `\maketitle`
```
````

- Ko shranite datoteko, bo Overleaf samodejno prevedel vaš dokument in prikazal rezultat na desni strani zaslona.
- Če ne, kliknite na gumb "Recompile" (prevedi znova) na vrhu desnega okna, da ročno prevedete dokument.
- Če spremenite datum v rojstni dan ali uporabite ukaz `\today`, boste opazili, da se bo datum na desni strani spremenil.
- Če ne vidite spremembe, znova kliknite na gumb "Recompile".

:::::


(latexUvod_jezikPaketi)=
## Paketi in jeziki




LaTeX je zelo prilagodljiv in razširljiv sistem.
Osnovni LaTeX ponuja le osnovne funkcije, vendar lahko z uporabo _paketov_ dodamo nove funkcije in možnosti.
LaTeX ima okoli [6000 paketov](https://www.ctan.org/pkg) na voljo.
Paketi so zbirke ukazov in okolij, ki jih lahko vključimo v naš dokument z ukazom 
```latex
\usepackage{ime_paketa}.
```

:::{admonition} Opozorilo!
:class: warning
Ukaz `\usepackage{ime_paketa}` mora biti v preambuli, torej pred `\begin{document}`.
:::

Eden najpomembnejših paketov je `babel`, ki omogoča uporabo različnih jezikov.
Paket naložimo z ukazom 
``` latex
\usepackage[jezik]{babel}
``` 
kjer `jezik` določa jezik, ki ga želimo uporabiti (npr. `slovene`, `english`, `spanish`, `french`, `german`, `italian`, ...).
Paket `babel` poskrbi za pravilno oblikovanje besedila glede na izbrani jezik (npr. vezaje, ločila, datum, ...).

:::{exercise}
:label: ex_latex_babel
1. V svojo prvo datoteko LaTeX dodajte vrstico `\usepackage[slovene]{babel}` v preambulo. Shranite in **poglejte datum!**.
2. Zamenjajte `slovene` z `spanish` in spet shranite. **Poglejte datum!**.
3. Spremenite ukaz nazaj v `\usepackage[slovene]{babel}` in spet shranite.
:::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

:::{solution} ex_latex_babel
:class: dropdown
Tukaj prikazujemo, kako uporabljati paket `babel`.
`````{tab-set}
````{tab-item} LaTeX
```latex
\documentclass[10pt]{article}
\usepackage[slovene]{babel}

\author{France Prešeren}
\title{Zdravljica}
\date{\today}  

\begin{document}
\maketitle
To je moja prva datoteka v LaTeXu. V tem bom napisal ljubezensko pismo Juliji.
\end{document}
```
````
````{tab-item} PDF (en)
```{figure} ./img/01_babel_en.png
:name: babel_english 
:alt: brez ukaza `\usepackage[slovene]{babel}`
```
````
````{tab-item} PDF (sl)
```{figure} ./img/01_babel_sl.png
:name: babel_slovene 
:alt: s ukazom `\usepackage[slovene]{babel}`
```
````
````{tab-item} PDF (es)
```{figure} ./img/01_babel_es.png
:name: babel_spanish 
:alt: s ukazom `\usepackage[spanish]{babel}`
```
````
````` 
:::

:::{admonition} Opomba!
:class: note
- V starih različicah LaTeXa nismo mogli preprosto pisati **č**, **š**, **ž**, **á**, **ü** …
- Te črke lahko vedno dobimo z ukazi, kot so:

```{table}
:align: center
| Ukaz     | Rezultat |
|:----------:|:----------:|
| `\v{c}`  | č        |
| `\v{s}`  | š        |
| `\v{z}`  | ž        |
| `\'{a}`  | á        |
| `\"{u}`  | ü        |
```
- Alternativno lahko uporabimo naslednje pakete za kodiranje znakov:

```latex
% Vhodnega dokumenta, 
\usepackage[utf8x]{inputenc} 
% opcije lahko so [utf8], [utf8x], ali [cp1215] 

% izhodnega dokumenta, 
\usepackage[T1]{fontenc} 
% lahko damo tudi [T2A] za cirilica 
```

- Sodobni LaTeX običajno ne potrebuje teh paketov. 
Ponavadi je dovolj če uporabimo paket `babel`.
:::


(latexUvod_komentari)=
## Komentarji, posbeni znaki, prazne vrstice in presledki. 

:::::{exercise}
:label: ex_latex_komentarji
1. Napišite naslednji stavek v svoj dokument:
```{div} 
:class: latex-block
Več kot 50 % površine Slovenije pokriva gozd.
```
1. Shranite (<kbd>Ctrl</kbd>+<kbd>S</kbd>) in poglejte rezultat.
:::::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

:::{solution} ex_latex_komentarji
:class: tip dropdown
Kadar LaTeX v vhodni datoteki sreča znak `%`, ignorira vse znake v nadaljevanju tekoče vrstice, prelom vrstice in vse presledke na začetku naslednje vrstice.

Pravilna rešitev je:
```latex
Več kot 50 \% površine Slovenije pokriva gozd.
```
::: 

:::{admonition} Nasvet!
:class: tip
Pri delu v LaTeXu besedila **ne brišemo**, temveč ga **komentiramo**.
:::

Če želimo izpizati simbol %, zapišemo `\%`.
Simbol % je v LaTeXu poseben znak, to pomeni, da ima poseben pomen in ga ne moremo uporabiti kar tako.
Drugi posebni znaki v LaTeXu so prikazni v [Tabeli %s](#tab-posebniZnaki).

:::{table} Posebni znaki v LaTeXu
:align: center
:name: tab-posebniZnaki
| Znak     | Ukaz      |
|:----------:|:----------:|
| `%`      | `\%`      |
| `$`      | `\$`      |
| `&`      | `\&`      |
| `#`      | `\#`      |
| `_`      | `\_`      |
| `{` `}`      | `\{` `\}` (vedno v paru)    |
| `~`      | `\textasciitilde` |
| `^`      | `\textasciicircum` |
| `\`      | `\textbackslash`   |
:::


:::{admonition} Pogosta napaka!
:class: error
Pogosta napaka v LaTeXu je, da se pozabi uporabiti ukaz za enega od posebnih simbolov.
:::


:::{exercise}
:label: ex_latex_posebniZnaki
1. Napišite naslednji stavek v svoj dokument:
```{div} 
:class: latex-block
Več kot 90 % Slovencev zasluži več kot 500 € na mesec, kar je približno 600 $.
```
:::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

:::{solution} ex_latex_posebniZnaki
:class: tip dropdown
Pravilna rešitev je:
`````{tab-set}
````{tab-item} LaTeX
```latex
Več kot 90 \% Slovencev zasluži več kot 500 € na mesec, kar je približno 600 \$.
```
````

````{tab-item} PDF
```{figure} ./img/01_posebniZnaki_1.png
:name: posebniZnaki_1 
:alt: Posebni znaki v LaTeXu
```
````
````{tab-item} PDF
```{figure} ./img/01_posebniZnaki_2.png
:name: posebniZnaki_2 
:alt: Posebni znaki v LaTeXu (z pisave `lmodern`)
```
````
`````

Upoštevajte, da simbol za evro ni poseben, lahko ga preprosto uporabimo. 
Vendar pa izgleda grdo, razlog za to pa je, da LaTeX uporablja nekoliko starejše pisave. 
To lahko popravimo z uporabo paketa `lmodern` (glej {ref}`latexUvod_pisave` )
:::


**Vezaj vs pomišljaj**

Vezaj v LaTeXu dobimo z enim samim znakom `-`.
Pogoste uporabe vezaja so:
- sestavljene besede, npr. `informacijsko-komunikacijska tehnologija`: [informacijsko&ndash; komunikacijska tehnologija]{.latex-line};
- sklanjanje kratic, npr. `v NUK-u`: {span .latex-line}`v NUK&ndash;u`.

Pomišljaj v LaTeXu dobimo z dvema znakama `--`.
Pogoste uporabe pomišljaja so:
- za označevanje intervalov, npr. `strani 10--20`: {span .latex-line}`strani 10&mdash;20`;
- ločevanje besedila, npr. za pojasnila v stavku, npr. `LaTeX -- program za oblikovanje besedil -- je zelo prilagodljiv`: {span .latex-line}`LaTeX &mdash; program za oblikovanje besedil &mdash; je zelo prilagodljiv`.


**Narekovaji** 

LaTeX ima posebna pravila za tiskanje narekovajev: 

- Enojne narekovaje dobimo z uporabo znakov ``` ` ``` in ``` ' ```, npr. ``` `narekovaj' ```: {span .latex-line}`'narekovaj'`.
- Dvojne narekovaje dobimo z uporabo znakov ``` `` ``` in ``` '' ```, npr. ``` ``narekovaji'' ```: {span .latex-line}`"narekovaji"`.
- Za slovenske narekovaje uporabimo ukaza ``` \glqq ``` in ``` \grqq ```, npr. ``` \glqq slovenski narekovaji\grqq ```: {span .latex-line}`„slovenski narekovaji“`.
- Če uporabimo `\usepackage[slovene]{babel}`, lahko preprosto napišemo ``` "` ``` in ``` "' ```, npr. ``` "`slovenski narekovaji"' ```: {span .latex-line}`„slovenski narekovaji“`.
- Lahko uporabimo tudi ```">``` in  ``` "< ```, npr. ``` ">slovenski narekovaji"< ```: {span .latex-line}`»slovenski narekovaji«` (potreben je tudi paket `babel`). 

::::{exercise}
:label: ex_VezajiPomisljajiNarekovaji

V svojem dokumentu napišite naslednje besedilo. Pazite, da uporabite pravilne znake za vezaje, pomišljaje in narekovaje.


```{figure} /img/01_ex-vezajPomislajNarekovaji.png
:name: latexUvod-ex-vezajPomislajNarekovaji
:alt: Uporaba vezajev, pomišljajev in narekovajev v LaTeXu.
```
::::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

:::{solution} ex_VezajiPomisljajiNarekovaji
:class: tip dropdown
Možna rešitev je:
```latex
V slovenščini vezaj (-) brez presledkov povezuje sestavine besed (slovensko-angleški slovar, C-vitamin), medtem ko pomišljaj (--) s presledki razmejuje ali poudarja miselne enote (To je bilo -- verjeli ali ne -- res.) ter označuje obseg (strani 15--20).
V slovenščini uporabljamo več vrst narekovajev. 
Najpogostejši so dvojni spodnji in zgornji ("` "'), npr. "`To je primer."' 
Uporabljajo se v knjižnem jeziku in uradnih besedilih. 
Pogosti so tudi dvojni zgornji (`` '' ), npr. ``Tako piše v članku.'', zlasti v elektronskih besedilih. Včasih naletimo na špičaste narekovaje ("> "<), npr. ">Tako so govorili."<, ki imajo dolgo tradicijo v slovenski tipografiji. 
Vsi trije tipi so pravilni, pomembno pa je, da v enem besedilu uporabljamo enotno obliko.

Ko pišemo besedilo v \LaTeX u, moramo paziti, da uporabljamo pravilne simbole. Poleg zgoraj navedenih simbolov ima \LaTeX tudi poseben ukaz za \dots, in sicer \dots{}  (prim. ...).
```     
:::


:::{admonition} Pogosta napaka!
:class: error
Pogosta napaka v LaTeXu je, da uporabljamo naravne narekovaje (``"`` in ``'``) ali pa napačno uporabljamo ukaze za narekovaje, npr.

- `"narekovaji"` 
- ``` ``narekovaji`` ```
:::




**Presledki**

- Poljubno število presledkov (ali tabulatorjev) med besedami se obravnava kot en sam presledek.
- Presledek na začetku vrstice se ignorira.
- Nova vrstica se obravnava kot presledek, če ni prazna.
- Prazna vrstica se obravnava kot konec odstavka in začne nov odstavek.
- Zaporedne prazne vrstice se obravnavajo kot ena sama prazna vrstica.
- Prazen komentar `%` ni prazna vrstica.

:::{prf:example}
:label: latexUvod_primerspresledki
`````{tab-set}
````{tab-item} LaTeX
```latex
Ni pomembno, če za besedo
stoji en ali pa več           presledkov.
Prelom vrstice brez praznih 
  se obravnava kot presledek.


Prazna vrstica začenja nov odstavek. 
%
Prazen komentar ni prazna vrstica.

```
````

````{tab-item} PDF
```{figure} ./img/01_presledki.png
:name: presledki 
:alt: Presledki v LaTeXu
```
````
`````
:::

:::{admonition} Nasvet!
:class: tip
Ker se nova vrstica v LaTeXu obravnava kot presledek, razen če je prazna, je dobro, da vsak stavek napišete v eno vrstico.
To olajša urejanje besedila in sledenje spremembam v sistemih za nadzor različic, kot je Git.
:::

Včasih resnično potrebujemo prelom vrstice, ne da bi začeli nov odstavek. Za to imamo na voljo naslednji dve ukazi.

- Ukaz `\\` ustvari prelom vrstice. 
- Ukaz `\newline` ustvari prelom vrstice in ignorira vse presledke na začetku naslednje vrstice.
- Ukaz `\linebreak[arg]` (`arg` je število od 0 do 4, privzeta vrednost je 4.): 0 pomeni, da je prelom vrstice nizke prioritete in se lahko, zaradi drugih okoliščin, ignorira, 4 pa pomeni, da je prioritete preloma vrstice visoka.
- Ukaz `\noindent` prepreči zamik prve vrstice novega odstavka.

:::{prf:example}
:label: latexUvod_eg-newline
`````{tab-set}
````{tab-item} LaTeX
```latex
\noindent Živé naj vsi naródi,\\
ki hrepené dočakat' dan,\newline
da koder sonce hodi,\\
prepir iz svéta bo pregnan,\newline
da rojak\\
prost bo vsak,\\
ne vrag, le sosed bo mejak!

```
````

````{tab-item} PDF
```{figure} ./img/01_zdravljica.png
:width: 300px
:name: zdravljica 
:alt: newline v LaTeXu
```
````
`````
:::

LaTeX ima tudi ukaze za obravnavanje prelomov strani.

- Ukaz `\pagebreak[arg]` je najbolj primitivni med njimi. Preprosto prekine stran na mestu, kjer se pojavi. Argument `arg` deluje enako kot pri `\linebreak`.
- Ukaz `\newpage` prekine stran in začne novo stran. 
Prav tako zapolni preostali prostor na strani s praznim prostorom.
- Ukaz `\clearpage` deluje podobno kot `\newpage`, vendar poleg tega tudi izpiše vse plavajoče elemente (npr. slike in tabele), ki še niso bili izpisani.
- Ukaz `\cleardoublepage` deluje podobno kot `\clearpage`, vendar zagotavlja, da se nova stran začne na desni strani v dvostranskem tisku.

(latex_prelomStrani)=
:::{admonition} Nevarnost!
:class: danger
Ukazi za prelome vrstic in strani so namenjeni uporabi v izjemno specifičnih okoliščinah, vendar **njihova uporaba ni priporočljiva**.

Ne pozabite, da moramo [oblikovanje dokumenta prepustiti LaTeXu](#latex_filozofija). 
:::


(latexUvod_pisave)=
## Pisave in velikosti pisave

LaTeX privzeto uporablja pisavo _Computer Modern_, ki jo je zasnoval Donald Knuth.
Sodobne različice LaTeX pogosto uporabljajo Latin Modern, ki je sodobna različica Computern Modern.
Če ta pisava ni privzeto naložena, jo lahko (in jo tudi morate) naložiti s ukazom `\usepackage{lmodern}` v preambuli.

LaTeX samodejno izbere pisavo in velikost črk glede na razred dokumenta in izbrane pakete.
Če želite spremeniti pisavo ali velikost pisave, LaTeX uporablja štirje parametri:

family (družina)
: Dejanska pisava, ki jo uporablja. Privzeto ima LaTeX tri družine: _roman_ oz. _pokončna serifna_ pisava (`\textrm`), _sans serif_ oz. _gladka_ pisava (`\textsf`)  in _strojepisna_ oz. _enakoprostorna_ pisava  (`\texttt`) 

series (serija)
: Debelina pisave. Privzeto ima LaTeX dve seriji: _medium_ oz. _srednja_ pisava (`\textmd`) in _bold face_ oz. _krepka_ pisava (`\textbf`).

shape (oblika):
: Naklon pisave. Privzeto ima LaTeX tri oblike: _italic_ oz. _poševna_ pisava (`\textit`),   _slanted_ oz.  _ležeča_ pisava (`\textsl`) in  _small caps_ oz. _male velike črke_ (`\textsc`). 
Poleg tega sta na voljo dve virtualni obliki: _pokončna_ (`\textup`) in _velika-mala_ (`\textulc`). To v resnici nista obliki, ampak uporabniški
ukazi. Prvi preklopi nazaj na pokončno pisavo, drugi pa onemogoči
male velike črke. Ukaz `\textnormal` je le
kombinacija obeh.

size (velikost).
: To se večinoma nadzira z možnostmi ukaza `\documentclass`, vendar o tem več kasneje.

Če želite spremeniti enega od prvih treh parametrov v danem besedilu, preprosto uporabite ukaze, kot je `\ukaz{dano besedilo}`. Npr. z ukazom `\textbf{To je krepko besedilo}` dobimo [**To je krepko besedilo**]{.latex-line} in z ukazom `\textit{To je poševno besedilo}` dobimo [*To je poševno besedilo*]{.latex-line}.

:::{admonition} Pazite!
:class: warning
Lahko združimo več ukazov, prikazanih zgoraj, (npr. `\textit{\textbf{To je krepko in poševno besedilo}}` proizvaja [**_To je krepko in poševno besedilo_**]{.latex-line}; vendar niso vse kombinacije na voljo. LaTeX bo pritoževal, če boste poskusili uporabiti kombinacijo, ki ne obstaja.
:::

Vsi zgornji ukazi imajo različico _switch_. Namesto da bi prejeli besedilo prek argumenta, trajno spremenijo pisavo, dokler se ta ponovno ne spremeni. V [Tabeli %2](#tab-pisave) so prikazani vsi ukazi in njihove različice _switch_.

::::{prf:example}
:label: latexUvod_eg-switch
`````{tab-set}
````{tab-item} LaTeX
```latex
Ukazi, kot je \texttt{\textit{argument}},
vplivajo samo na \textit{argument}. 
Če uporabimo različico switch, se vse, 
kar je po ukazom \texttt{\itshape} \itshape,  
spremeni in ostane tako, dokler se ne pojavi drug \texttt{upshape}. 
Zdaj je vse tako, kot je bilo prej.
```
````

````{tab-item} PDF
```{figure} ./img/01_eg-switch.png
:name: eg-switch 
:alt: Switch ukazi v LaTeXu
```
````
`````
::::   


::::{tab-set}
````{tab-item} Pisave
```{list-table} Pisave v LaTeXu
:header-rows: 1
:label: tab-pisave

* - Pisava
  - Ukaz (za argument)
  - Ukaz (switch)
* - pokončna serifna pisava
  - `\textrm{<besedilo>}` 
  - `\rmfamily`
* - gladka pisava
  - `\textsf{<besedilo>}`
  - `\sffamily`
* - strojepisna pisava
  - `\texttt{<besedilo>}`
  - `\ttfamily`
* - srednja debelina
  - `\textmd{<besedilo>}`
  - `\mdseries`
* - krepka pisava
  - `\textbf{<besedilo>}`
  - `\bfseries`
* - poševna pisava
  - `\textit{<besedilo>}`
  - `\itshape`
* - *ležeča pisava*
  - `\textsl{<besedilo>}`
  - `\slshape`
* - male velike črke
  - `\textsc{<besedilo>}`
  - `\scshape`
* - pokončna
  - `\textup{<besedilo>}`
  - `\upshape`
* - velika-mala
  - `\textulc{<besedilo>}`
  - `\ulcshape`
* - privzeta pisava
  - `\textnormal{<besedilo>}`
  - `\normalfont`
```
```` 
````{tab-item} LaTeX
```{figure} ./img/01_tab-pisave.png
:name: pisave 
:alt: Pisave v LaTeXu
```
```` 
::::

Poleg zgoraj navedenih ukazov lahko ustvarimo tudi podčrtano besedilo (`\underline{besedilo}`) in poudarjeno besedilo (`\emph`).
Delovanje ukaza `\emph{besedilo}` je odvisno od konteksta. Običajno ustvari besedilo, ki je zelo podobno besedilu, ustvarjenemu z ukazom \textitt, vendar ni namenjeno za pisanje poševna pisava. Poglejte {prf:ref}`latexUvod_eg-emph` za primer. 

:::{prf:example}
:label: latexUvod_eg-emph
`````{tab-set}
````{tab-item} LaTeX
```latex
To je \underline{podčrtano} besedilo. 
Izgleda \underline{malo} \underline{grdo}, 
zato ga ne uporabljajmo pogosto.

To je \emph{poudarjeno} besedilo.

\textit{To je poševno besedilo, v 
katerem je \emph{poudarjeno} besedilo.}

\emph{Ta \emph{poudarjeno besedilo} 
je obdan s poudarjenim besedilom \dots 
ali je \emph{res} poudarjen?}
```
````

````{tab-item} PDF
```{figure} ./img/01_eg-emph.png
:name: eg-emph 
:alt: Ukaz emph v LaTeXu
```
````
`````
:::

::::{exercise}
:label: ex_pisave
Uporabite različne pisave, da reproducirajte naslednje besedilo. 
Delajte s besedilom v res majhnih delih.

```{figure} /img/01_ex-pisave.png
:name: latexUvod-ex-pisave
:alt: Različne pisave v LaTeXu
```
::::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```

:::{solution} ex_pisave
:class: tip dropdown
Možna rešitev je:
``` latex
Praviloma pisave izbiramo premišljeno, ali pa izbor kar prepustimo LaTeXu.
Besedilo lahko \emph{poudarimo} ali zapišemo \textbf{krepko}, ali pa \emph{\textbf{oboje skupaj}}.
Kaj se zgodi, če \emph{uporabimo poudarjeno \emph{znotraj} poudarjenega besedila}?
Seveda \textbf{lahko nastavimo tudi \textnormal{običajno} pisavo}.
Besedilo lahko tudi \underline{podčrtamo}, vendar tega ne priporočamo, \underline{ker} \underline{je grdo}.

Pišemo lahko tudi v \textsf{sans-serifni pisavi} ali pa \textsc{z malimi velikimi črkami},
denimo \textsc{SageMath}. 
\textsl{Ležeča pisava} {ni ista reč kot} \textit{poševna pisava}.
Poševna pisava uporablja \textit{drugačne glife}, 
ležeča pisava pa uporablja \textsl{iste glife}, vendar ležečo. 
Razlika je res očitna, če pogledate 
\textit{poševno pisano črko a} poleg \textsl{ležeče črke a}.

Včasih uporabimo tudi \texttt{pisavo fiksne širine}, 
v kateri so vsi znaki enako široki.
```
:::
Za razliko od večine urejevalnikov besedil WYSIWTG (Word, itd.) LaTeX nima izrecnega načina za določanje velikosti pisave.
Dejanska velikost besedila je odvisna od možnosti argumenta `\documentclass` (`10pt`, `11pt` ali `12pt`).
To pomeni, da bo navadno besedilo velikosti `10pt` (oz. `11pt` ali `12pt`).
Velikost pisave za druge dele besedila bo določena ustrezno.

Če resnično želimo spremeniti velikost pisave za določen del besedila, uporabimo ukaze v [Tabli %s](#tab-velikostiPisave). 
Natančneje, ti ukazi niso LaTeX ukazi, ampak TeX ukazi (to pomeni, da niso sodobni ukazi). 
Zaradi tega je njihova sintaksa nekoliko drugačna. 
Delujejo kot `{\velikost <besedilo>}`, kjer `velikost` je eden od ukazov iz tabele in `besedilo` je besedilo, ki ga želimo spremeniti.
Npr. z ukazom `{\Huge  To je največje besedilo, ki ga lahko ustvari LaTeX.}`  dobimo stavek:

:::{div}
:class: latex-block Huge
To je največje besedilo, ki ga lahko ustvari LaTeX.
:::

V [Tabeli %s](#tab-velikostiPisave) podajamo dejansko velikost za vsako od njih ter relativno primerjavo med različnimi velikostmi.

::::{tab-set}
````{tab-item} Velikosti pisave
```{list-table} Velikosti pisave v LaTeXu
:header-rows: 1
:name: tab-velikostiPisave
* - Ukaz
  - `10pt`
  - `11pt`
  - `12pt`
* - `\tiny`
  - 5 pt
  - 6 pt
  - 6 pt
* - `\scriptsize`
  - 7 pt
  - 8 pt
  - 8 pt
* - `\footnotesize`
  - 8 pt
  - 9 pt
  - 10 pt
* - `\small`
  - 9 pt
  - 10 pt
  - 11 pt
* - `\normalsize`
  - 10 pt 
  - 11 pt
  - 12 pt
* - `\large`
  - 12 pt
  - 12 pt
  - 14,4 pt
* - `\Large`
  - 14.4 pt
  - 14,4 pt
  - 17,28 pt
* - `\LARGE`
  - 17,28 pt
  - 17,28 pt
  - 20,74 pt
* - `\huge`
  - 20,74 pt
  - 20,74 pt
  - 24,88 pt
* - `\Huge`
  - 24,88 pt
  - 24,88 pt
  - 24,88 pt
```
```` 
````{tab-item} LaTeX
```{figure} ./img/01_tab-velikostiPisave.png
:name: velikostiPisave 
:alt: Velikosti pisave v LaTeXu
Velikosti pisave v LaTeXu
```
````
::::

Mnoge od teh ukazov imajo svojo sodobno različico v obliki okolja. Namesto da napišete `{\small majhna pisava}`, lahko na primer napišete `\begin{small} majna pisava \end{small}`.

::::{exercise}
:label: ex_VelikostiPisave
Uporabite različne velikosti pisave in pisave, da reproducirajte naslednje besedilo.

```{figure} /img/01_ex-velikostiPisave.png
:name: latexUvod-ex-VelikostiPisave
:alt: Različne pisave v LaTeXu
```

::::

```{margin} 
[Seznam vaj](#latexUvod_vaje)
```
::::{solution} ex_VelikostiPisave
:class: tip dropdown
Ste goljufali in pogledali rešitev?
```{admonition} Opozorilo!
:class: warning
V resnici ni potrebno, da natančno sledite velikostim pisave.
Preveč igranja s pisavami in velikostmi pisav je v nasprotju s [filozofijo LaTeXa](#latex_filozofija). 
```

Če ste resnično radovedni, tukaj je možna rešitev:


``` latex
\underline{\textbf{Pom\textsc{nite}\Huge!}} \textit{Čim}
\textsf{V\textbf{\LARGE E}}\textit{č} pisav \Huge uporabljate
\footnotesize \textbf{v} vašem \small \texttt{dokumentu},
\large \textit{tem} \normalsize lažje \textsc{berljiv} in
\textsl{\textsf{lepši} pos\large t\Large a\LARGE n\huge e}.
```
::::


(latexUvod-warningSize)=
:::{admonition} Opozorilo!
:class: error
To je res pomembno, zato je vredno ponoviti: 
Preveč igranja s pisavami in velikostmi pisav je v nasprotju s [filozofijo LaTeXa](#latex_filozofija).
Ne pozabite, da moramo LaTeXu prepustiti oblikovanje, medtem ko se **mi osredotočimo na vsebino**.
:::

(latexUvod_vaje)=
## Vaje


Vsako poglavje v tej knjigi se konča s povzetkom različnih vaj ter dodatnimi vajami ali domačimi Vajami. Tukaj je ustrezna vaja za prvo poglavje:

- [Vaja %s](#ex-overleafRacun): Ustvarjanje računa v Overleafu. 
- [Vaja %s](#ex_latex_prvaDatoteka): Ustvarjanje prve LaTeX datoteke.
- [Vaja %s](#ex_latex_avtorNaslovDatum): Dodajanje avtorja, naslova in datuma.
- [Vaja %s](#ex_latex_babel): Uporaba paketa `babel`.
- [Vaja %s](#ex_latex_komentarji): Uporaba komentarjev in posebnih znakov.
- [Vaja %s](#ex_latex_posebniZnaki): Uporaba posebnih znakov.
- [Vaja %s](#ex_VezajiPomisljajiNarekovaji): Uporaba vezajev, pomišljajev in narekovajev.
- [Vaja %s](#ex_pisave): Uporaba različnih pisav.
- [Vaja %s](#ex_VelikostiPisave): Uporaba različnih velikosti pisav.


:::{exercise} Domača Vaja
:nonumber:
1. Napišite novo datoteko z imenom `DN1.tex`.
1. Z njo ustvarite dokument z naslovom _Poučevanje slovenščine mojega učitelja"_
1. Dodajte svoje ime kot avtorja in današnji datum.
1. Ne pozabite uporabite paket `babel` z možnostjo `slovene`. 
1. V dokumentu mi opišite svoj dan ali napišite kratko otroško zgodbo, ali pa mi povejte zabavno anekdoto, izbira je vaša!  Pomembno je, da vadite pisanje v LaTeXu, jaz pa bom vadil branje slovenskega jezika.
1. Uporabite različne pisave in velikosti pisav, da bo vaše besedilo bolj zanimivo (ampak ne preveč!).
1.  Domačo nalogo oddajte kot datoteko `.zip` prek spletne učilnice. Če ne veste, kako pridobiti datoteko `.zip` iz Overleafa, poglejte [](./B_izvozIzOverleaf).
:::


