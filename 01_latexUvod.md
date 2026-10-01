(latexUvod)=
# Uvod v LaTeX

:::{admonition} Cilji poglavja
:class: seealso
Po tem poglavju boste znali:

- ustvariti in prevesti dokument v Overleafu,
- razložiti razliko med ukazom in okoljem ter med preambulo in telesom dokumenta,
- dokumentu dodati naslov, avtorja in datum,
- pravilno zapisati posebne znake, vezaje, pomišljaje in slovenske narekovaje,
- izbrati pisavo in velikost pisave ter vedeti, zakaj tega večinoma ne počnemo.

Predvideni čas: 2 do 3 pedagoške ure.
:::

(latexUvod_kajJeLaTeX)=
## Kaj je LaTeX?

LaTeX je _stavni sistem_: program, ki iz besedila in navodil o njegovi zgradbi samodejno postavi dokument vrhunske tipografske kakovosti.

Zgrajen je na programu TeX, ki ga je leta 1978 razvil Donald E. Knuth.
Prvo različico LaTeXa je leta 1983 napisal Leslie Lamport (od tod ime: **La**mport **TeX**).
Gre za zbirko dodatnih ukazov za TeX, ki avtorju omogočajo, da dokument opiše po njegovi _zgradbi_ (naslov, razdelek, poudarek), oblikovanje pa prepusti že pripravljenim profesionalnim vzorcem.

Trenutna standardna verzija je LaTeX2e (1994), zanj pa je odgovoren Frank Mittelbach. LaTeX se izgovori 'láteh', po angleško pa običajno rečemo 'lejteh'.

Čeprav je LaTeX2e star že več kot trideset let, se njegovo jedro posodablja dvakrat letno.
Zato marsikateri nasvet, ki ga najdete na spletu, danes ni več potreben. Na to bomo sproti opozarjali.

Ko želi _avtor_ kaj objaviti, pošlje svoj rokopis založniku.
Tam _knjižni opremljevalec_ določi obliko dokumenta (širino stolpcev, obliko črk, velikost presledkov pred in po naslovih ...).
Opremljevalec svoja navodila skupaj z rokopisom preda _črkostavcu_, ki na podlagi teh podatkov stavi knjigo.

