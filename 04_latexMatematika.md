---
numbering: false
---

(04_latexMatematika1)=

# Matematika v LaTeXu

LaTeX je še posebej primeren za pisanje matematičnih izrazov in ena izmed njegovih glavnih prednosti je prav podpora za matematične simbole in formule.
LaTeX je že sam po sebi zelo zmogljiv. Vendar pa obstaja tudi veliko paketov, ki še dodatno razširijo njegove zmogljivosti na področju matematike.

Standardni paket za matematiko so:

- `amsmath`: paket, ki ga je razvila Ameriška matematična družba (American Mathematical Society) in ponuja številne izboljšave za pisanje matematičnih izrazov.
- `amssymb`: paket, ki ponuja dodatne matematične simbole.
- `amsfonts`: paket, ki omogoča uporabo dodatnih matematičnih pisav.
- `amsthm`: paket za definiranje in oblikovanje matematičnih izrekov, trditve, definicij itd.

Ti paketi so pogosto vključeni v predloge dokumentov, vendar jih je mogoče vključiti tudi ročno z ukazom `\usepackage{amsmath, amssymb, amsfonts, amsthm}` v preambuli vašega LaTeX dokumenta.

V sodoben LaTeX dokument je priporočljivo vključiti paket `mathtools`, ki je razširitev paketa `amsmath` in ponuja dodatne funkcije in izboljšave za pisanje matematičnih izrazov.

:::{admonition} Pomembno!
:class: important
V tem poglavju bomo predpostavljali, da so ti paketi že vključeni v vaš dokument. Lahko jih vključite z naslednjim ukazom v preambuli vašega LaTeX dokumenta:

```latex
\usepackage{mathtools}  % mathtools vključuje tudi amsmath
\usepackage{amssymb, amsfonts, amsthm}
```

:::

## Osnovni matematični izrazi

LaTeX omogoča pisanje matematičnih izrazov na dva načina: znotraj besedila (_vrstični način_; ang. _inline mode_ ) in v ločenih vrsticah (_prikazen način_; ang. _display mode_).

Matematika v vrstičnem načinu se vstavlja z uporabo znakov `$...$` ali `\(...\)`. Na primer, izraz za Pitagorov izrek lahko zapišemo kot `$a^2 + b^2 = c^2$` (ali `\(a^2 + b^2 = c^2\)`), ki je natisnjen kot $a^2 + b^2 = c^2$.

Za prikaz matematičnih izrazov v ločenih vrsticah (in osredotočeno poravnano) se uporabljajo znaki `\[...\]` ali okolje `equation*` (sta enakomerna). Na primer, če je $ax^2 + bx +c = c$ kvadratna enačba, potem je rešitev te enačbe:

```latex
\[x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2} \]
```

kar je natisnjeno kot

$$
x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2}.
$$

Ta izraz v vrstičnem načinu bi bil zapisan kot `$x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2}$`, kar je natisnjeno kot $x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2}$.

:::{admonition} Opomba
:class: note
Matematika v vrstičnem načinu zapisana z `$...$` včasih se šteje za zastarelo. Priporočljivo je uporabljati `\(...\)`. Vendar, v praksi večinoma avtorjev uporabijo `$...$`, ker je hitreje za tipkanje in dobi se enak rezultat.

Podobno je tudi pri prikaznem načinu, kjer je priporočljivo uporabljati `\[...\]` (ali okolja `equation*`) namesto `$$ ... $$`s. Vendar je `$$...$$` resnično zastarelo in **se ne sme uporabljati**.
:::

Matematične izraze v prikaznem načinu je mogoče tudi oštevilčiti z uporabo okolja `equation` (brez zvezdice). Rezultat je podoben kot zgoraj, vendar bo enačba oštevilčena. Seveda, lahko sklicujemo na to enačbo v besedilu z uporabo ukazov `\label{<oznaka>}` in `\ref{<oznaka>}`:

::::::{prf:example}
:label: eg_matematika_equation_1

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{equation}
\label{eq:kvadratna_formula}
x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{equation}
V enačbi \ref{eq:kvadratna_formula} je prikazana kvadratna formula.
```
````
````{tab-item} PDF
```{figure} ./img/04_eg-matematika-equation-1.png
:label: fig:eg-math-equation-1
:width: 100%
```
````
`````

::::::

Za enačbe lahko tudi uporabimo ukaze `\eqref{<oznaka>}` in `\tag{<opis>}`, ki omogočata bolj prilagojeno sklicevanje in označevanje enačb:

::::::{prf:example}
:label: eg_matematika_equation_2

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{equation}
\label{eq:kvadratna_formula}
x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{equation}
V enačbi \eqref{eq:kvadratna_formula} je prikazana kvadratna formula.
```
````
````{tab-item} PDF
```{figure} ./img/04_eg-matematika-equation-2.png
:label: fig:eg-math-equation-2
:width: 100%
```
````
`````

::::::

::::::{prf:example}
:label: eg_matematika_equation_3

`````{tab-set}
````{tab-item} LaTeX
```latex
\begin{equation}
\label{eq:kvadratna_formula}
\tag{Kvadratna formula}
x_{1,2} = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{equation}
V enačbi \eqref{eq:kvadratna_formula} je prikazana kvadratna formula.
```
````
````{tab-item} PDF
```{figure} ./img/04_eg-matematika-equation-3.png
:label: fig:eg-math-equation-3
:width: 100%
```
````
`````
::::::

Ukazi in okolja za pisanje matematičnih aktivirajo matematični način, kjer so nekateri znaki in ukazi drugačni kot v običajnem besedilnem načinu. Na primer, presledki v matematičnem načinu nimajo pomena, medtem ko so v besedilnem načinu pomembni:

::::{grid} 2 2 2 2
:::{card} LaTeX
```latex
$123xyz$ je enako kot \(1 2 3 x y z \)
```
:::
:::{card} PDF

```{figure} ./img/04_eg-math-mode-1.png
:label: fig:eg-math-mode-1
:width: 80%
```
:::
::::

Vse črke so v matematičnem načinu obravnavane kot spremenljivke in so zato natisnjene v poševni pisavi (italics). Razmik med črkami je večji kot v običajnem besedilu.

:::::{grid} 2 2 2 2
::::{card} LaTeX
```latex
Primerjaj besedo \textit{office}
z besedo $office$.
```
::::

::::{card} PDF
```{figure} ./img/04_eg-math-mode-2.png
:label: fig:eg-math-mode-2
:width: 110%
```
::::
:::::

Zaradi zgoraj navedenih razlogov moramo matematično besedilo **vedno** zapisovati v matematičnem načinu (v vrstici ali prikazano).

`````{tab-set}
````{tab-item} LaTeX
```latex
  V \LaTeX u moramo matematični del besedila zapisati v matematičnem načinu.
  Tudi če je to nekaj tako preprostega kot ta številka $2$
  ali ta spremenljivka $x$.
```
````
````{tab-item} PDF
``` {figure} ./img/04_eg-math-mode-3.png
:label: fig-math-mode-3
```
````
`````

Če želimo v matematičnem načinu uporabiti običajno besedilo, lahko uporabimo ukaz `\text{...}`: why?

:::::{grid} 2 2 2 2

::::{card} LaTeX
```latex
\[2+\text{enka}=3\]
```
::::

::::{card} PDF
$$
 2+\text{enka}=3
$$
::::
:::::

## Stavljenje matematičnih formul

Možnosti za matematične simbole je ogromno, zato bomo prikazali le nekaj
primerov.
Seznam primerov tukaj je namenjen prikazu nekaterih najpogostejših primerov uporabe, vendar nikakor ni izčrpen.

Pri sestavljanju matematičnih formul vam bodo morda v pomoč naslednji viri.

