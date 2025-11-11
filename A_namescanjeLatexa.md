(A_latexInstallation)=
# Nameščanje LaTeXa na svoj računalnik

LaTeX je popolnoma brezplačen in ga lahko enostavno namestite na svoj računalnik.
Uradno spletno stran za namestitev si lahko ogledate [tukaj](https://www.latex-project.org/get/) (v angleščini).

Za uporabo LaTeXa potrebujete v bistvu dve orodji:
- distribucijo LaTeX, ki je sam program LaTeX, s katerim boste ustvarjali svoje dokumente.
- urejevalnik besedil, ki je vmesnik, ki ga boste uporabljali za pisanje in izdelavo dokumentov. Verjetno že imate urejevalnik besedil na svojem računalniku (npr. Notepad ali TextEdit). Ti urejevalniki so večnamenski in imajo običajno zelo malo orodij. Na tej strani priporočamo nekaj možnosti, ki vam bodo olajšale delo.


##  Windows

### Namestitev distribucije
1. Odprite spletno stran [MiKTeX](https://miktex.org/download).
2. Prenesite namestitveni program za Windows.
3. Zaženite namestitev in sledite navodilom (pustite privzete nastavitve).
4. Po zaključku preverite namestitev tako, da v ukazni vrstici (Command Prompt) vpišete:
   ```
   pdflatex --version
   ```

### Priporočeni urejevalniki
- [Visual Studio Code](https://code.visualstudio.com/) (potrebujete tudi razširitev *LaTeX Workshop*). Še bolje, predlagamo, da namestite [VSCodium](https://vscodium.com/), brezplačno/odprtokodno različico vscode.

- [TeXworks](https://www.tug.org/texworks/) (preprost, pogosto nameščen z MiKTeX).
- [TeXstudio](https://www.texstudio.org/) (bolj napreden, uporabniku prijazen).

## macOS

### Namestitev distribucije
1. Odprite spletno stran [MacTeX](https://tug.org/mactex/).
2. Prenesite paket **MacTeX.pkg** (velik ~4 GB).
3. Odprite preneseno datoteko in sledite navodilom za namestitev.
4. Preverite namestitev v Terminalu:
   ```
   pdflatex --version
   ```

### Priporočeni urejevalniki
- [Visual Studio Code](https://code.visualstudio.com/) (razširitev *LaTeX Workshop*).
Še bolje, predlagamo, da namestite [VSCodium](https://vscodium.com/), brezplačno/odprtokodno različico vscode.
- [TeXShop](https://pages.uoregon.edu/koch/texshop/) (priložen MacTeX-u).
- [TeXstudio](https://www.texstudio.org/).



## Linux (primer: Ubuntu/Debian)

Če uporabljate Linux, verjetno ne potrebujete naših navodil. 

### Namestitev distribucije
1. Odprite Terminal.
2. Namestite TeX Live:
   ```
   sudo apt update
   sudo apt install texlive-full
   ```
3. Preverite namestitev:
   ```
   pdflatex --version
   ```

### Priporočeni urejevalniki
- [Visual Studio Code](https://code.visualstudio.com/). (razširitev *LaTeX Workshop*). Še bolje, predlagamo, da namestite [VSCodium](https://vscodium.com/), brezplačno/odprtokodno različico vscode. 
- [Kile](https://kile.sourceforge.io/) (posebej priljubljen v Linux okolju).
- [TeXstudio](https://www.texstudio.org/).
- [TeXworks](https://www.tug.org/texworks/).
