
# Dolžine v LaTeXu

Dolžine (*lengths*) so pomemben del LaTeXa, saj omogočajo natančen nadzor nad razmikom, velikostjo elementov, zamiki, robovi in še več. 
Vsaka dolžina je shranjena kot spremenljivka, ki ji lahko dodelimo vrednost, jo povečamo ali zmanjšamo, in uporabimo pri različnih ukazih.



## Osnovne merske enote

V LaTeXu lahko dolžine izrazimo z različnimi enotami. Najpogosteje uporabljene so: 

| Enota | Opis |
|:------|:------|
| `pt`  | točka (1/72,27 palca) – osnovna enota v TeXu |
| `mm`  | milimeter |
| `cm`  | centimeter |
| `in`  | palec (2.54 cm) |
| `ex`  | višina male črke *x* v trenutni pisavi |
| `em`  | širina črke *M* v trenutni pisavi |
| `bp`  | velika točka (1/72 palca) |
| `pc`  | pica = 12 točk |
| `dd`  | didotova točka |
| `cc`  | cicer = 12 didotov |
| `sp`  | najmanjša notranja enota v TeXu (65536 sp = 1 pt) |

## Privzete dolžinske spremenljivke

LaTeX ima več že vnaprej določenih dolžin, ki vplivajo na izgled dokumenta:

| Dolžina | Opis |
|:---------|:------|
| `\textwidth` | širina glavnega besedila |
| `\textheight` | višina glavnega besedila |
| `\linewidth` | širina vrstice znotraj okolja (npr. v `minipage`) |
| `\columnwidth` | širina stolpca v dvostolpčnem načinu |
| `\paperwidth`, `\paperheight` | dimenzije papirja |
| `\parindent` | zamik prve vrstice odstavka |
| `\parskip` | razmik med odstavki |
| `\baselineskip` | navpična razdalja med vrsticami besedila |
| `\topmargin`, `\oddsidemargin`, `\evensidemargin` | robovi strani |

<!-- Primer uporabe:

```latex
\setlength{\parindent}{0pt}
\setlength{\parskip}{1em}
```

S tem odstranimo zamik odstavkov in dodamo več prostora med njimi.

## Določanje in spreminjanje dolžin

Za delo z dolžinami uporabljamo naslednje ukaze:

```latex
\setlength{\ime}{vrednost}
\addtolength{\ime}{vrednost}
```

Primer:

```latex
\setlength{\textwidth}{14cm}
\addtolength{\textwidth}{1cm}
```

Ukaz `\setlength` nastavi absolutno vrednost, medtem ko `\addtolength` doda (ali odšteje) določeno dolžino.

## Uporaba dolžin v izrazih

LaTeX omogoča uporabo relativnih vrednosti in računanje z dolžinami z uporabo ukaza `\dimexpr`. Primer:

```latex
\setlength{\textwidth}{\dimexpr\paperwidth-2in\relax}
```

Ta ukaz nastavi širino besedila tako, da je za 2 palca manjša od širine papirja. -->

<!-- ## Uporabni namigi

- Dolžine lahko definirate tudi sami z `\newlength`:
  ```latex
  \newlength{\mojadolzina}
  \setlength{\mojadolzina}{5cm}
  ```
- Za začasne spremembe uporabite okolje `minipage`, kjer lahko lokalno spremenite `\linewidth`.
- Za bolj napreden nadzor nad postavitvijo lahko uporabite pakete kot so `geometry`, `calc` ali `layouts`. -->