- [Comprehensive LaTeX Symbol List](https://tug.ctan.org/info/symbols/comprehensive/symbols-a4.pdf): Obsežen seznam LaTeX simbolov, ki vključuje simbole iz različnih paketov **Skoraj 500 strani**.
- [Detexify](http://detexify.kirelabs.org/classify.html): Orodje, ki vam omogoča, da narišete simbol, ki ga iščete, in orodje vam bo predlagalo ustrezne LaTeX ukaze za ta simbol.
- [Seznam osnovnih matematičnih simbolov](./img/04_seznamSimbolov.pdf){target="\_blank"}: Kratek seznam pogosto uporabljenih LaTeX matematičnih simbolov.

:::::{dropdown} Osnovni aritmetični izrazi

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[a^{2}+b^{2} = c^{2}\]
```
:::

:::{card} PDF

$$
a^{2}+b^{2} = c^{2}
$$
:::

:::{card} LaTeX

```latex
\[A_x = B_{foo} \neq B_foo\]
```
:::
:::{card} PDF

$$
A_x = B_{foo} \neq B_foo
$$
:::
:::{card} LaTeX

```latex
\[(4 \times 6) \div 3 = 8\]
```
:::
:::{card} PDF

$$
(4 \times 6) \div 3 = 8
$$
:::
:::{card} LaTeX

```latex
\[(5 \cdot 3) / 2 \not = 7\]
```
:::
:::{card} PDF

$$
(5 \cdot 3) / 2 \not = 7
$$
:::
:::{card} LaTeX

```latex
\[1 \leq 2 \text{ vs.} 1 \leqslant 2\]
```
:::
:::{card} PDF

$$
1 \leq 2 \text{ vs.} 1 \leqslant 2
$$
:::
:::{card} LaTeX

```latex
\[\sqrt{a} \cdot \sqrt{b} = \sqrt{ab}\]
```
:::
:::{card} PDF

$$
\sqrt{a} \cdot \sqrt{b} = \sqrt{ab}
$$
:::
:::{card} LaTeX

```latex
\[a = \sqrt[7]{b^7 + c^7}\]
```
:::
:::{card} PDF

$$
a = \sqrt[7]{b^7 + c^7}
$$
:::
:::{card} LaTeX

```latex
$3 + \frac{a+c}{b+d}$
```
:::
:::{card} PDF

$3 + \frac{a+c}{b+d}$
:::
:::{card} LaTeX

```latex
\[3 + \frac{a+c}{b+d}\]
```
:::
:::{card} PDF

$$
3 + \frac{a+c}{b+d}
$$
:::

::::
:::::

:::::{dropdown} Logika in množice

::::{grid} 2 2 2 2
:::{card} LaTeX
```latex
\[
p \land q \iff
\lnot ( p \implies \lnot q )
\]
```
:::
:::{card} PDF

$$
p \land q \iff
  \lnot ( p \implies \lnot q )
$$
:::
:::{card} LaTeX

```latex
\[ \lnot \forall q P(q) \iff \exists q \lnot P(q)\]
```
:::
:::{card} PDF

$$
\lnot \forall q P(q) \iff \exists q \lnot P(q)
$$
:::
:::{card} LaTeX

```latex
\[\{1, 2, 3, \ldots, 100 \}]
```
:::
:::{card} PDF

$$
\{1, 2, 3, \ldots, 100\}
$$
:::

:::{card} LaTeX

```latex
\[ \{x \in X \colon\ \exists y \ x^2+y^2 = 1 \} \]
```
:::
:::{card} PDF

$$
\{x \in X \colon\ \exists y \ x^2+y^2 = 1 \}
$$
:::

:::{card} LaTeX

```latex
\[ \emptyset \subset X \cap Y \]
```
:::
:::{card} PDF

$$
\emptyset \subset X \cap Y
$$
:::
:::{card} LaTeX

```latex
\[ X \subseteq (X \cup Y) \setminus Y \]
```
:::
:::{card} PDF

$$
X \subseteq (X \cup Y) \setminus Y
$$
:::

::::
:::::

:::::{dropdown} Grške črke

Mali grške črke se v LaTeXu vpišejo z uporabo ukaza `\ime_črka` (npr. `\alpha`, `\beta`, `\gamma`, ...), medtem ko se velike grške črke vpišejo z uporabo ukaza `\Ime_črka` (npr.`\Gamma`, ...). Vendar pa je treba opozoriti, da nekatere velike grške črke nimajo posebnega ukaza in se v LaTeXu pišejo enako kot njihove latinske ustreznice (npr. `A`, `B`, `E`, ...).
Nekaj malih grških črk ima tudi variante, ki se v LaTeXu vpišejo z uporabo ukaza `\varIme_črka` (npr. `\varepsilon`, `\vartheta`, ...):

::::{list-table} Mali grške črke
:header-rows: 1
* - LaTeX
  - PDF
  - LaTeX
  - PDF
  - LaTeX
  - PDF
  - LaTeX
  - PDF
* - `\alpha`
  - $\alpha$
  - `\beta`
  - $\beta$
  - `\gamma`
  - $\gamma$
  - `\delta`
  - $\delta$
* - `\epsilon`
  - $\epsilon$
  - `\zeta`
  - $\zeta$
  - `\eta`
  - $\eta$
  - `\theta`
  - $\theta$
* - `iota`
  - $\iota$
  - `\kappa`
  - $\kappa$
  - `\lambda`
  - $\lambda$
  - `\mu`
  - $\mu$
* - `\nu`
  - $\nu$
  - `\xi`
  - $\xi$
  - `\pi`
  - $\pi$
  - `\rho`
  - $\rho$
* - `\sigma`
  - $\sigma$
  - `\tau`
  - $\tau$
  - `\upsilon`
  - $\upsilon$
  - `\phi`
  - $\phi$
* - `\chi`
  - $\chi$
  - `\psi`
  - $\psi$
  - `\omega`
  - $\omega$
  -
  -
* - `varepsilon`
  - $\varepsilon$
  - `vartheta`
  - $\vartheta$
  - `\varkappa`
  - $\varkappa$
  - `\varpi`
  - $\varpi$
* - `\varrho`
  - $\varrho$
  - `\varsigma`
  - $\varsigma$
  - `\varphi`
  - $\varphi$
  -
  - 
::::

Nekaj velikih grških črk ima variante, ki se v LaTeXu vpišejo z uporabo ukaza `\varIme_črka` (npr. `\varTheta`, `\varGamma`, ...):

::::{list-table} Variante velikih grških črk
:header-rows: 1

* - LaTeX
  - PDF
  - LaTeX
  - PDF
  - LaTeX
  - PDF
  - LaTeX
  - PDF
* - `\varTheta`
  - $\varTheta$
  - `\varGamma`
  - $\varGamma$
  - `\varDelta`
  - $\varDelta$
  - `\varLambda`
  - $\varLambda$
* - `\varXi`
  - $\varXi$
  - `\varPi`
  - $\varPi$
  - `\varSigma`
  - $\varSigma$
  - `\varUpsilon`
  - $\varUpsilon$
* - `\varPhi`
  - $\varPhi$
  - `\varPsi`
  - $\varPsi$
  - `\varOmega`
  - $\varOmega$
  -
  - 
::::
:::::

:::::{dropdown} Operatorji in funkcije
Določene funkcije in operatorji morajo biti zapizani v rimski pisavi (upravičeno) (prim. $sin(x)$ in $\sin(x)$). Običajno, se to doseže z uporabo ukaza `\ime_funkcije` (npr. `\sin`, `\cos`, `\log`, ...). Tabela spodaj prikazuje funkcije in operatorje, ki so na voljo v LaTeXu:

::::{list-table} Operatorji in funkcije
:header-rows: 1
:label: tab:latex_operators

* - LaTeX
  - PDF
  - LaTeX
  - PDF
  - LaTeX
  - PDF
  - LaTeX
  - PDF
* - `\arcos`
  - $\arccos$
  - `\arcsin`
  - $\arcsin$
  - `\arctan`
  - $\arctan$
  - `\arg`
  - $\arg$
* - `\cos`
  - $\cos$
  - `\cosh`
  - $\cosh$
  - `\cot`
  - $\cot$
  - `\coth`
  - $\coth$
* - `\csc`
  - $\csc$
  - `\deg`
  - $\deg$
  - `\det`
  - $\det$
  - `\dim`
  - $\dim$
* - `\exp`
  - $\exp$
  - `\gcd`
  - $\gcd$
  - `\hom`
  - $\hom$
  - `\inf`
  - $\inf$
* - `\ker`
  - $\ker$
  - `\lg`
  - $\lg$
  - `\lim`
  - $\lim$
  - `\liminf`
  - $\liminf$
* - `\limsup`
  - $\limsup$
  - `\log`
  - $\log$
  - `\ln$`
  - $\ln$
  - `\max`
  - $\max$
* - `\min`
  - $\min$
  - `\Pr`
  - $\Pr$
  - `\sec`
  - $\sec$
  - `\sin`
  - $\sin$
* - `\sinh`
  - $\sinh$
  - `\sup`
  - $\sup$
  - `\tan`
  - $\tan$
  - `\tanh`
  - $\tanh$
::::

Če želimo napisati operatorje, ki niso vključeni v zgornjo tabelo, lahko uporabimo ukaz `\operatorname{ime_operatorja}`. Na primer, za pisanje operatorja "foo" bi uporabili ukaz `\operatorname{foo}`, kar bi dalo rezultat $\operatorname{foo}$.

Vendar, če pogosto uporabljamo določen operator, je priporočljivo definirati nov operator z uporabo ukaza `\DeclareMathOperator{\ime_operatorja}{opis_operatorja}` v preambuli dokumenta. Na primer, za definiranje operatorja "foo" bi dodali naslednjo vrstico v preambulo:

```latex
\DeclareMathOperator{\foo}{foo}
```

Nato lahko uporabimo ukaz `\foo` v matematičnem načinu, kar bo dalo rezultat $\operatorname{foo}$.
:::::

:::::{dropdown} Veliki operatorji
Nekateri matematični operaterji se štejejo za »velike« operaterje. Ti operatorji so običajno uporabljeni v prikaznem načinu in imajo večje simbole, medtem ko so v vrstičnem načinu manjši. Veliki operatorji vključujejo vsote, produkte, integrale, itd.
Nekatere funkcije v [Tabeli %s](#tab_latex-operators) so tudi veliki operatorji.

::::{list-table} Veliki operatorji
:header-rows: 1
:label: tab_latex-operators

* - LaTeX
  - PDF (prikazni način)
  - PDF (vrstični način)
* - `\sum_{i=1}^{n} i`
  - $\displaystyle \sum_{i=1}^{n} i$
  - $\sum_{i=1}^{n} i$
* - `\prod_{i=1}^{n} i`
  - $\displaystyle \prod_{i=1}^{n} i$
  - $\prod_{i=1}^{n} i$
* - `\int_{a}^{b} f(x) \, dx`
  - $\displaystyle \int_{a}^{b} f(x) \, dx$
  - $\int_{a}^{b} f(x) \, dx$
* - `\iint_{D} f(x,y) \, dA`
  - $\displaystyle \iint_{D} f(x,y) \, dA$
  - $\iint_{D} f(x,y) \, dA$
* - `\iiint_{E} f(x,y,z) \, dV`
  - $\displaystyle \iiint_{E} f(x,y,z) \, dV$
  - $\iiint_{E} f(x,y,z) \, dV$
* - `\oint_{C} f(z) \, dz`
  - $\displaystyle \oint_{C} f(z) \, dz$
  - $\oint_{C} f(z) \, dz$
* - `\bigcup_{i=1}^{n} A_i`
  - $\displaystyle \bigcup_{i=1}^{n} A_i$
  - $\bigcup_{i=1}^{n} A_i$
* - `\bigcap_{i=1}^{n} A_i`
  - $\displaystyle \bigcap_{i=1}^{n} A_i$
  - $\bigcap_{i=1}^{n} A_i$
* - `\lim_{x \to \infty} f(x)`
  - $\displaystyle \lim_{x \to \infty} f(x)$
  - $\lim_{x \to \infty} f(x)$
* - `\sup_{x \in A} f(x)`
  - $\displaystyle \sup_{x \in A} f(x)$
  - $\sup_{x \in A} f(x)$
* - `\inf_{x \in A} f(x)`
  - $\displaystyle \inf_{x \in A} f(x)$
  - $\inf_{x \in A} f(x)$
* - `\max_{x \in A} f(x)`
  - $\displaystyle \max_{x \in A} f(x)$
  - $\max_{x \in A} f(x)$
* - `\min_{x \in A} f(x)`
  - $\displaystyle \min_{x \in A} f(x)$
  - $\min_{x \in A} f(x)$
::::

Če želimo definirati nove velike operatorje, lahko uporabimo ukaz

```latex
\DeclareMathOperator*{\ime_operatorja}{opis_operatorja}
```

v preambuli dokumenta. Na primer, za definiranje velikega operatorja "Fun" bi dodali naslednjo vrstico v preambulo:

```latex
\DeclareMathOperator*{\Fun}{Fun}
```

Nato lahko uporabimo ukaz `\Fun` v matematičnem načinu, kar bo dalo različne rezultate v vrstičnem in prikaznem načinu.

:::::
:::::{dropdown} Matematične pisave
Standardni ukazi za uporabo različnih pisav, kot je, `\textbf{...}`, ne delujejo v matematičnem načinu. Namesto tega LaTeX ponuja posebne ukaze za različne matematične pisave:

::::{list-table} Matematične pisave
:header-rows: 1

* - LaTeX
  - PDF
* - `\mathrm{ABC xyz \Gamma \Delta \Lambda \alpha \beta \gamma}`
  - $\mathrm{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}$
* - `\mathit{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma }`
  - $\mathit{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}$
* - `\mathbf{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}`
  - $\mathbf{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}$
* - `\mathsf{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}`
  - $\mathsf{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}$
* - `\mathtt{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}`
  - $\mathtt{ABC xyz \Gamma \Delta \Lambda  \alpha \beta \gamma}$
* - `\mathcal{ABC}`
  - $\mathcal{ABC}$
* - `\mathbb{ABC}`
  - $\mathbb{ABC}$
* - `\mathfrak{ABCxyz}`
  - $\mathfrak{ABCxyz}$
::::

Nekatere vir (npr. [Standard ISO 80000-2](https://www.sist.si/velicine-in-enote-2-del-matematika-sist-en-iso-80000-220196-prevod-v-slovenscino.html)) priporočajo, da se za matematične konstante in posebne funkcije uporablja rimska pisava (upravičeno). Na primer, Eulerjevo število $e$, imaginarna enota $i$ in diferencialni operator $d$ naj bodo zapisani v rimski pisavi kot `\mathrm{e}`: $\mathrm{e}$, `\mathrm{i}`:$\mathrm{i}$ in `\mathrm{d}`: $\mathrm{d}$.
Ukaz `\mathrm{\pi}` bi uporabili za zapis števila pi v rimski pisavi: $\mathrm{\pi}$.

Seveda bi bilo preveč, če bi morali vsakič, ko želimo napisati znano konstanto, vpisati ukaz `\mathrm{\pi}`. Lahko pa opredelimo lasten ukaz, tako da v preambuli vstavimo ukaz `\NewDocumentCommand{\kpi}{}{\mathrm{\pi}}`, in nato uporabimo ukaz `\kpi` za pisanje števila pi v rimski pisavi. Poleg tega, ce se v nekem trenutku odločimo, da ne želimo, da se konstanta pi piše v rimski pisavi, lahko preprosto spremenimo ukaz `\kpi` v preambuli.

Ukaz `\mathbb{...}` se običajno uporablja za množice števil, kot so naravna števila $\mathbb{N}$, cela števila $\mathbb{Z}$, racionalna števila $\mathbb{Q}$, realna števila $\mathbb{R}$ in kompleksna števila $\mathbb{C}$.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[4 \in \mathbb{N}, -5 \in \mathbb{Z},\frac{1}{2} \in \mathbb{Q}, \sqrt{2} \in \mathbb{R}\]
```

:::

:::{card} PDF

$$
4 \in \mathbb{N}, -5 \in \mathbb{Z},\frac{1}{2} \in \mathbb{Q}, \sqrt{2} \in \mathbb{R}
$$

:::
::::

:::::

:::::{dropdown} Oklepaji in drugi ločevalniki
Poleg oklepajev `(`, `)`, oglatih oklepajev `[`, `]` in zavitih oklepajev `\{`, `\}`, LaTeX ponuja tudi druge vrste ločevalnikov, npr.:

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\langle x \rangle,
\lVert x \rVert,
\lfloor x \rfloor,
\lceil x \rceil,
\lvert x \rvert
\]
```

:::
:::{card} PDF

$$
\langle x \rangle,
\lVert x \rVert,
\lfloor x \rfloor,
\lceil x \rceil,
\lvert x \rvert
$$

:::
::::

Čeprav vsi delujejo dobro za preproste matematične izraze, se stvari zapletejo, ko izraz znotraj njih postane dolg.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
{\lfloor
\frac
{{\langle\sum_{k=1}^{\infty} k^{-4}\rangle}^3}
{\frac{{\lvert\{a,b,c\}\rvert}^8}{{(x^4)}^3}}
\rfloor}^6
\]
```

:::
:::{card} PDF

$$
{\lfloor
\frac
{{\langle\sum_{k=1}^{\infty} k^{-4}\rangle}^3}
{\frac{{\lvert\{a,b,c\}\rvert}^8}{{(x^4)}^3}}
\rfloor}^6
$$

:::
::::

V takih primerih je priporočljivo uporabiti ukaza `\left` in `\right`, ki samodejno prilagodita velikost ločevalnikov glede na vsebino znotraj njih. **Morate pa paziti**, da vsak `\left` ima ustrezen `\right`, ampak ni nujno, da sta oba ločevalnika enaka.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\left(
\frac{1}{1 +
  \frac{1}{1 +
    \frac{1}{1 +
      \frac{1}{1 +
        \sqrt{2}}}}}
\right]
\]
```

:::
:::{card} PDF

$$
\left(
\frac{1}{1 +
  \frac{1}{1 +
    \frac{1}{1 +
      \frac{1}{1 +
        \sqrt{2}}}}}
\right]
$$

:::
::::

Če želite uporabiti le enega od ločevalnikov, lahko uporabite `\left.` ali `\right.` za označevanje odsotnega ločevalnika.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
x = \left.
\sum_{k=1}^{\infty}
\frac{1}{k^2}
\right\}
\]
```