Pri delu z LaTeXom obe vlogi, opremljevalca in črkostavca, prevzame program sam.
Vam ostane samo še vloga avtorja (glej [Sliko %s](#kaj-je-latex)).

:::{figure} ./img/01_osnovne.png
---
width: 80%
name: kaj-je-latex
class: dark-light
alt: Avtor preda rokopis knjižnemu opremljevalcu, ta svoja navodila črkostavcu, ki dokument stavi. LaTeX prevzame zadnji dve vlogi.
---
Pot rokopisa od avtorja do natisnjene knjige. LaTeX prevzame vlogi knjižnega opremljevalca in črkostavca.
:::

(latex_filozofija)=
:::{admonition} Filozofija LaTeXa
:class: important
Oblikovanje dokumentov z LaTeXom sledi naslednjemu načelu:

> Mi (avtorji) se ukvarjamo z **vsebino** dokumenta, LaTeX pa poskrbi za **oblikovanje**.

Ali, enakovredno,

> Ne skrbimo za **oblikovanje**, zato se lahko osredotočimo na **vsebino**.
:::



(latexUvod_KajZmoreLaTeX)=
## Kaj zmore LaTeX?

LaTeX zmore skoraj vse, kar zmorejo urejevalniki besedil, kot sta Word in Google Docs.
Posebej dobro pa se obnese pri besedilih z veliko matematičnimi formulami in simboli, saj samodejno poskrbi tudi za tabele, grafe, kazala, sklice in bibliografijo.

Za učitelja matematike to pomeni predvsem troje:

- **delovni listi, testi in izpiti**, v katerih so formule postavljene pravilno in vsakič enako;
- **gradiva, ki jih je mogoče popraviti in znova uporabiti**: naslednje leto zamenjate le podatke, oblika ostane nedotaknjena;
- **zaključna dela in strokovni prispevki**, pri katerih je LaTeX pogosto kar zahteva založnika ali fakultete.

Čeprav je LaTeX optimiziran za znanstvena in tehnična besedila, ni omejen samo nanje.
Sam ga danes uporabljam za vse dokumente, ki naj bodo videti profesionalni ali lepi, od osebnih in poslovnih pisem do pesmarice za igranje kitare.

Vprašal sem svoje sodelavce, kaj delajo z LaTeXom.
Tukaj je nekaj zanimivih odgovorov:

- **zaključna dela (diplome, magistrska dela, doktorati);**
- knjige, članke in zapiske predavanj;
- predstavitve, s pomočjo Beamerja [](./06_latexBeamer.md);
- strokovno dokumentacijo (npr. CV, projektne vloge);
- pisma in najemne pogodbe;
- pravila za družabne igre;
- note (za glasbo);
- objave na Facebooku in Instagramu ter celo SMS-e (da, res je!).

Če vas zanima, si lahko tukaj ogledate [mojo doktorsko disertacijo](https://anteromontonio.github.io/assets/pdf/2019_Mon_phDThesis.pdf), ki je bila napisana izključno z uporabo programa LaTeX.

(latexUvod_latexNiWord)=
## LaTeX ni Word

MS Word, Google Docs in LibreOffice Writer so urejevalniki tipa **WYSIWYG** (_What You See Is What You Get_, tj. kar vidiš, to tudi dobiš).
V njih avtor obliko dokumenta določa interaktivno, med samim vnašanjem besedila, in ves čas na zaslonu vidi, kakšen bo dokument, ko bo natisnjen.
Strukturo in obliko torej urejate hkrati s pisanjem. Pri daljših projektih se je ob tem zelo lahko izgubiti.

LaTeX deluje po drugačnem načelu, ki mu pravimo **WYSIWYM** (_What You See Is What You Mean_, tj. kar vidiš, to tudi misliš).
Med tipkanjem ne vidite končne oblike, ampak opisujete **pomen** posameznih delov besedila: to je naslov, to je poudarek, to je izrek.
Končno obliko vidite šele, ko datoteko prevedete (ne skrbite, to je zelo enostavno in hitro). Za enkrat, pomembno je da razumete razliko: v Wordu kar avtor piše je tudi končna oblika, v LaTeXu pa avtor piše le pomen besedila, obliko pa določa LaTeX. Enakomerno, LaTeX torej avtorja sili, da določi logično strukturo besedila, sam pa nato izbere najprimernejšo obliko.

(latexUvod_zakaj)=
### Zakaj LaTeX?

Predstavljajmo si, da pišete roman v svojem najljubšem urejevalniku WYSIWYG.
V tej knjigi se odvijata dve vzporedni zgodbi v različnih dimenzijah.
Da bi bralcu sporočili, katera od dimenzij je trenutno opisana, ste se odločili, da boste za vsako uporabili svojo barvo.
Vaša knjiga bi tako lahko bila videti takole:

:::{div}
:class: latex-block text-blue
„Ne, ne moreš me zapustiti!“ je zaklical Peredur Lancelotu.\
„Moram,“ je odgovoril. „Usoda me kliče. Toda ponovno se bova srečala. Obljubim.“
:::

:::{div}
:class: latex-block text-green
Shao je občutila nepojasnjeno žalost, kot da bi pravkar izgubila nekaj ali nekoga, ki ji je bil pomemben.\
„Si v redu?“ je vprašala Ashby, medtem ko je jedla svojo kašo.\
„Ne izgledaš dobro.“\
„V redu sem, samo utrujena.“
:::

Ko ste končali prvi osnutek (ki obsega 300 strani), ste ga po e-pošti poslali prijatelju, da bi vam povedal svoje mnenje.
Izkazalo se je, da njegov tiskalnik tiska samo črno-belo, zato vaši barvi zanj ne pomenita ničesar.

Enostavna rešitev! Vse zeleno besedilo spremenite v kurzivno pisavo, ostalo pa pustite pokončno.
Ko ste ročno predelali že prvih 120 strani, pa ste se spomnili, da kurzivno pisavo ponekod uporabljate tudi za poudarjanje, na primer:
[Ali boš *to* jedla?]{.latex-line .text-green}
Zdaj boste morali pregledati še vsak odstavek posebej, poiskati vse take poudarke in jih spremeniti v kak drug slog. Šele nato lahko preostalo zeleno besedilo mirno spremenite v kurzivo.

**Vidite neskončni problem?**

LaTeX ta problem reši drugače.
V besedilo ne zapišete barve, ampak povete, **kaj** posamezen odlomek je, recimo `\dimenzijaA{...}` in `\dimenzijaB{...}`, kako naj bo videti, pa določite na enem samem mestu v preambuli.
Ko prijatelj potrebuje črno-belo različico, spremenite tisto eno vrstico in vseh 300 strani se popravi samo.
Kako se take ukaze definira, boste izvedeli v poglavju [](./05_latexRazno.md).


(latexUvod_kakoDeluje)=
## Kako deluje LaTeX?

Postopek je preprost:

1. V datoteko s končnico `.tex` (npr. `ime_datoteke.tex`) napišete besedilo skupaj z ukazi za LaTeX.
2. Datoteko _prevedete_ s programom `pdflatex`, ki iz nje naredi `ime_datoteke.pdf`.
3. Nastalo datoteko PDF lahko natisnete ali pošljete naprej.

V Overleafu se drugi korak zgodi samodejno, ko datoteko shranite, zato se vam z njim ne bo treba ukvarjati.

:::{admonition} Opomba!
:class: note
Včasih je treba datoteko prevesti dvakrat.
Kadar dokument vsebuje kazalo, sklice ali literaturo, mora LaTeX podatke najprej zbrati in jih šele ob naslednjem prevajanju postavi na pravo mesto.

Poleg datoteke PDF pri prevajanju nastane še nekaj pomožnih datotek (`.aux`, `.log`, `.out`).
Brisati jih ni treba; v datoteki `.log` se skrivajo sporočila o napakah.
:::

Zgodovinsko je bila pot nekoliko daljša: program `latex` je iz datoteke `.tex` naredil datoteko `.dvi`, to pa je bilo treba s posebnim programom šele pretvoriti v `.pdf`.
Datotek `.dvi` danes skoraj nihče ne uporablja, saj jih večina programov ne zna odpreti.

:::{figure} ./img/01_datoteke.png
---
width: 80%
name: kako-deluje-latex
class: dark-light
alt: Stara pot vodi iz datoteke .tex prek prečrtane datoteke .dvi do .pdf, program pdflatex pa pelje neposredno iz .tex v .pdf.
---
Pot od izvorne datoteke do dokumenta PDF. Stara pot prek datoteke `.dvi` je prečrtana: danes uporabljamo `pdflatex`, ki gre naravnost iz `.tex` v `.pdf`.
:::


(latexUvod_kakoZaceti)=
## Kako začeti z LaTeXom?

LaTeX lahko namestite na svoj računalnik; če to želite, poglejte [](./A_namescanjeLatexa.md).

Mi bomo ubrali drugačno pot in delali kar v brskalniku, prek **Overleafa**, ki je platforma za urejanje in prevajanje dokumentov LaTeX.
Tako vam ni treba ničesar nameščati, do svojih projektov pa lahko dostopate z vsakega računalnika.
Najprej si morate ustvariti račun.


:::{exercise}
:label: ex-overleafRacun

Ustvarite si račun v Overleafu.
:::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

:::{solution} ex-overleafRacun
:class: dropdown
1. Pojdite na [Overleaf](https://www.overleaf.com/).
2. Kliknite na gumb "Register" v zgornjem desnem kotu strani.
3. Odprla se bo stran, na kateri lahko ustvarite račun na različne načine, med drugim z uporabo e-poštnega ali Google računa.
4. Če izberete možnost registracije z e-pošto, morate vnesti svoje ime, e-poštni naslov in ustvariti geslo. Nato kliknite na gumb "Register". V tem primeru boste morda morali potrditi svoj e-poštni naslov.
:::

:::{admonition} Nasvet!
:class: tip
Ko boste ustvarili prvi projekt, si oglejte še te nastavitve (gumb "Menu" zgoraj levo):

- "Compiler" (prevajalnik): pustite `pdfLaTeX`, saj ga bomo uporabljali v celotnem učbeniku.
- "Spell check" (črkovalnik): nastavite na slovenščino, sicer vam bo Overleaf podčrtal domala vsako besedo.
- "Main document" (glavna datoteka): pove, katero datoteko naj Overleaf prevede, kadar jih je v projektu več.

Brezplačni račun ima omejen čas prevajanja. Za naše dokumente je to povsem dovolj, pri zelo dolgih projektih pa se lahko zgodi, da prevajanje ne uspe.
:::




(latexUvod_ukaziOkolja)=
## Ukazi in okolja

Kot smo [že omenili](#latex_filozofija), se moramo pri delu z LaTeXom osredotočiti na vsebino, oblikovanje pa prepustiti LaTeXu.
Ker pa je LaTeX "samo" računalniški program, potrebuje natančna navodila.
Avtor mora navesti dodatne podatke, ki opisujejo logično strukturo njegovega besedila.
Te podatke zapišemo z _ukazi_ in _okolji_, ki jih vpisujemo med besedilo.

Z ukazi dajemo LaTeXu posamezna navodila. Splošna oblika ukaza je:

```latex
\imeUkaza[neobvezni argument]{obvezni argument}
```

- Ukaz se *vedno* začne z znakom `\`.
- Obveznih argumentov je lahko več, npr. `{prvi}{drugi}...{zadnji}`, lahko pa jih ni nobenega: ukazi brez argumentov, kot so `\today`, `\maketitle` in `\tiny`, so čisto običajni.
- Neobvezne argumente pišemo v oglate oklepaje; kadar jih je več, jih ločimo z vejicami: `[prvi, drugi, ..., zadnji]`. Če jih ne potrebujemo, oglatih oklepajev sploh ne napišemo.

:::{admonition} Pazite!
:class: warning
LaTeX razlikuje med velikimi in malimi črkami: `\Large` in `\large` sta dva različna ukaza.

Ime ukaza se konča pri prvem znaku, ki ni črka. Presledek, ki sledi imenu ukaza, LaTeX požre, zato `\LaTeX je lep` izpiše "LaTeXje lep". Če želimo presledek obdržati, napišemo `\LaTeX{} je lep` ali `\LaTeX\ je lep`.
:::

Okolje je posebna vrsta ukaza z naslednjo strukturo:

```latex
\begin{okolje}
  Vsebina okolja: ukazi in besedilo
\end{okolje}
```

Okolja običajno določajo, kako bo del besedila postavljen v dokumentu.

Zaenkrat vam ni treba skrbeti, kako ukazi in okolja delujejo.
Spoznavali jih bomo sproti, v poglavju [](./02_latexOsnovnaOkolja.md) pa si bomo podrobneje ogledali nekatera najpomembnejša okolja.

(latexUvod_preambulaTelo)=
## Preambula in telo datoteke

Vsaka datoteka LaTeX ima naslednjo obliko:

```latex
% --- preambula ---
\documentclass{...}

\usepackage{...}
% ...

\begin{document}
% --- telo dokumenta ---
Vsebina dokumenta.
\end{document}
```

Najpomembnejše okolje v LaTeXu je okolje `document`.
V vsakem dokumentu nastopa natanko enkrat, vanj pa napišemo dejansko vsebino.
Vse, kar je znotraj tega okolja, se imenuje _telo_ dokumenta.

Prav tako nepogrešljiv je ukaz `\documentclass`, s katerim se začne vsaka datoteka.
Vse od ukaza `\documentclass` do začetka okolja `document` se imenuje _preambula_.
V preambuli nastavimo splošno delovanje LaTeXa: naložimo pakete, določimo jezik, avtorja, naslov ...

:::{admonition} Opozorilo!
:class: warning
V preambulo sodijo samo ukazi, ne pa besedilo. To gre v telo dokumenta.
Nekatere ukaze je celo dovoljeno uporabiti *samo* v preambuli.
Zelo pogosta napaka v LaTeXu je, da del kode napišemo na napačno mesto.
:::

Ukaz `\documentclass` določa vrsto dokumenta, ki ga želimo ustvariti.
Uporabljamo ga takole:

```latex
\documentclass[možnosti]{razred}
```

Tu `razred` določa vrsto dokumenta (npr. članek, knjiga, poročilo ...), `možnosti` pa so dodatne nastavitve, ki vplivajo na videz dokumenta (npr. velikost pisave, velikost papirja ...).
V [Tabeli %s](#tab_latex_razredi) so prikazani različni razredi dokumentov LaTeX.

:::{list-table} Razredi dokumentov LaTeX
:header-rows: 1
:label: tab_latex_razredi

* - Razred
  - Opis
* - `article`
  - za članke v znanstvenih revijah, kratka poročila in druge krajše dokumente.
* - `proc`
  - razred za zbornike, ki temelji na razredu *article*.
* - `report`
  - za daljša poročila, ki vsebujejo več poglavij, manjše knjige, doktorske disertacije ...
* - `book`
  - za prave knjige.
* - `beamer`
  - za predstavitve.
* - `letter`
  - za pisma.
:::

V tem učbeniku bomo obravnavali le razreda `article` in `beamer` (glej [](./06_latexBeamer.md)), vendar bo večino tega, kar se bomo naučili, mogoče brez težav uporabiti tudi v drugih razredih.

Nekatere uporabne `možnosti` so `10pt` (prim. `11pt`, `12pt`), `a4paper` (prim. `letterpaper`), `onecolumn` (prim. `twocolumn`).
Privzete možnosti za razred `article` so `[letterpaper, 10pt, oneside, onecolumn, final]`.

:::{admonition} Nasvet!
:class: tip
Privzeta velikost papirja je ameriška (`letterpaper`), zato pri nas skoraj vedno dodamo možnost `a4paper`.
:::

:::{admonition} Opomba
:class: note
Med možnostmi ukaza `\documentclass` lahko navedemo tudi jezik dokumenta, npr. `\documentclass[a4paper, 12pt, slovene]{article}`.
O jezikih bomo podrobneje govorili v razdelku [](#latexUvod_jezikPaketi), zato tega zdaj še ne potrebujemo.
:::

:::{exercise}
:label: ex_latex_prvaDatoteka

Napišite svoj prvi dokument z LaTeXom:

1. Na Overleafu kliknite "new project" (nov projekt) in izberite "blank project" (prazen projekt). Projekt poimenujte, npr. `MatTeh_latexUvod`.
2. Overleaf ustvari datoteko `main.tex`. Z desnim klikom nanjo izberite "Rename" (preimenuj) in jo preimenujte v `prvaDatoteka.tex`.
3. Izbrišite vse, kar je v datoteki.
4. Napišite vrstico `\documentclass[10pt]{article}`.
5. Pod njo napišite še vrstici `\begin{document}` in `\end{document}`.
6. Med njiju napišite nekaj besedila in shranite (<kbd>Ctrl</kbd>+<kbd>S</kbd> oz. <kbd>Cmd</kbd>+<kbd>S</kbd>).
7. Vrstico `\documentclass[10pt]{article}` zamenjajte z vrstico `\documentclass[12pt]{article}` in spet shranite.
:::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

::::::{solution} ex_latex_prvaDatoteka
:class: dropdown
Tukaj je primer, kako bi lahko bila videti vaša datoteka `prvaDatoteka.tex`:

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[12pt]{article}
\begin{document}
  To je moja prva datoteka v LaTeXu. V njej bom napisal ljubezensko pismo Juliji.
\end{document}
```
::::

::::{tab-item} 10pt
:::{figure} ./img/01_prvaDatoteka10pt.png
:name: prvaDatoteka_10pt
:alt: prvaDatoteka.tex, prevedena z možnostjo 10pt
:::
::::

::::{tab-item} 12pt
:::{figure} ./img/01_prvaDatoteka12pt.png
:name: prvaDatoteka_12pt
:alt: prvaDatoteka.tex, prevedena z možnostjo 12pt
:::
::::
:::::

- Ko shranite datoteko, bo Overleaf samodejno prevedel vaš dokument in prikazal rezultat na desni strani zaslona.
- Če se to ne zgodi, kliknite na gumb "Recompile" (prevedi znova) na vrhu desnega okna.
- Ko velikost pisave spremenite iz `10pt` v `12pt`, se bo besedilo na desni povečalo.
- Če spremembe ne opazite, znova kliknite "Recompile". Morda boste morali napisati več besedila, da bo razlika vidna.
::::::

:::{admonition} Nasvet!
:class: tip
Prej ali slej se bo zgodilo, da Overleaf namesto dokumenta pokaže sporočilo o napaki.
Ne skrbite, to se dogaja tudi izkušenim uporabnikom in je del običajnega dela z LaTeXom.

1. Kliknite na rdeči števec napak nad predogledom. Overleaf bo izpisal seznam napak in vrstice, v katerih jih je našel.
2. Napaka je pogosto **nekaj vrstic višje**, kot pravi Overleaf: LaTeX težavo opazi šele, ko nanjo naleti.
3. Tri najpogostejše napake na začetku so:
   - manjkajoč `\end{...}` za neko okolje;
   - poseben znak, zapisan brez `\` (npr. `%` ali `_`), o teh govori razdelek [](#latexUvod_komentari);
   - sporočilo `Undefined control sequence`, ki pomeni, da je ime ukaza napačno zapisano (pozor na velike in male črke!).
4. Če se ne znajdete, kliknite "Raw logs" (dnevnik prevajanja) in poiščite prvo vrstico, ki se začne z `!`.
:::

(latexUvod_avtorNaslovDatum)=
## Avtor, naslov in datum

Z ukazi `\title`, `\author` in `\date` lahko določimo naslov, avtorja in datum dokumenta.
Ti ukazi se običajno uporabljajo v preambuli, vendar jih lahko uporabimo tudi v telesu dokumenta.
Sami po sebi ne naredijo ničesar, dokler ne uporabimo ukaza `\maketitle`, ki izpiše naslov z vsemi podatki, ki smo jih določili z zgornjimi ukazi.
Upoštevajte, da morajo ukazi `\title`, `\author` in `\date` stati pred ukazom `\maketitle`, sicer LaTeX teh podatkov še ne pozna.
Poglejte [Primer %s](#eg-avtorNaslovDatum).

:::{prf:example}
:label: eg-avtorNaslovDatum
```latex
% --- preambula ---
\documentclass[12pt]{article}

\author{France Prešeren}
\title{Zdravljica}
\date{26.04.1848}

\begin{document}
% --- telo dokumenta ---
\maketitle
V tem dokumentu bom napisal ljubezensko pismo Juliji.
\end{document}
```
:::

:::{exercise}
:label: ex_latex_avtorNaslovDatum

1. Z uporabo ukazov `\author`, `\title` in `\date` dodajte avtorja, naslov in datum v vašo prvo datoteko LaTeX.
2. Shranite (<kbd>Ctrl</kbd>+<kbd>S</kbd> oz. <kbd>Cmd</kbd>+<kbd>S</kbd>).
3. Na vrh telesa dokumenta napišite ukaz `\maketitle` in spet shranite.
4. Zamenjajte datum s svojim rojstnim dnem in spet shranite.
5. Zamenjajte argument ukaza `\date` z ukazom `\today` in spet shranite.
:::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

::::::{solution} ex_latex_avtorNaslovDatum
:class: dropdown tip
Tukaj je primer, kako bi lahko bila videti vaša datoteka `prvaDatoteka.tex`:

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[12pt]{article}
\author{France Prešeren}
\title{Zdravljica}
\date{26.04.1848}
\begin{document}
\maketitle
  To je moja prva datoteka v LaTeXu. V njej bom napisal ljubezensko pismo Juliji.
\end{document}
```
::::
::::{tab-item} PDF (brez naslova)
:::{figure} ./img/01_avtorNaslovDatum_1.png
:name: avtorNaslovDatum_1
:alt: Dokument brez ukaza \maketitle, izpiše se samo besedilo.
:::
::::
::::{tab-item} PDF (z naslovom)
:::{figure} ./img/01_avtorNaslovDatum_2.png
:name: avtorNaslovDatum_2
:alt: Dokument z ukazom \maketitle, izpišejo se naslov, avtor in datum 26.04.1848.
:::
::::

::::{tab-item} PDF (z ukazom `\today`)
:::{figure} ./img/01_avtorNaslovDatum_3.png
:name: avtorNaslovDatum_3
:alt: Dokument z ukazom \today, datum je izpisan v angleščini.
:::
::::

- Ko shranite datoteko, bo Overleaf samodejno prevedel vaš dokument in prikazal rezultat na desni strani zaslona.
- Če ne, kliknite na gumb "Recompile" (prevedi znova) na vrhu desnega okna, da ročno prevedete dokument.
- Če spremenite datum v rojstni dan ali uporabite ukaz `\today`, boste opazili, da se bo datum na desni strani spremenil.
- Če ne vidite spremembe, znova kliknite na gumb "Recompile".
- Upoštevajte, da ukaz `\today` izpiše datum v angleščini. To bomo popravili v razdelku [](#latexUvod_jezikPaketi).
:::::
::::::

(latexUvod_jezikPaketi)=
## Paketi in jeziki

LaTeX je zelo prilagodljiv in razširljiv sistem.
Osnovni LaTeX ponuja le osnovne funkcije, vendar lahko z uporabo _paketov_ dodamo nove funkcije in možnosti.
Na voljo je okoli [6000 paketov](https://www.ctan.org/pkg).
Paketi so zbirke ukazov in okolij, ki jih lahko vključimo v naš dokument z ukazom:

```latex
\usepackage{ime_paketa}
```

:::{admonition} Opozorilo!
:class: warning
Ukaz `\usepackage{ime_paketa}` mora biti v preambuli, torej pred `\begin{document}`.
:::

Eden najpomembnejših paketov je `babel`, ki omogoča uporabo različnih jezikov.
Paket naložimo z ukazom:

```latex
\usepackage[jezik]{babel}
```

kjer `jezik` določa jezik, ki ga želimo uporabiti (npr. `slovene`, `english`, `spanish`, `french`, `german`, `italian`, ...).
Paket `babel` poskrbi za pravilno oblikovanje besedila glede na izbrani jezik, npr. za deljenje besed, narekovaje in imena mesecev.


:::{exercise}
:label: ex_latex_babel

1. V svojo prvo datoteko LaTeX dodajte vrstico `\usepackage[slovene]{babel}` v preambulo. Shranite in **poglejte datum!**
2. Zamenjajte `slovene` s `spanish` in spet shranite. **Poglejte datum!**
3. Spremenite ukaz nazaj v `\usepackage[slovene]{babel}` in spet shranite.
:::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

::::::{solution} ex_latex_babel
:class: dropdown
Tukaj prikazujemo, kako uporabimo paket `babel`.

:::::{tab-set}
::::{tab-item} LaTeX
```latex
\documentclass[10pt]{article}
\usepackage[slovene]{babel}

\author{France Prešeren}
\title{Zdravljica}
\date{\today}

\begin{document}
\maketitle
To je moja prva datoteka v LaTeXu. V njej bom napisal ljubezensko pismo Juliji.
\end{document}
```
::::

::::{tab-item} PDF (en)
:::{figure} ./img/01_babel_en.png
:name: babel_english
:alt: Naslov z datumom, izpisanim v angleščini, torej brez paketa babel.
:::
::::

::::{tab-item} PDF (sl)
:::{figure} ./img/01_babel_sl.png
:name: babel_slovene
:alt: Naslov z datumom, izpisanim v slovenščini, z ukazom \usepackage[slovene]{babel}.
:::
::::

::::{tab-item} PDF (es)
:::{figure} ./img/01_babel_es.png
:name: babel_spanish
:alt: Naslov z datumom, izpisanim v španščini, z ukazom \usepackage[spanish]{babel}.
:::
::::
:::::
::::::

:::{admonition} Nasvet!
:class: tip
V sodobnem LaTeXu jezika običajno ne navajamo pri posameznem paketu, ampak kot možnost celotnega dokumenta, torej v ukazu `\documentclass`:

```latex
\documentclass[a4paper, 12pt, slovene]{article}
\usepackage{babel}
```

Paket `babel` jezik prebere kar iz možnosti dokumenta, zato ga ni treba napisati še enkrat.
Prednost tega je, da isti jezik vidijo tudi vsi drugi paketi, ki se ravnajo po njem, zato se nam ne more zgoditi, da bi bil en del dokumenta v slovenščini, drug pa v angleščini.
:::

Z paketom `babel` lahko v dokumentu uporabljamo tudi več jezikov, npr. `\usepackage[english, slovene]{babel}`.
Upoštevajte, da je privzeti jezik tisti, ki je naveden **zadnji**, zato je v tem primeru privzeta slovenščina.
Še jasneje ga določimo z možnostjo `main`, npr. `\usepackage[main=slovene, english]{babel}`.
Na drug jezik nato preklopimo z ukazom `\selectlanguage{english}`, krajše odlomke pa zapišemo z ukazom `\foreignlanguage{english}{...}`.


::::{admonition} Opomba!
:class: note
V starih različicah LaTeXa nismo mogli preprosto pisati **č**, **š**, **ž**, **á**, **ü** ...
Te črke lahko vedno dobimo tudi z ukazi:

:::{table}
:align: center
| Ukaz     | Rezultat |
|:----------:|:----------:|
| `\v{c}`  | č        |
| `\v{s}`  | š        |
| `\v{z}`  | ž        |
| `\'{a}`  | á        |
| `\"{u}`  | ü        |
:::

V starejših predlogah in v nasvetih na spletu pogosto naletite tudi na naslednji vrstici:

```latex
\usepackage[utf8]{inputenc}  % kodiranje vhodne datoteke
\usepackage[T1]{fontenc}     % kodiranje pisav v izhodnem dokumentu
```

Paketa `inputenc` danes ne potrebujemo več, saj sodobni LaTeX privzeto bere datoteke v kodiranju UTF-8.
Paket `fontenc` z možnostjo `T1` pa je pri uporabi programa `pdflatex` še vedno koristen, saj poskrbi, da se šumniki pravilno izpišejo in da LaTeX besede z njimi pravilno deli (za cirilico bi namesto `T1` uporabili `T2A`).
::::



(latexUvod_komentari)=
## Komentarji, posebni znaki, prazne vrstice in presledki

::::{exercise}
:label: ex_latex_komentarji

1. Napišite naslednji stavek v svoj dokument:

   :::{div}
   :class: latex-block
   Več kot 50 % površine Slovenije pokriva gozd.
   :::

1. Shranite (<kbd>Ctrl</kbd>+<kbd>S</kbd>) in poglejte rezultat.
::::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

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

Če želimo izpisati simbol `%`, zapišemo `\%`.
Znak `%` je v LaTeXu poseben, kar pomeni, da ima zase pridržen pomen in ga ne moremo uporabiti kar tako.
Drugi posebni znaki v LaTeXu so prikazani v [Tabeli %s](#tab-posebniZnaki).

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

:::{admonition} Opomba!
:class: note
Znak `~` ima v LaTeXu še eno, veliko pogostejšo vlogo: pomeni _nedeljivi presledek_, torej presledek, na katerem se vrstica ne sme prelomiti.
Uporabljamo ga npr. v zapisih `Slika~1`, `5~cm` in `v~šoli`, da ena sama številka ali črka ne ostane sama na koncu vrstice.

Podobno `\\` ni ukaz za poševnico, ampak ukaz za prelom vrstice, o katerem bomo govorili niže.
:::


:::{admonition} Pogosta napaka!
:class: error
Pogosta napaka v LaTeXu je, da se pozabi uporabiti ukaz za enega od posebnih simbolov.
:::


::::{exercise}
:label: ex_latex_posebniZnaki

1. Napišite naslednji stavek v svoj dokument:

   :::{div}
   :class: latex-block
   Več kot 90 % Slovencev zasluži več kot 500 € na mesec, kar je približno 600 $.
   :::
::::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

::::::{solution} ex_latex_posebniZnaki
:class: tip dropdown
Pravilna rešitev je:
:::::{tab-set}
::::{tab-item} LaTeX
```latex
Več kot 90 \% Slovencev zasluži več kot 500 € na mesec, kar je približno 600 \$.
```
::::

::::{tab-item} PDF (privzeta pisava)
:::{figure} ./img/01_posebniZnaki_1.png
:name: posebniZnaki_1
:alt: Stavek s posebnimi znaki, izpisan s privzeto pisavo; znak za evro je videti grdo.
:::
::::

::::{tab-item} PDF (s paketom lmodern)
:::{figure} ./img/01_posebniZnaki_2.png
:name: posebniZnaki_2
:alt: Isti stavek, izpisan s pisavo lmodern; znak za evro je videti lepo.
:::
::::
:::::

Upoštevajte, da simbol za evro ni poseben, lahko ga preprosto uporabimo. 
Vendar pa je videti grdo, razlog za to pa je, da LaTeX uporablja nekoliko starejše pisave. 
To lahko popravimo z uporabo paketa `lmodern` (glej [](#latexUvod_pisave)).
::::::


### Vezaj in pomišljaj

Vezaj v LaTeXu dobimo z enim samim znakom `-`.
Pogoste uporabe vezaja so:
- sestavljene besede, npr. `informacijsko-komunikacijska tehnologija`: {span .latex-line}`informacijsko-komunikacijska tehnologija`;
- sklanjanje kratic, npr. `v NUK-u`: {span .latex-line}`v NUK-u`.

Pomišljaj v LaTeXu dobimo z dvema znakoma `--`.
Pogoste uporabe pomišljaja so:
- za označevanje obsega, npr. `strani 10--20`: {span .latex-line}`strani 10&ndash;20`;
- za ločevanje miselnih enot, npr. `LaTeX -- program za oblikovanje besedil -- je zelo prilagodljiv`: {span .latex-line}`LaTeX &ndash; program za oblikovanje besedil &ndash; je zelo prilagodljiv`.

S tremi znaki `---` dobimo daljši pomišljaj: {span .latex-line}`&mdash;`.
V slovenščini ga skoraj ne uporabljamo, pogost pa je v angleških besedilih.

:::{admonition} Pazite!
:class: warning
Vezaj `-` ni isto kot minus.
Minus je matematični znak in ga zapišemo v matematičnem načinu, torej `$-5$`: {span .latex-line}`&minus;5`.
Če napišemo samo `-5`, dobimo {span .latex-line}`-5`, kar je krajše in tipografsko napačno.
Zaenkrat o tem ne skrbite, saj se bomo o matematičnem načinu pogovarjali v razdelku [](./03_latexMatematika.md).
:::


### Narekovaji

LaTeX ima posebna pravila za tiskanje narekovajev: 

- Enojne narekovaje dobimo z uporabo znakov ``` ` ``` in ``` ' ```, npr. ``` `narekovaj' ```: {span .latex-line}`&lsquo;narekovaj&rsquo;`.
- Dvojne narekovaje dobimo z uporabo znakov ``` `` ``` in ``` '' ```, npr. ``` ``narekovaji'' ```: {span .latex-line}`&ldquo;narekovaji&rdquo;`.
- Za slovenske narekovaje uporabimo ukaza ``` \glqq ``` in ``` \grqq ```, npr. ``` \glqq slovenski narekovaji\grqq ```: {span .latex-line}`„slovenski narekovaji“`.
- Če uporabimo `\usepackage[slovene]{babel}`, lahko preprosto napišemo ``` "` ``` in ``` "' ```, npr. ``` "`slovenski narekovaji"' ```: {span .latex-line}`„slovenski narekovaji“`.
- Lahko uporabimo tudi ```">``` in ``` "< ```, npr. ``` ">slovenski narekovaji"< ```: {span .latex-line}`»slovenski narekovaji«` (potreben je tudi paket `babel`). 

::::{exercise}
:label: ex_VezajiPomisljajiNarekovaji

V svojem dokumentu napišite naslednje besedilo. Pazite, da uporabite pravilne znake za vezaje, pomišljaje in narekovaje.


:::{figure} ./img/01_ex-vezajPomislajNarekovaji.png
:name: latexUvod-ex-vezajPomislajNarekovaji
:alt: Uporaba vezajev, pomišljajev in narekovajev v LaTeXu.
:::
::::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

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

Ko pišemo besedilo v \LaTeX u, moramo paziti, da uporabljamo pravilne simbole. Poleg zgoraj navedenih simbolov ima \LaTeX\ tudi poseben ukaz za \dots, in sicer \dots{}  (prim. ...).
```
:::


:::{admonition} Pogosta napaka!
:class: error
Pogosta napaka v LaTeXu je, da uporabljamo ravne narekovaje (``"`` in ``'``) ali pa napačno uporabljamo ukaze za narekovaje, npr.

- `"narekovaji"` 
- ``` ``narekovaji`` ```
:::




### Presledki

- Poljubno število presledkov (ali tabulatorjev) med besedami se obravnava kot en sam presledek.
- Presledek na začetku vrstice se ignorira.
- Nova vrstica se obravnava kot presledek, če ni prazna.
- Prazna vrstica se obravnava kot konec odstavka in začne nov odstavek.
- Zaporedne prazne vrstice se obravnavajo kot ena sama prazna vrstica.
- Prazen komentar `%` ni prazna vrstica.
- Presledek takoj za imenom ukaza LaTeX požre, glej razdelek [](#latexUvod_ukaziOkolja).

::::::{prf:example}
:label: latexUvod_primerspresledki
:::::{tab-set}
::::{tab-item} LaTeX
```latex
Ni pomembno, če za besedo
stoji en ali pa več           presledkov.
Prelom vrstice brez praznih 
  se obravnava kot presledek.


Prazna vrstica začenja nov odstavek. 
%
Prazen komentar ni prazna vrstica.

```
::::

::::{tab-item} PDF
:::{figure} ./img/01_presledki.png
:name: presledki
:alt: Izpis besedila, ki prikazuje, kako LaTeX obravnava presledke in prazne vrstice.
:::
::::
:::::
::::::

:::{admonition} Nasvet!
:class: tip
Ker se nova vrstica v LaTeXu obravnava kot presledek, razen če je prazna, je dobro, da vsak stavek napišete v eno vrstico.
To olajša urejanje besedila in sledenje spremembam v sistemih za nadzor različic, kot je Git.
:::

Včasih resnično potrebujemo prelom vrstice, ne da bi začeli nov odstavek. Za to imamo na voljo naslednje ukaze.

- Ukaz `\\` ustvari prelom vrstice. Z neobveznim argumentom lahko za njim dodamo še navpični presledek, npr. `\\[5mm]`.
- Ukaz `\newline` naredi isto kot `\\`, vendar ga lahko uporabimo samo v običajnem besedilu. Ukaz `\\` deluje tudi v tabelah in matematičnih okoljih, zato ga bomo uporabljali veliko pogosteje.
- Ukaz `\linebreak[arg]` prav tako prelomi vrstico, vendar besedilo pred prelomom raztegne čez vso širino vrstice, zato je rezultat pogosto grd. Argument `arg` je število od 0 do 4 (privzeto 4) in pove, kako močno si prelom želimo: pri 0 je prelom nizke prioritete in ga LaTeX lahko prezre, pri 4 pa je prioriteta najvišja.
- Ukaz `\noindent` prepreči zamik prve vrstice novega odstavka.

::::::{prf:example}
:label: latexUvod_eg-newline
:::::{tab-set}
::::{tab-item} LaTeX
```latex
\noindent Živé naj vsi naródi,\\
ki hrepené dočakat' dan,\newline
da koder sonce hodi,\\
prepir iz svéta bo pregnan,\newline
da rojak\\
prost bo vsak,\\
ne vrag, le sosed bo mejak!

```
::::

::::{tab-item} PDF
:::{figure} ./img/01_zdravljica.png
:width: 300px
:name: zdravljica
:alt: Pesem, prelomljena z ukazoma \\ in \newline.
:::
::::
:::::
::::::

LaTeX ima tudi ukaze za obravnavanje prelomov strani.

- Ukaz `\pagebreak[arg]` prelomi stran na mestu, kjer se pojavi, vendar vsebino navpično raztegne, da zapolni ves list. Argument `arg` deluje enako kot pri `\linebreak`.
- Ukaz `\newpage` prav tako začne novo stran, vendar preostali prostor na strani pusti prazen.
- Ukaz `\clearpage` deluje podobno kot `\newpage`, poleg tega pa izpiše še vse plavajoče elemente (npr. slike in tabele), ki še niso bili izpisani.
- Ukaz `\cleardoublepage` deluje podobno kot `\clearpage`, vendar zagotovi, da se nova stran v dvostranskem tisku začne na desni strani.

(latex_prelomStrani)=
:::{admonition} Nevarnost!
:class: danger
Ukazi za prelome vrstic in strani so namenjeni izjemno specifičnim okoliščinam, zato jih praviloma **ne uporabljamo**.

Ne pozabite, da moramo [oblikovanje dokumenta prepustiti LaTeXu](#latex_filozofija).
:::


(latexUvod_pisave)=
## Pisave in velikosti pisave

LaTeX privzeto uporablja pisavo _Computer Modern_, ki jo je zasnoval Donald Knuth.
Sodobne različice LaTeXa pogosto uporabljajo pisavo _Latin Modern_, ki je razširjena različica pisave Computer Modern.
Če ta pisava ni privzeto naložena, jo lahko (in jo tudi morate) naložiti z ukazom `\usepackage{lmodern}` v preambuli.

LaTeX samodejno izbere pisavo in velikost črk glede na razred dokumenta in izbrane pakete.
Pisavo v LaTeXu opisujejo štirje parametri:

family (družina)
: Dejanska pisava, ki jo uporabljamo. Privzeto ima LaTeX tri družine: _roman_ oz. _pokončna serifna_ pisava (`\textrm`), _sans serif_ oz. _gladka_ pisava (`\textsf`) in _strojepisna_ oz. _enakoprostorna_ pisava (`\texttt`).

series (serija)
: Debelina pisave. Privzeto ima LaTeX dve seriji: _medium_ oz. _srednja_ pisava (`\textmd`) in _bold face_ oz. _krepka_ pisava (`\textbf`).

shape (oblika)
: Naklon pisave. Privzeto ima LaTeX tri oblike: _italic_ oz. _ležeča_ pisava (`\textit`), _slanted_ oz. _poševna_ pisava (`\textsl`) in _small caps_ oz. _male velike črke_ (`\textsc`).
Poleg tega sta na voljo še dve navidezni obliki: _pokončna_ (`\textup`) in _velike in male črke_ (`\textulc`).
To v resnici nista obliki, ampak uporabniška ukaza: prvi preklopi nazaj na pokončno pisavo, drugi pa onemogoči male velike črke.
Ukaz `\textnormal` je le kombinacija obeh.

size (velikost)
: To se večinoma nadzira z možnostmi ukaza `\documentclass`, vendar o tem več kasneje.

Če želite spremeniti enega od prvih treh parametrov v danem besedilu, preprosto uporabite ukaze, kot je `\ukaz{dano besedilo}`. Npr. z ukazom `\textbf{To je krepko besedilo}` dobimo [**To je krepko besedilo**]{.latex-line} in z ukazom `\textit{To je ležeče besedilo}` dobimo [*To je ležeče besedilo*]{.latex-line}.

:::{admonition} Pazite!
:class: warning
Zgoraj prikazane ukaze lahko tudi združujemo, npr. `\textit{\textbf{To je krepko in ležeče besedilo}}` da [**_To je krepko in ležeče besedilo_**]{.latex-line}.
Vendar niso vse kombinacije na voljo: če poskusite uporabiti kombinacijo, ki ne obstaja, se bo LaTeX pritožil.
:::

Vsi zgornji ukazi imajo tudi različico _switch_. Ta besedila ne prejme prek argumenta, ampak spremeni pisavo od mesta uporabe naprej, in sicer do konca skupine `{...}` ali okolja, v katerem jo uporabimo. V [Tabeli %s](#tab-pisave) so prikazani vsi ukazi in njihove različice _switch_.

::::::{prf:example}
:label: latexUvod_eg-switch
:::::{tab-set}
::::{tab-item} LaTeX
```latex
Ukazi, kot je \texttt{\textbackslash textit\{argument\}},
vplivajo samo na \textit{argument}.
Če uporabimo različico switch, se vse,
kar je za ukazom \texttt{\textbackslash itshape},
\itshape spremeni in ostane tako,
dokler ne uporabimo ukaza \texttt{\textbackslash upshape}.
\upshape Zdaj je vse tako, kot je bilo prej.
```
::::

::::{tab-item} PDF
:::{figure} ./img/01_eg-switch.png
:name: eg-switch
:alt: Primer, ki prikazuje razliko med ukazom z argumentom in različico switch.
:::
::::
:::::
::::::


:::::{tab-set}
::::{tab-item} Pisave
:::{list-table} Pisave v LaTeXu
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
* - ležeča pisava
  - `\textit{<besedilo>}`
  - `\itshape`
* - poševna pisava
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
:::
::::
::::{tab-item} LaTeX
:::{figure} ./img/01_tab-pisave.png
:name: pisave
:alt: Tabela pisav v LaTeXu, prevedena v dokument PDF.
:::
::::
:::::

Poleg zgoraj navedenih ukazov lahko ustvarimo tudi podčrtano besedilo (`\underline{besedilo}`) in poudarjeno besedilo (`\emph`).
Delovanje ukaza `\emph{besedilo}` je odvisno od konteksta. Običajno da podoben rezultat kot ukaz `\textit`, vendar ni namenjen pisanju ležeče pisave, ampak **poudarjanju**: če je besedilo že ležeče, ga `\emph` postavi pokončno. Za primer poglejte {prf:ref}`latexUvod_eg-emph`.

::::::{prf:example}
:label: latexUvod_eg-emph
:::::{tab-set}
::::{tab-item} LaTeX
```latex
To je \underline{podčrtano} besedilo. 
Videti je \underline{malo} \underline{grdo},
zato ga ne uporabljajmo pogosto.

To je \emph{poudarjeno} besedilo.

\textit{To je ležeče besedilo, v 
katerem je \emph{poudarjeno} besedilo.}

\emph{To \emph{poudarjeno besedilo}
je obdano s poudarjenim besedilom \dots
ali je \emph{res} poudarjeno?}
```
::::

::::{tab-item} PDF
:::{figure} ./img/01_eg-emph.png
:name: eg-emph
:alt: Primer, ki prikazuje obnašanje ukazov \underline in \emph.
:::
::::
:::::
::::::

::::{exercise}
:label: ex_pisave
Uporabite različne pisave, da reproducirajte naslednje besedilo. 
Delajte s besedilom v res majhnih delih.

:::{figure} ./img/01_ex-pisave.png
:name: latexUvod-ex-pisave
:alt: Besedilo, ki ga je treba reproducirati z različnimi pisavami.
:::
::::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::

:::{solution} ex_pisave
:class: tip dropdown
Možna rešitev je:
```latex
Praviloma pisave izbiramo premišljeno, ali pa izbor kar prepustimo LaTeXu.
Besedilo lahko \emph{poudarimo} ali zapišemo \textbf{krepko}, ali pa \emph{\textbf{oboje skupaj}}.
Kaj se zgodi, če \emph{uporabimo poudarjeno \emph{znotraj} poudarjenega besedila}?
Seveda \textbf{lahko nastavimo tudi \textnormal{običajno} pisavo}.
Besedilo lahko tudi \underline{podčrtamo}, vendar tega ne priporočamo, \underline{ker} \underline{je grdo}.

Pišemo lahko tudi v \textsf{sans-serifni pisavi} ali pa \textsc{z malimi velikimi črkami},
denimo \textsc{SageMath}. 
\textit{Ležeča pisava} ni ista reč kot \textsl{poševna pisava}.
Ležeča pisava uporablja \textit{drugačne glife},
poševna pisava pa \textsl{iste glife}, le nagnjene.
Razlika je res očitna, če pogledate
\textit{ležečo črko a} poleg \textsl{poševne črke a}.

Včasih uporabimo tudi \texttt{pisavo fiksne širine}, 
v kateri so vsi znaki enako široki.
```
:::
Za razliko od večine urejevalnikov besedil WYSIWYG (Word itd.) LaTeX nima izrecnega načina za določanje velikosti pisave.
Dejanska velikost besedila je odvisna od možnosti argumenta `\documentclass` (`10pt`, `11pt` ali `12pt`).
To pomeni, da bo navadno besedilo velikosti `10pt` (oz. `11pt` ali `12pt`).
Velikost pisave za druge dele besedila bo določena ustrezno.

Če resnično želimo spremeniti velikost pisave za določen del besedila, uporabimo ukaze v [Tabeli %s](#tab-velikostiPisave).
Natančneje, ti ukazi so _deklaracije_: besedila ne prejmejo prek argumenta, ampak veljajo od mesta uporabe do konca skupine ali okolja.
Zaradi tega je njihova sintaksa nekoliko drugačna.
Delujejo kot `{\velikost <besedilo>}`, kjer je `velikost` eden od ukazov iz tabele, `besedilo` pa besedilo, ki ga želimo spremeniti.
Npr. z ukazom `{\Huge To je največje besedilo, ki ga lahko ustvari LaTeX.}` dobimo stavek:

:::{div}
:class: latex-block Huge
To je največje besedilo, ki ga lahko ustvari LaTeX.
:::

V [Tabeli %s](#tab-velikostiPisave) podajamo dejansko velikost za vsako od njih ter relativno primerjavo med različnimi velikostmi.

:::::{tab-set}
::::{tab-item} Velikosti pisave
:::{list-table} Velikosti pisave v LaTeXu
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
  - 14,4 pt
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
:::
::::
::::{tab-item} LaTeX
:::{figure} ./img/01_tab-velikostiPisave.png
:name: velikostiPisave 
:alt: Velikosti pisave v LaTeXu
Velikosti pisave v LaTeXu
:::
::::
:::::

Mnoge od teh ukazov imajo svojo sodobno različico v obliki okolja. Namesto da napišete `{\small majhna pisava}`, lahko na primer napišete `\begin{small} majna pisava \end{small}`.

::::{exercise}
:label: ex_VelikostiPisave
Uporabite različne velikosti pisave in pisave, da reproducirajte naslednje besedilo.

:::{figure} /img/01_ex-velikostiPisave.png
:name: latexUvod-ex-VelikostiPisave
:alt: Različne pisave v LaTeXu
:::

::::

:::{margin}
[Seznam vaj](#latexUvod_vaje)
:::
::::{solution} ex_VelikostiPisave
:class: tip dropdown
Ste goljufali in pogledali rešitev?
:::{admonition} Opozorilo!
:class: warning
V resnici ni potrebno, da natančno sledite velikostim pisave.
Preveč igranja s pisavami in velikostmi pisav je v nasprotju s [filozofijo LaTeXa](#latex_filozofija). 
:::

Če ste resnično radovedni, tukaj je možna rešitev:


```latex
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


Vsako poglavje v tej knjigi se konča s seznamom vaj ter dodatnimi ali domačimi nalogami. Tukaj so vaje prvega poglavja:

- [ ] [Vaja %s](#ex-overleafRacun): Ustvarjanje računa v Overleafu.
- [ ] [Vaja %s](#ex_latex_prvaDatoteka): Ustvarjanje prve datoteke LaTeX.
- [ ] [Vaja %s](#ex_latex_avtorNaslovDatum): Dodajanje avtorja, naslova in datuma.
- [ ] [Vaja %s](#ex_latex_babel): Uporaba paketa `babel`.
- [ ] [Vaja %s](#ex_latex_komentarji): Znak `%` in komentarji.
- [ ] [Vaja %s](#ex_latex_posebniZnaki): Uporaba posebnih znakov.
- [ ] [Vaja %s](#ex_VezajiPomisljajiNarekovaji): Uporaba vezajev, pomišljajev in narekovajev.
- [ ] [Vaja %s](#ex_pisave): Uporaba različnih pisav.
- [ ] [Vaja %s](#ex_VelikostiPisave): Uporaba različnih velikosti pisav.


:::{exercise} Domača naloga
:nonumber:
1. Napišite novo datoteko z imenom `DN1.tex`.
1. Z njo ustvarite dokument z naslovom _Poučevanje slovenščine mojega učitelja_.
1. Dodajte svoje ime kot avtorja in današnji datum.
1. Ne pozabite uporabiti paketa `babel` z možnostjo `slovene`.
1. V dokumentu mi opišite svoj dan ali napišite kratko otroško zgodbo, ali pa mi povejte zabavno anekdoto, izbira je vaša! Pomembno je, da vadite pisanje v LaTeXu, jaz pa bom vadil branje slovenskega jezika.
1. Uporabite različne pisave in velikosti pisav, da bo vaše besedilo bolj zanimivo (ampak ne preveč!).
1. Domačo nalogo oddajte kot datoteko `.zip` prek spletne učilnice. Če ne veste, kako pridobiti datoteko `.zip` iz Overleafa, poglejte [](./B_izvozIzOverleaf.md).
:::


