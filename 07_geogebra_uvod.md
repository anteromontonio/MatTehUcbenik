---
kernelspec:
  name: python
  display_name: Python 3
---

# GeoGebra: Uvod kot MD

:::{code-cell} python
:tags: remove-input
import IPython.display as display
from IPython.display import IFrame
:::


## Kaj je Geogebra?

[Geogebra](https://www.geogebra.org/) je brezplačno dinamično matematično orodje, ki omogoča raziskovanje in vizualizacijo različnih matematičnih konceptov.

Trenuto, Geogebra je popoln paket za učenje in poučevanje matematike. Ponuja različne aplikacije, ki pokrivajo področja, kot so geometrija, algebra, statistika in kalkulus.
Vse te aplikacije je mogoče namestiti lokalno ali dostopati do njih prek spleta:

- [Scientific Calculator](https://www.geogebra.org/scientific): Za izračune z ulomki, statistiko in osnovnimi matematičnimi funkcijami.
- [Graphing Calculator](https://www.geogebra.org/graphing): Za vizualizacijo enačb in funkcij z interaktivnimi grafikoni.
- [Geometry](https://www.geogebra.org/geometry): Za dinamične geometrijske koncepte in konstrukcije v ravnini.
- [3D Calculator](https://www.geogebra.org/3d): Za raziskovanje tridimenzionalnih oblik in površin.
- [CAS Calculator](https://www.geogebra.org/cas): Za simbolne izračune in reševanje enačb.
- [Calculator suit](https://www.geogebra.org/calculator): Kombinacija različnih orodij za širok spekter matematičnih nalog. Idealna za učence in študente.
- [Geogebra Classic](https://www.geogebra.org/classic): Vse-v-enem aplikacija, ki združuje vse zgoraj omenjene funkcije. Idealna za avtorije učnih gradiv.

Različne možnosti, ki jih ponuja vsako od orodij, so navedene v [Tabeli 1](#tab_geogebra-apps).

:::{list-table} Primerjava različnih aplikacij Geogebra
:header-rows: 1
:label: tab_geogebra-apps

   * - aplikacije / funkcije 
     - Scientific
     - Graphing
     - Geometry
     - 3D
     - CAS
     - Suit
     - Classic
   * - Numerični izračuni
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - Funkcije
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - Operacije z ulomki
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - Grafično prikazovanje
     - 
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - Drsniki
     - 
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - Vektorji in matrike
     - 
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - Tabele
     - 
     - ✓
     - 
     - 
     - ✓
     - ✓
     - ✓
   * - Geometrijske konstrukcije
     - 
     - 
     - ✓
     - ✓
     - ✓
     - ✓
     - ✓
   * - 3D prikazovanje
     - 
     - 
     - 
     - ✓
     - 
     - ✓
     - ✓
   * - Verjetnost in statistika
     - 
     - 
     - 
     - 
     - 
     - ✓
     - ✓
   * - Odvodi in integrali
     - 
     - 
     - 
     - ✓
     - ✓
     - ✓
     - ✓
   * - Reševanje enačb
     - 
     - 
     - 
     - ✓
     - ✓
     - ✓
     - ✓
   * - Simbolni izračuni
     - 
     - 
     - 
     - ✓
     - ✓
     - ✓
     - ✓
   * - Spreadsheets
     - 
     - 
     - 
     - 
     - 
     - 
     - ✓
:::


Mi bomo v nadaljevanju uporabljali predvsem [Geogebra Classic](https://www.geogebra.org/classic), saj omogoča uporabo vseh orodij na enem mestu.

## Kako začnemo z Geogebro?

Geogebra lahko uporabimo na dva načina: prek spletnega brskalnika ali z namestitvijo aplikacije na računalnik (ali telefon/tablet).

V vsakem primeru bomo uporabili račun Geogebra, ki nam omogoča shranjevanje naših delovnih zvezkov v oblak in dostop do njih od kjerkoli. 

:::{exercise}
:label: ex_geogebra-account
Ustvarite račun Geogebra.
:::

:::{solution} ex_geogebra-account
:class: dropdown
1. Obiščite [spletno stran Geogebra](https://www.geogebra.org/).
2. Kliknite na "Sign in" gumb v zgornjem desnem kotu strani.
3. Izberite "Create account".
4. Izberite način registracije (prek e-pošte ali z uporabo obstoječega računa, npr. Google, Microsoft, Office 365).
:::

Zdaj imate dve možnosti za začetek uporabe Geogebre:
1. **Uporaba spletnega brskalnika**:
	 - Obiščite [Geogebra Classic](https://www.geogebra.org/classic).
	 - Kliknite na gumn  <img src="./geogebra/images/16px-Menu-button-open-menu.svg.png" class="inline" width="22px"> _Menu_ v zgornjem levem kotu.
	 - Prijavite se s svojim računom z klikom na  <img src="./geogebra/images/16px-Menu-signin.png" class="inline" width="22px"> _Sign in_.
2. **Namestitev aplikacije**:
	 - Prenesite aplikacijo Geogebra Classic za vaš operacijski sistem z [uradne strani za prenos](https://geogebra.github.io/docs/reference/en/GeoGebra_Installation/#_geogebra_classic_6).
	 - Namestite aplikacijo in jo odprite.
	 - Prijavite se s svojim računom z klikom na gumb <img src="./geogebra/images/16px-Menu-button-open-menu.svg.png" class="inline" width="22px"> _Menu_  v zgornjem levem kotu in nato na <img src="./geogebra/images/16px-Menu-signin.png" class="inline" width="22px"> _Sign in_ .	 
	 
Ko odprete Geogebro in se prijavite, boste videli glavno delovno okolje. Privzeto je prikazi <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px">_Graf_ (ang. <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px">_Graphing perspective_), ki omogoča risanje funkcij in geometrijskih objektov. Lahko jo vidite tudi spodaj:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/classic/bmkqk4ju", width=600, height=450, frameborder="1")
:::

:::{note} Opomba.
<img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px">_Graphing perspective_ je eden izmed več prikazi, ki jih ponuja Geogebra. Vsaka aplikacija Geogebre je sestavljena iz različnih prikazov, tako da lahko ustvarimo gradiva za različne aplikacije.
Različne prikaze lahko izberemo s klikom na gumb <img src="./geogebra/images/16px-Menu-button-open-menu.svg.png" class="inline" width="22px"> _Menu_ v zgornjem levem kotu in nato izbiro možnosti <img src="./geogebra/images/16px-Menu-perspectives.svg.png" class="inline" width="22px"> _Perspectives_.
:::

Vsak prikaz ponuja različne _poglede_ (ang, _views_).
Lahko jih dodamo ali odstranimo glede na naše potrebe s klikom na gumb <img src="./geogebra/images/16px-Menu-button-open-menu.svg.png" class="inline" width="22px"> _Menu_ v zgornjem levem kotu in nato izbiro možnosti <img src="./geogebra/images/16px-Menu-view.svg.png" class="inline" width="22px"> _View_.
Različni pogledi vključujejo:
- <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px"> _Algebrsko okno_ (ang. <img src="./geogebra/images/16px-Menu_view_algebra.svg.png" class="inline">_Algebra_).
- <img src="./geogebra/images/16px-Menu_view_cas.svg.png" class="inline"> _Simbolno računanje_ (ang. <img src="./geogebra/images/16px-Menu_view_cas.svg.png" class="inline">_CAS_).
- <img src="./geogebra/images/16px-Menu_view_graphics.svg.png" class="inline"> _Risalna površina_ (ang. <img src="./geogebra/images/16px-Menu_view_graphics.svg.png" class="inline">_Graphics_).
- <img src="./geogebra/images/16px-Menu_view_graphics.svg.png" class="inline"> _Grafika 2_ (ang. <img src="./geogebra/images/16px-Menu_view_graphics2.svg.png" class="inline">_Graphics 2_).
- <img src="./geogebra/images/16px-Perspectives_algebra_3Dgraphics.svg.png" class="inline"> _3d grafika_ (ang. <img src="./geogebra/images/16px-Perspectives_algebra_3Dgraphics.svg.png" class="inline">_3D Graphics_).
- <img src="./geogebra/images/16px-Menu_view_spreadsheet.svg.png" class="inline"> _Preglednica_ (ang. <img src="./geogebra/images/16px-Menu_view_spreadsheet.svg.png" class="inline">_Spreadsheet_).
- <img src="./geogebra/images/16px-Menu_view_probability.svg.png" class="inline"> _Računanje verjetnosti_ (ang. <img src="./geogebra/images/16px-Menu_view_probability.svg.png" class="inline">_Probability Calculator_).

Drugi vnosi nad gumbom <img src="./geogebra/images/16px-Menu-button-open-menu.svg.png" class="inline" width="22px"> _Menu_ omogočajo dostop do različnih orodij in nastavitev Geogebre, kot so:
- <img src="./geogebra/images/16px-Menu-file.svg.png" class="inline" width="22px"> _Datoteka_ (ang. <img src="./geogebra/images/16px-Menu-file.svg.png" class="inline" width="22px">_File_): Ustvarjanje, odpiranje, shranjevanje in izvoz datotek.
- <img src="./geogebra/images/16px-Menu-edit.svg.png" class="inline" width="22px"> _Uredi_ (ang. <img src="./geogebra/images/16px-Menu-edit.svg.png" class="inline" width="22px">_Edit_): Razveljavi, ponovi, kopiraj, prilepi in druge osnovne funkcije urejanja.
- <img src="./geogebra/images/16px-Menu-options.svg.png" class="inline" width="22px"> _Nastavitev_ (ang. <img src="./geogebra/images/16px-Menu-options.svg.png" class="inline" width="22px">_Settings_): Prilagajanje nastavitev Geogebre, kot so jezika, velikosti pisave in drugih možnosti.
- <img src="./geogebra/images/16px-Menu-tools.svg.png" class="inline"> _Orodja_ (ang. <img src="./geogebra/images/16px-Menu-tools.svg.png" class="inline" width="22px" >_Tools_): Dostop do različnih orodij za risanje in konstrukcije.
- <img src="./geogebra/images/24px-Menu-help.svg.png" class="inline" width="22px"> _Pomoč_ (ang. <img src="./geogebra/images/24px-Menu-help.svg.png" class="inline" width="22px">_Help and Feedback_): Dostop do dokumentacije, vadnic in podpore skupnosti Geogebra.
- <img src="./geogebra/images/24px-Menu-account.png" class="inline" width="22px"> _Račun_ (ang. <img src="./geogebra/images/24px-Menu-account.png" class="inline" width="22px"> _Account_): Prijava in odjava iz računa Geogebra.

:::{warning} Opomba
Geogebra se lahko uporablja v slovenskem jeziku, vmesnik je preveden, prav tako pa tudi ukazi, žal pa ni dokumentacije v slovenskem jeziku za ukaze (ki jih uporabljamo za ustvarjanje gradiva). Zaradi tega bomo vmesnik ohranili v angleščini, vendar upoštevajte, da če želite Geogebro uporabljati z otroki ali učenci, lahko jezik spremenite v meniju <img src="./geogebra/images/16px-Menu-options.svg.png" class="inline" width="22px">_Settings_.
:::


Poleg gumba <img src="./geogebra/images/16px-Menu-button-open-menu.svg.png" class="inline" width="22px"> _Menu_, pomembni del orodjarne so tudi:

:::{list-table}

* - *Orodja vrstica* (ang. *Toolbar*):
  -  <img src="./geogebra/images/344px-Toolbar-Graphics.png" class="inline">
* - *Slog vrstica* (ang. *Stylebar*):
  -  <img src="./geogebra/images/40px-Stylingbar_icon_graphics.svg.png" class="inline" width="24px">
* - *Razveljavi* (ang. *Undo*):
  -  <img src="./geogebra/images/24px-Menu-edit-undo.svg.png" class="inline" width="24px">
* - *Ponovno naredi* (ang. *Redo*):
  -  <img src="./geogebra/images/24px-Menu-edit-redo.svg.png" class="inline" width="24px">
:::