:::
:::{card} PDF

$$
x = \left.
\sum_{k=1}^{\infty}
\frac{1}{k^2}
\right\}
$$

:::
::::

Čeprav je včasih potrebno neposredno uporabiti ukaza `\left` in `\right`, je najpogostejši primer uporabe nekaterih vnaprej določenih ločil na obeh straneh. Za to uporabo je ukaz

```latex
\DeclarePairedDelimiter{\ime_ločivalnika}{levo_ločivalnik}{desno_ločivalnik}
```

v preambuli dokumenta. Nato lahko uporabimo ukaz `\ime_ločivalnika{...}` v matematičnem načinu, kar bo ustvarilo ločevalnike okoli vsebine znotraj `levo_ločivalnik` in `desno_ločivalnik`. Različica "z zvezdico" ta ukaza je enaka kot uporaba `\left` in `\right`, kar pomeni, da se velikost ločevalnikov samodejno prilagodi vsebini znotraj njih.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
%V preambuli:
\DeclarePairedDelimiter{\set}{\{}{\}}
\[
%...
% V telesu dokumenta:
\[
\mathbb{Q} = \set*{
\frac{a}{b} \colon\
a,b \in \mathbb{Z}, b \neq 0
}
\]
```

:::
:::{card} PDF

$$
\mathbb{Q} = \left\{
\frac{a}{b} \colon\
a,b \in \mathbb{Z}, b \neq 0
\right\}
$$

:::
::::

Včasih je potrebno prilagoditi velikost ločevalnikov ročno, ne glede na vsebino znotraj njih. V takih primerih lahko uporabimo ukaze `\big`, `\Big`, `\bigg` in `\Bigg` pred ločevalniki, da določimo njihovo velikost.
Te ukaze morate dodati pred `l` ali `r` (odvisno od tega, ali želite odpreti ali zapreti) in ločevalnika.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\Biggl(
\biggl(
\Bigl(
\bigl(
  \sqrt{2}
\bigr)
\Bigr)
\biggr)
\Biggr)
\]
```

:::

:::{card} PDF

$$
\Biggl(
\biggl(
\Bigl(
  \bigl(
    \sqrt{2}
  \bigr)
\Bigr)
\biggr)
\Biggr)
$$

:::
::::  
:::::

:::::{dropdown} Matematični akcenti
Za poudarjanje delov matematičnih izrazov lahko uporabimo različne ukaze za akcent:

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\bar{a},
\vec{v},
\hat{n},
\dot{x},
\ddot{y}
\]
```

:::
:::{card} PDF

$$
\bar{a},
\vec{v},
\hat{n},
\dot{x},
\ddot{y}
$$

::::

Nekateri akcenti obstajajo tudi v _široki_ različici.
Ti lahko zajemajo več kot en znak.
Primerjajte `\hat` z `\widehat` v primeru spodaj.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\hat{ABC},
\widehat{ABC}
\]
```

:::
:::{card} PDF

$$
\hat{ABC},
\widehat{ABC}
$$

:::
::::

Široka verzija obstaja tudi za `\bar` in `\vec`, ki se imenujeta `\overline` in `\overrightarrow`.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\frac{9}{14} = 0,6\overline{428571},
\vec{AB},
\overrightarrow{AB}
\]
```

:::
:::{card} PDF

$$
\frac{9}{14} = 0,6\overline{428571},
\vec{AB},
\overrightarrow{AB}
$$

:::
::::

Nekateri akcenti celo sprejemajo omejitve:

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\underbrace{
\overbrace{(3!)}^6
\times
\overbrace{(2^3 - 1)}^7
}_{\text{odgovor na vprašanje o vsem}}=42
\]
```

:::

:::{card} PDF

$$
\underbrace{
\overbrace{(3!)}^6
\times
\overbrace{(2^3 - 1)}^7
}_{\text{odgovor na vprašanje o vsem}}=42
$$

:::
::::

Lahko celo ustvarite svoje matematični akcenti z uporabo ukazov `\overset` in `\underset`.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\overset{\heartsuit}{x},
\underset{\rightarrow}{A}
\]
```

:::

:::{card} PDF

$$
\overset{\heartsuit}{x},
\underset{\rightarrow}{A}
$$

:::
::::

:::::

:::::{dropdown} Matrike in navpično poravnana matematika

Za pisanje matrik in drugih navpično poravnanih matematičnih izrazov lahko uporabimo okolje `array`.
Ta okolje deluje podobno kot okolje `tabular`, vendar je namenjeno za uporabo v matematičnem načinu.
Okolje tabular, skupaj z ločilniki, lahko uporabimo za ustvarjanje matrik z različnimi vrstami oklepajev okoli njih:

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\left(
\begin{array}{ccc}
a & b & c \\
d & e & f \\
g & h & i
\end{array}
\right)
\]
```

:::

:::{card} PDF

$$
\left(
\begin{array}{ccc}
a & b & c \\
d & e & f \\
g & h & i
\end{array}
\right)
$$

:::
::::

Za ustvarjanje matematičnih izrazov, opredeljenih s primeri, lahko uporabimo okolje `array`.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
y= \left\{
\begin{array}{ll}
y=
\left\{
\begin{array}{ll}
a & \text{če }d>c\\
b+x & \text{zjutraj}\\
l & \textrm{čez cel dan}
\end{array}
\right.
\]
```

:::

:::{card} PDF

$$
y=
\left\{
\begin{array}{ll}
a & \text{če }d>c\\
b+x & \text{zjutraj}\\
l & \textrm{čez cel dan}
\end{array}
\right.
$$

:::
::::

Okolje `array` je nekoliko zastarelo in razmik ni pravilno v primerjavi z drugimi matematičnimi objekti. Paket `amsmath` ponuja sodobna okolja, ki dosegajo enake funkcionalnosti.

The okolje `matrix` omogoča ustvarjanje matrik brez oklepajev in je naravni nadomestek za okolje `array`. Upoštevajte, da okolje `matrix` ne sprejema specifikacije stolpcev. Največje število stolpcev za okolje `matrix` je 10.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\left(
\begin{matrix}
a & b & c \\
d & e & f \\
g & h & i
\end{matrix}
\right)
\]
```

:::

:::{card} PDF

$$
\left(
\begin{matrix}
a & b & c \\
d & e & f \\
g & h & i
\end{matrix}
\right)
$$

:::
::::

Ker so matrike običajno ločene, obstaja pet dodatnih okolj, ki vsebino matrike preprosto obkrožajo z ločevalniki. Ti okolji so prikazen v [Tabeli %s](#tab:latex_matrike):

::::{list-table} Okolja za matrike
:header-rows: 1
:label: tab:latex_matrike

* - LaTeX
  - PDF
* - `\begin{matrix} a & b \\ c & d \end{matrix}`
  - $\begin{matrix} a & b \\ c & d \end{matrix}$
* - `\begin{pmatrix} a & b \\ c & d \end{pmatrix}`
  - $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$
* - `\begin{bmatrix} a & b \\ c & d \end{bmatrix}`
  - $\begin{bmatrix} a & b \\ c & d \end{bmatrix}$
* - `\begin{Bmatrix} a & b \\ c & d \end{Bmatrix}`
  - $\begin{Bmatrix} a & b \\ c & d \end{Bmatrix}$
* - `\begin{vmatrix} a & b \\ c & d \end{vmatrix}`
  - $\begin{vmatrix} a & b \\ c & d \end{vmatrix}$
* - `\begin{Vmatrix} a & b \\ c & d \end{Vmatrix}`
  - $\begin{Vmatrix} a & b \\ c & d \end{Vmatrix}$
::::

Matrike, ki so ustvarili z uporabo teh okolij so precej velike, ker so namenjene za prikazni način. Če jih želite uporabiti v vrstičnem načinu, lahko uporabimo okolje `smallmatrix`, ki je manjše različica okolja `matrix`. Okolja `smallmatrix` ni mogoče uporabiti z ločevalniki, zato morate ročno dodati oklepaje ali druge ločevalnike okoli matrike.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
Primerjajte
$\left(
\begin{smallmatrix}
a & b \\
c & d
\end{smallmatrix}
\right)
$ z
$\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}$
```

:::

:::{card} PDF

Primerjajte
$
\left(
\begin{smallmatrix}   
a & b \\
c & d
\end{smallmatrix}
\right)
$ z
$\begin{pmatrix}   
a & b \\
c & d 
\end{pmatrix}$
:::
::::

Okolje `matrix` lahko uporabimo tudi za ustvarjanje matematičnih izrazov, opredeljenih s primeri, točno kot okolje `array`.
Vendar, okolje `cases` ponuja boljšo obliko za ta namen.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
y= \begin{cases}
a & \text{če }d>c\\
b+x & \text{zjutraj}\\
l & \textrm{čez cel dan}
\end{cases}
\]
```

:::

:::{card} PDF

$$
y= \begin{cases}
  a & \text{če }d>c\\
  b+x & \text{zjutraj}\\
  l & \textrm{čez cel dan}
\end{cases}
$$

:::
::::
:::::

:::::{dropdown} Večvrstne enačbe

**Dolge enačbe**

Okolje `equation` omogoča pisanje enovrstičnih enačb. Vendar pa je včasih enačba predolga, da bi se prilegala eni vrstici:

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
a = b + c + d + e + f
+ g + h + i + j
+ k + l + m + n + o + p
\]
```

:::

:::{card} PDF

$$
a = b + c + d + e + f
+ g + h + i + j
+ k + l + m + n + o + p
$$

:::
::::

V tem primeru je treba v enačbo vstaviti prelome vrstic.
Pri tem je pomembno upoštevati nekaj pravil za izboljšanje berljivosti:

- Na splošno je treba enačbo vedno razdeliti _pred_ znakom enakosti ali operatorjem.
- Prelom vrstice pred znakom za enakost je boljši kot prelom pred katerim koli drugim operatorjem.
- Prelom vrstice pred znaki `+` ali `-` je boljši kot prelom pred znaki `*`, `/`.
- Vsakršno drugo vrsto prelomov vrstic je treba po možnosti izogibati.

Najlažji način za prikazovanje večvrstnih enačb je uporaba okolja `multline`.
Omogoča prelom vrstic z uporabo ukaza `\\` in samodejno poravna prvo vrstico na levo in zadnjo vrstico na desno, medtem ko so vse vmesne vrstice poravnane na sredino.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{multline}
a + b + c + d + e \\
+ f + g + h + i \\
= j + k + l + m + n
\end{multline}
```

:::

:::{card} PDF

```{figure} ./img/04_eg-multline-2.png

```

::::

Če ne želite, da je določena notranja vrstica sredinsko poravnana, lahko uporabite ukaze `\shoveleft` ali `\shoveright`, da prisilite levo ali desno poravnavo določene vrstice.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{multline}
a + b + c \\
\shoveleft{+ d + e + f} \\
\shoveright{+ g + h + i} \\
= j + k + l + m + n
\end{multline}
```

:::

:::{card} PDF

```{figure} ./img/04_eg-multline-2.png

```

:::
::::

Podobno kot okolja `equation`, okolje `multline` samodejno doda številke vrsticam. Če želite odstraniti številke vrstic, lahko uporabite okolje `multline*`.

**Večkratna neporavnana enačba**

Pri sestavljanju več enačb v več okoljih `equation` se med njimi pojavi nepotrebni razmik.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{equation}
2 + 2 = 4
\end{equation}
\begin{equation}
2 \times 2 = 4
\end{equation}
\begin{equation}
2 + 2 \times 2 = 6
\end{equation}
```

:::

:::{card} PDF

\begin{equation}
2 + 2 = 4
\end{equation}
\begin{equation}
2 \times 2 = 4
\end{equation}
\begin{equation}
2 + 2 \times 2 = 6
\end{equation}
:::
::::

Da se temu izognemo, lahko uporabimo okolje `gather`, ki omogoča več enačb brez dodatnega razmika med njimi. Vsaka vrstica je samodejno poravnana na sredino in oštevilčena.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{gather}
2 + 2 = 4 \\
2 \times 2 = 4 \notag \\
2 + 2 \times 2 = 6
\end{gather}
```

:::

:::{card} PDF

\begin{gather}
2 + 2 = 4 \\
2 \times 2 = 4 \\
2 + 2 \times 2 = 6
\end{gather}
:::
::::

Vsaka enačba bo dobila svojo številko (tukaj v učbeniku ne, vendar v vašem dokumentu bo) in lahko uporabite ukaze `\label`, `\ref`, `\tag` in `\eqref` v vsaki enačbi.
Lahko pa uporabite ukaz `\notag`, da preprečite oštevilčenje določene enačbe.

Kot vedno, različica okolja `gather*` odstrani številke vrstic.

**Poravnane enačbe**

Okolje `align` omogoča pisanje več enačb, ki so poravnane glede na določen znak, običajno znak enakosti. To storimo z uporabo znaka `&`, ki označuje mesto poravnave v vsaki vrstici.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{align}
2 + 2 & = 2 \times 2 \\
3 + 3 & \neq 3 \times 3 \\
2 + 2 \times 2 & < 8
\end{align}
```

:::

:::{card} PDF

\begin{align}
2 + 2 & = 2 \times 2 \\
3 + 3 & \neq 3 \times 3 \\
2 + 2 \times 2 & < 8
\end{align}
:::
::::

Okolje `align` omogoča umestitev več matematičnih elementov v eno vrstico z uporabo več znakov `&` za določitev več mest poravnave.
Elementi se obravnavajo kot pari, zato bo vsak drugi znak poravnave ustvaril večje prostor, da se prilagodi razmik med pari.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{align}
a & \succeq b & c & \leq d \\
a & \geq d & d & \prec c
\end{align}
```

:::

:::{card} PDF

\begin{align}
a & \succeq b & c & \leq d \\
a & \geq d & d & \prec c
\end{align}
:::
::::

Okolje `align*` (z zvezdico) je tudi zelo uporabno za pisanje zaporedij izračunov, kjer je vsak korak prikazan v novi vrstici in so vsi znaki enakosti poravnani.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{align*}
\sum_{k=0}^n k
&= \sum_{k=0}^{n-1} k + n \\
&= \frac{n(n-1)}{2} + n \\
&= \frac{n(n+1)}{2}
\end{align*}
```

:::

:::{card} PDF

\begin{align*}
\sum*{k=0}^n k
&= \sum*{k=0}^{n-1} k + n \\
&= \frac{n(n-1)}{2} + n \\
&= \frac{n(n+1)}{2}
\end{align*}
:::
::::

**Enačbe kot gradniki**

Okolja `multline`, `gather` in `align` se lahko uporabljajo znotraj drugih matematičnih okolij, kot so `equation` ali `align` z dodajanjem končnice -ed k njihovemu imenu. Na primer, `multlineed`, `gathered` in `aligned`.
To so uporabno, kadar želite vključiti večvrstične enačbe, da dobi samo eno številko enačbe.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{equation}
\begin{aligned}
\sum_{k=0}^n k
&= \sum_{k=0}^{n-1} k + n \\
&= \frac{n(n-1)}{2} + n \\
&= \frac{n(n+1)}{2}
\end{aligned}
\end{equation}
```

:::

:::{card} PDF

\begin{equation}
\begin{aligned}
\sum*{k=0}^n k
&= \sum*{k=0}^{n-1} k + n \\
&= \frac{n(n-1)}{2} + n \\
&= \frac{n(n+1)}{2}
\end{aligned}
\end{equation}
:::
::::

:::::

:::::{dropdown} Presledki v matematičnem načinu

Kot smo že omenili, se razmik v matematičnem načinu obravnava drugače kot v običajnem besedilnem načinu.
V matematičnem načinu lahko vstavimo vodoravni presledek z uporabo ukaza `\mspace{širina}`, kjer je `širina` dolžina presledka, ki ga želimo vstaviti v posebni enoti `mu`, ki je približno enaka 1/18 širine črke 'M' v trenutni matematični pisavi.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
$a \mspace{18mu} 2$
```

:::

:::{card} PDF

$a \quad b$
:::
::::

Vendar pa je uporaba ukaza `\mspace` redka. Pogosteje se uporabljajo vnaprej določeni presledki, ki jih ponuja LaTeX:

::::{list-table} Ukazi za presledke v matematičnem načinu
:header-rows: 1

* - Ukaz
  - Alias
  - Velikost v `mu`
  - Primer
* - none
  -
  - `\mspace{0mu}`
  - $\rightarrow\leftarrow$
* - `\thinspace`
  - `\!`
  - `\mspace{3mu}`
  - $\rightarrow \thinspace \leftarrow$
* - `\medspace`
  - `\:`
  - `\mspace{4mu}`
  - $\rightarrow \: \leftarrow$
* - `\thickspace`
  - `\;`
  - `\mspace{5mu}`
  - $\rightarrow \; \leftarrow$
* - `\quad`
  -
  - `\mspace{18mu}`
  - $\rightarrow \quad \leftarrow$
* - `\qquad`
  -
  - `\mspace{36mu}`
  - $\rightarrow \qquad \leftarrow$
* - `\negthinspace`
  - `\!`
  - `\mspace{-3mu}`
  - $\rightarrow \negthinspace \leftarrow$
* - `\negmedspace`
  -
  - `\mspace{-4mu}`
  - $\rightarrow \negmedspace \leftarrow$
* - `\negthickspace`
  -
  - `\mspace{-5mu}`
  - $\rightarrow \negthickspace \leftarrow$

::::
:::::

:::::{dropdown} Drugi matematični izrazi

**Modularna aritmetika**
::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
a^{\varphi(n)} \equiv 1 \pmod n
\]
```

:::  
:::{card} PDF

$$
a^{\varphi(n)} \equiv 1 \pmod{n}
$$

:::
::::

**Binomski koeficienti**
::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[
\binom{n}{k} = \frac{n!}{k!(n-k)!}
\]
```

:::  
:::{card} PDF

$$
\binom{n}{k} = \frac{n!}{k!(n-k)!}
$$

:::
::::

**Tri pike**

Ukaz `\dots` ustvari tri pike in izpustiti del matematičnega izraza, ki ga je mogoče zlahka sklepati iz konteksta.
LaTeX poskuša prilagoditi svoj izpis na podlagi okoliških simbolov.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{gather*}
1, 2, 3, \dots, 100 \\
1 + 2 + 3 + \dots + 100 = 5050
\end{gather*}
```

:::

:::{card} PDF

\begin{gather*}
1, 2, 3, \dots, 100 \\
1 + 2 + 3 + \dots + 100 = 5050
\end{gather*}
:::
::::

Če razmik, ki ga izbere LaTeX, ni primeren, ha lahko določite izrecno z uporabo:

- `\dotsc` za tri pike med vejicami, `$1,2,\dotsc,100$`: $1,2, \dotsc , 100$.
- `\dotsb` za tri pike med binarnimi operatorji, `$1 + 2 + \dotsb + 100$`: $1 + 2 + \dotsb + 100$.
- `\dotsm` za tri pike, ki označujejo množenje `$a_1 a_2 \dotsm a_n$`: $a_1 a_2 \dotsm a_n$.
- `\dotsi` za tri pike med integraloma `$\int_{a_1}^{b_1} \int_{a_2}^{b_2} \dotsi \int_{a_n}^{b_n} f(x) \, dx$`: $\int_{a_1}^{b_1} \int_{a_2}^{b_2} \dotsi \int_{a_n}^{b_n} f(x) \, dx$.
- `\dotso` za tri pike v drugih kontekstih.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{gather*}
1 + 2 + 3 + \dots \\
1 + 2 + 3 + \dotsb \\
\end{gather*}
```

:::

:::{card} PDF

\begin{gather*}
1 + 2 + 3 + \dots \\
1 + 2 + 3 + \dotsb \\
\end{gather*}
:::
::::

Če nobena od zgornjih možnosti ni primerna, lahko uporabite ukaz `\ldots` za vodoravne tri pike na spodnji črti besedila, in `\cdots` za tri pike, ki so poravnane s sredino.

Ko delate z matrikami, lahko uporabite `\vdots` za navpične tri pike in `\ddots` za diagonalne tri pike (od zgoraj levo do spodaj desno) in `\adots` za diagonalne tri pike (od spodaj levo do zgoraj desno).

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\[  \begin{bmatrix}
a_{1,1} & \cdots & a_{1,n} \\
\vdots & \ddots & \vdots \\
a_{m,1} & \cdots & a_{m,n} \\
\end{bmatrix} \]
```

:::

:::{card} PDF

$$
\begin{bmatrix}
a_{1,1} & \cdots & a_{1,n} \\
\vdots & \ddots & \vdots \\
a_{m,1} & \cdots & a_{m,n} \\
\end{bmatrix}
$$

:::
::::

**Fantomski presledki**

Včasih je potrebno ustvariti presledek, ki zavzame prostor, vendar ni viden.
To lahko dosežemo z uporabo ukaza `\phantom{izraz}`, ki ustvari neviden element z enako širino kot `izraz`.
Ukaza `\hphantom{izraz}` in `\vphantom{izraz}` ustvarita neviden element z enako širino oziroma višino kot `izraz`.

::::{grid} 2 2 2 2

:::{card} LaTeX

```latex
\begin{multline*}
f(a, b) = \left(
\int_a^b f(x)
dooooooooolgo
\right. \\
\left.
\vphantom{
  \int_a^b f(x)
dooooooooolgo
}
kratko d x
\right)
\end{multline*}
```

:::

:::{card} PDF

```{figure} ./img/04_eg-multline-3.png

```

:::
::::
:::::

:::{exercise}
:label: ex-matematika-1
Napišite LaTeX kodo za naslednje matematične izraze:

1. $\cos^2 \theta + \sin^2 \theta = 1$
2. $\displaystyle \int_{0}^{\infty} e^{-x^2} \, dx = \frac{\sqrt{\pi}}{2}$
3. $\displaystyle \sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}$
4. Če je
$A =\begin{pmatrix} 2 & 1 & 1 \\ 1 & 1 & 0 \\ 1 & 0 & 1 \end{pmatrix}$ torej je
$
A^{-1} = 
\begin{pmatrix}1 & -1 & -1 \\
-1 & 2 & 1 \\
-1 & 1 & 2
\end{pmatrix}
$

5. $\displaystyle |x| = \begin{cases}
x & \text{če } x \geq 0 \\
-x & \text{če } x < 0
\end{cases}$

6. Če je $\vec{v} = (v_1, \dots, v_n)$, torej je njena norma definirana kot
$\lvert \vec{v}\rvert = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}$.
:::

```{margin}
[Seznam vaj](#latexMatematika_vaje)
```

:::{solution} ex-matematika-1
:class: tip, dropdown

1. ```latex
\[
\cos^2 \theta + \sin^2 \theta = 1
\]
```
2. ```latex
\[
\int_{0}^{\infty} e^{-x^2} \, dx = \frac{\sqrt{\pi}}{2}
\]
```
3. ```latex
\[
\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}
\]
```
4. ```latex
Če je $A =\begin{pmatrix} 2 & 1 & 1 \\ 1 & 1 & 0 \\ 1 & 0 & 1 \end{pmatrix}$  torej je
$ A^{-1} = \begin{pmatrix}1 & -1 & -1 \\ -1 & 2 & 1 \\ -1 & 1 & 2\end{pmatrix}$
```
5. ```latex
\[
|x| = \begin{cases}
x & \text{če } x \geq 0 \\
-x & \text{če } x < 0
\end{cases}
\]
```
````

6. ```latex
Če je $\vec{v} = (v_1, \dots, v_n)$, torej je njena norma definirana kot
$\lvert \vec{v}\rvert = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}$.
````
:::

:::{exercise}
:label: ex-matematika-2
Napišite LaTeX kodo za naslednje matematične izraze:

- \begin{align}
x^2 + y^2 &= 1\\
y &= \sqrt{1-x^2} && \text{če je } y \geq 0\\
\end{align}

- \begin{align}
x+2y+3z & = 6\\
2x+3y+z & = 5\\
3x+y+2z & = 7
\end{align}

- \begin{align}
(x+y)^n & = \sum\_{k=0}^{n} \binom{n}{k} x^{n-k} y^k\\
& = x^n + \binom{n}{1} x^{n-1} y + \binom{n}{2} x^{n-2} y^2 + \dots + y^n
\end{align}

:::

```{margin}
[Seznam vaj](#latexMatematika_vaje)
```

:::{solution} ex-matematika-2
:class: tip, dropdown

- ```latex
\begin{align}
x^2 + y^2  &= 1\\
y &= \sqrt{1-x^2} && \text{če je } y \geq 0\\
\end{align}
```
- ```latex
\begin{align}
x+2y+3z & = 6\\
2x+3y+z & = 5\\
3x+y+2z & = 7
\end{align}
```
- ```latex
\begin{align}
(x+y)^n & = \sum_{k=0}^{n} \binom{n}{k} x^{n-k} y^k\\
& = x^n + \binom{n}{1} x^{n-1} y + \binom{n}{2} x^{n-2} y^2 + \dots + y^n
\end{align}
```
:::

:::{exercise}
:label: ex-matematika-3
Napišite LaTeX kodo, da reproducira besedilo prikazano na sliki spodaj:

```{figure} ./img/04_ex-maxwell.png
:name: fig_ex_maxwell
```

:::

```{margin}
[Seznam vaj](#latexMatematika_vaje)
```

:::{solution} ex-matematika-3
:class: tip, dropdown

```latex
Maxwellove enačbe v vakuumu so:
\begin{align}
\nabla \cdot \mathbf{E} & = \frac{\rho}{\varepsilon_0} \label{eq:GaussE} \\
\nabla \cdot \mathbf{B} & = 0 \label{eq:GaussB} \\
\nabla \times \mathbf{E} & = -\frac{\partial \mathbf{B}}{\partial t} \label{eq:Faraday} \\
\nabla \times \mathbf{B} & = \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t} \label{eq:Ampere}
\end{align}

Enačba \ref{eq:GaussE} opisuje Gaussov zakon za električno polje, enačba \ref{eq:GaussB} pa Gaussov zakon za magnetno polje. Enačba \ref{eq:Faraday} predstavlja Faradayev zakon elektromagnetne indukcije, medtem ko enačba \ref{eq:Ampere} predstavlja Amperov zakon z Maxwellovim dodatkom.
```

:::

## Izreki, dokazi, definicije, itd..

Ko sestavljanju matematičnih besedil je pogosto potrebno vključiti izreke, dokaze, definicije in podobne strukture (ki jih bomo zaradi enostavnosti imenovali "teoremi").
Paket `amsthm`, ponuja enostaven način za ustvarjanje teh struktur z uporabo okolij.

Najprej moramo definirati nova okolja za naše teoreme v preambuli dokumenta.
To storimo z uporabo ukaza

```latex
\newtheorem{<ime_okolja>}[<drugi_teorem>]{<Napis>}[<razdelek>]
```

kjer je `<ime_okolja>` ime novega okolja in
`<Napis>` je besedilo, ki se bo prikazalo pred številko teorema.
Neobvezna argumenta `<drugi_teorem>` in `<razdelek>` določata, kako se bodo teoremi številčili (in lahko uporabimo samo ena od njih ali nobene).
Uporabimo `<drugi_teorem>`, če želimo, da se novi teoremi številčijo skupaj z obstoječim teoremom, kjer je `<drugi_teorem>` ime okolja.
Če želimo, da se številčenje teoremov ponastavi v vsakem razdelku, uporabimo `<razdelek>`, kjer je `<razdelek>` ime števca razdelkov (npr. `section` ali `subsection`).
Če ne uporabimo nobenega od teh dveh argumentov, se bodo teoremi številčili neodvisno skozi celoten dokument (1, 2, 3, ...).
Ukaz `\newtheorem*{<ime_okolja>}{<Naslov>}` definira različico okolja, ki ne bo imela številke.

Po definiciji okolja lahko uporabimo novo okolje v našem dokumentu z uporabo standardnega LaTeX okolja sintakse:

```latex
\begin{<ime_okolja>}[<Naslov>]
Vsebina teorema.
\end{<ime_okolja>}
```

Neobvezni argument `<Naslov>` omogoča dodajanje naslova teorema, ki bo prikazan poleg številke teorema.

:::{prf:example}
:label: eg_theorems_1

`````{tab-set}
  ````{tab-item} LaTeX
    ```latex
    %V preambuli dokumenta
    \usepackage{amsthm}
    \newtheorem{izrek}{Izrek}
    %V telesu dokumenta
    \begin{izrek}[Pitagorov izrek]
      Vsota površin kvadratov katet pravokotnega
      trikotnika je enaka površini kvadrata nad
      hipotenuzo.
      Izrek lahko zapišemo tudi kot: \[c^{2} = a^{2} + b^{2}\]
    \end{izrek}
    ```
  ````
  ````{tab-item} PDF
    ``` {figure} ./img/04_eg-theorems-1.png
      :name: fig_theorems_1
    ```
  ````
`````

:::

V LaTeXu obstajajo tri različne sloge teoremov:

- `plain`: privzeti slog, krepko naslov in poševno telo.
- `definition`: krepko naslov in pokončno telo.
- `remark`: poševno naslov in pokončno telo.

Za nastavitev sloga teorema uporabimo ukaz

```latex
\theoremstyle{<slog>}
```

pred definicijo okolja teorema.
Vsak teorem, ki je definiran po tem ukazu, bo uporabil določen slog.

:::{prf:example}
:label: eg_theorems_2

`````{tab-set}
````{tab-item} LaTeX
```latex
  % V preambuli
  \theoremstyle{plain}
  \newtheorem{izrek}{Izrek}[section]
  \newtheorem{trd}[izrek]{Trditev}
  \theoremstyle{definition}
  \newtheorem{defja}[izrek]{Definicija}
  \theoremstyle{remark}
  \newtheorem*{zgled}{Zgled}
  % ...
  % V telesu dokumenta
  \section{Razdelek z teoremi}
  \begin{izrek} (Pitagorov izrek)
    V pravokotnem trikotniku velja \[c^{2} = a^{2} + b^{2}\]
  \end{izrek}
  % ...
  \begin{trd}
    Ne vem, če ta trditev velja.
  \end{trd}
  % ...
  \begin{defja}
    Tukaj sem napisal definicijo. Običajno vporabljamo \emph{povdarjeno} besedilo za naslove definicij.
  \end{defja}
  % ...
  \begin{zgled}
    Tukaj sem napisal primer.
  \end{zgled}
```
````
````{tab-item} PDF
``` {figure} ./img/04_eg-theorems-2.png
:name: fig_theorems_2
```
````
`````

:::

Paket `amsthm` ponuja tudi okolje `proof` za pisanje dokazov.
Okolje samodejno doda besedo "Dokaz" na začetek in simbol kvadrata na konec dokaza.

:::{prf:example}
:label: eg-theorems_3

`````{tab-set}
  ````{tab-item} LaTeX
    ```latex
     \begin{trd}
      Ne vem, če ta trditev velja.
    \end{trd}
    \begin{proof}
      Očitno, uporabimo
      \[E=mc^2.\]
    \end{proof}
    ```
  ````
  ````{tab-item} PDF
    ``` {figure} ./img/04_eg-theorems-3.png
      :name: fig_theorems_3
    ```
  ````
`````

:::

Ukaz `\qedhere` lahko uporabimo znotraj okolja `proof`, da postavimo simbol kvadrata na določeno mesto, običajno na konec enačbe.

:::{prf:example}
:label: eg-theorems_4

`````{tab-set}
  ````{tab-item} LaTeX
    ```latex
     \begin{trd}
      Ne vem, če ta trditev velja.
    \end{trd}
    \begin{proof}
      Očitno, uporabimo
      \[E=mc^2. \qedhere\]
    \end{proof}
    ```
  ````
  ````{tab-item} PDF
    ``` {figure} ./img/04_eg-theorems-4.png
      :name: fig_theorems_4
    ```
  ````
`````

:::

:::{exercise}
:label: ex-matematika-4
V svoj dokument napišite LaTeX kodo za naslednje besedilo:

```{figure} ./img/04_ex-theorems.png
:name: fig_ex_theorems
```

:::

```{margin}
[Seznam vaj](#latexMatematika_vaje)
```

:::{solution} ex-matematika-4
:class: tip, dropdown

Ustrezni deli kode so naslednji:

```latex
% V preambuli
\usepackage{amsthm}
\theoremstyle{plain}
\newtheorem{izrek}{Izrek}

% V telesu dokumenta
\begin{izrek}[de Morganovi zakoni]
  Za vsakih dvoje podmnožic $A$ in $B$ množice $X$ veljata naslednji enačbi:
  \begin{align}
    X\setminus (A \cup B) & = (X \setminus A) \cap (X \setminus B) \label{eq:deMorgan1}\\
    X\setminus (A \cap B) & = (X \setminus A) \cup (X \setminus B) \label{eq:deMorgan2}
  \end{align}
\end{izrek}
\begin{proof}
  Dokaz za prvo enačbo:
  Naj bo $x \in X\setminus (A \cup B)$. Potem
  \begin{align*}
    x \in X \text{ in } x \notin A \cup B
    & \Rightarrow x \in X \text{ in } (x \notin A \text{ in } x \notin B) \\
    & \Rightarrow  (x \in X \text{ in } x \notin A) \text{ in } (x \in X \text{ in } x \notin B) \\
    & \Rightarrow x \in X \setminus A \text{ in } x \in X \setminus B \\
    & \Rightarrow  x \in (X \setminus A) \cap (X \setminus B)
  \end{align*}
%
  Obratno, naj bo $x \in (X \setminus A) \cap (X \setminus B)$. Potem
  \begin{align*}
    x \in (X \setminus A) \cap (X \setminus B)
    & \Rightarrow (x \in X \text{ in } x \notin A) \text{ in } (x \in X \text{ in } x \notin B) \\
    & \Rightarrow x \in X \text{ in } (x \notin A \text{ in } x \notin B) \\
    & \Rightarrow x \in X \text{ in } x \notin A \cup B \\
    & \Rightarrow x \in X\setminus (A \cup B)
  \end{align*}
S tem je dokaz prve enačbe zaključen.

  Dokaz za drugo enačbo je podoben:
  Naj bo $x \in X\setminus (A \cap B)$. Potem
  \begin{align*}
    x \in X\setminus (A \cap B)
    & \Rightarrow x \in X \text{ in } x \notin A \cap B \\
    & \Rightarrow x \in X \text{ in } (x \notin A \text{ ali } x \notin B) \\
    & \Rightarrow  (x \in X \text{ in } x \notin A) \text{ ali } (x \in X \text{ in } x \notin B) \\
    & \Rightarrow x \in X \setminus A \text{ ali } x \in X \setminus B \\
    & \Rightarrow  x \in (X \setminus A) \cup (X \setminus B)
  \end{align*}
%
Obratno, naj bo $x \in (X \setminus A) \cup X \setminus B$. Potem
  \begin{align*}
    x \in (X \setminus A) \cup (X \setminus B)
    & \Rightarrow (x \in X \text{ in } x \notin A) \text{ ali } (x \in X \text{ in } x \notin B) \\
    & \Rightarrow x \in X \text{ in } (x \notin A \text{ ali } x \notin B) \\
    & \Rightarrow x \in X \text{ in } x \notin A \cap B \\
    & \Rightarrow x \in X\setminus (A \cap B)
  \end{align*}
  Sledi, da $X\setminus (A\cap B) = (X \setminus A) \cup (X \setminus B)$.

  Torej enačbi \ref{eq:deMorgan1} in \ref{eq:deMorgan2} držita.
\end{proof}
```

:::

(latexMatematika_vaje)=

## Vaje

- [Vaja %s](#ex-matematika-1): Napišite LaTeX kodo za osnovne matematične izraze.
- [Vaja %s](#ex-matematika-2): Napišite LaTeX kodo za matematične izraze z uporaba okolji `align` in `align*` in `aligned`.
- [Vaja %s](#ex-matematika-3): Napišite LaTeX kodo, da reproducira Maxwellove enačbe.
- [Vaja %s](#ex-matematika-4): Napišite LaTeX kodo za izreke in dokaze.

:::{exercise} Domača naloga
:nonumber:
Spodaj je seznam znanih matematičnih izrekov.

- Mali Fermatov izrek.
- Taylorjev izrek.
- Osnovni izrek matematične analize.
- Izrek o srednji vrednosti.
- Kitajski izrek o ostankih.
- Evklidov izrek (neskončnost praštevil).
- Binomski izrek.
- Izrek o implicitni funkciji.
- Izrek da je $\sqrt{p}$ iracionalno število za vsako praštevilo $p$.
- de Moivreova formula.

1. Izberite dveh izmed njih in napišite LaTeX datoteko, ki vsebuje natančno formulacijo izbranih izrekov skupaj z njihovimi dokazi.
2. Uporabite okolje in sloge teoremov, kot je opisano v tem poglavju.
3. V dokument, vključujete seznam virov, ki ste jih uporabili za iskanje izrekov in njihovih dokazov, zato morate uporabite paket `biblatex` za upravljanje literature.
4. Oddajte kodo kot datoteko `.zip`.

**Opomba:** Ne morate dokazovati izrekov sami, lahko uporabite dokaze iz zanesljivih virov, vendar morate pravilno citirati te vire v svojem dokumentu. Če ne znate virov citirati, se obrnite na svojega profesorja za pomoč.
:::
