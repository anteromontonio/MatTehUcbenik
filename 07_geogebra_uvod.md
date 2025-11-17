---
kernelspec:
  name: python
  display_name: Python 3
---
<script src="https://www.geogebra.org/apps/deployggb.js"></script>


# GeoGebra: Uvod

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
IFrame("https://www.geogebra.org/material/iframe/id/bmkqk4ju/width/1280/height/720/border/3C82F6/sfsb/true/smb/true/stb/true/stbh/true/ai/true/asb/true/sri/true/rc/true/ld/true/sdz/true/ctl/true/szb/true", width="600", height="340px", allowfullscreen=True)
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

* - *Orodarne* (ang. *Toolbar*):
  -  <img src="./geogebra/images/344px-Toolbar-Graphics.png" class="inline">
* - *Slog vrstica* (ang. *Stylebar*):
  -  <img src="./geogebra/images/40px-Stylingbar_icon_graphics.svg.png" class="inline" width="24px">
* - *Razveljavi* (ang. *Undo*):
  -  <img src="./geogebra/images/24px-Menu-edit-undo.svg.png" class="inline" width="24px">
* - *Ponovno naredi* (ang. *Redo*):
  -  <img src="./geogebra/images/24px-Menu-edit-redo.svg.png" class="inline" width="24px">
:::

## Orodje

Geogebra ponuja širok nabor orodij za ustvarjanje in manipulacijo matematičnih objektov. Orodja so dostopna prek orodjarne (ang. _Toolbar_), ki se nahaja običajno na vrhu zaslona.
Orodjarna je odvisna od izbranega prikaza in ponuja različna orodja glede na kontekst.
Za zdaj, mi bomo raziskali nekaj osnovnih orodij, ki so na voljo v privzetem prikazu <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px">_Graphing_ in v prikazu <img src="./geogebra/images/16px-Menu_view_graphics.svg.png" class="inline" width="22px">_Graphics_, in sicer:
:::{image} ./geogebra/images/344px-Toolbar-Graphics.png
:::

V nadelevanju opisujemo nekatere najpogosteje uporabljena orodja, celoten seznam orodij pa najdete v [dokumentaciji Geogebre](https://geogebra.github.io/docs/manual/en/).

::::{dropdown} <img src="./geogebra/images/32px-Mode_move.svg.png" class="inline" width="22px">
:::{list-table}
:header-rows: 1
* - Orodje
  - 
  - Opis
* - <img src="./geogebra/images/32px-Mode_move.svg.png" class="inline" width="22px"> 
  - *Izbira in premikanje* (ang. *Move*) 
  - Omogoča izbiro in premikanje objektov v grafičnem prostoru.
:::
::::

::::{dropdown}<img src="./geogebra/images/32px-Mode_point.svg.png" width="22px" class="inline">
:::{list-table}
:header-rows: 1
* - Orodje
  -
  - Opis
* - <img src="./geogebra/images/32px-Mode_point.svg.png" class="inline" width="22px"> 
  - *Točka* (ang. *Point*) 
  - Ustvari posamezno točko na določenem mestu.
* - <img src="./geogebra/images/32px-Mode_pointonobject.svg.png" class="inline" width="22px"> 
  - *Točka na objektu* (ang. *Point on Object*) 
  - Ustvari točko, ki leži na izbranem objektu, kot je premica ali krog.
* - <img src="./geogebra/images/32px-Mode_intersect.svg.png" class="inline" width="22px"> 
  - *Točka presečišča* (ang.  *Intersect*) 
  - Ustvari točko na presečišču dveh izbranih objektov.
* - <img src="./geogebra/images/32px-Mode_midpoint.svg.png" class="inline" width="22px"> 
  - *Sredina ali središče* (ang. *Midpoint or Center*) 
  - Ustvari točko, ki predstavlja sredino daljice ali središče kroga.
* - <img src="./geogebra/images/32px-Mode_complexnumber.svg.png" class="inline" width="22px"> 
  - *Kompleksa števila* (ang. *Complex Number*)
  - Ustvari točko, ki predstavlja kompleksno število v kompleksni ravnini.
* - <img src="./geogebra/images/32px-Mode_roots.png" class="inline" width="22px"> 
  - *Ničle* (ang. *Roots*) 
  - Poišci ničle polinomov ali funkcij.
:::
::::

::::{dropdown} <img src="./geogebra/images/32px-Mode_line.svg.png" class="inline" width="22px">
:::{list-table}
:header-rows: 1
* - Orodje
  -
  - Opis
* - <img src="./geogebra/images/32px-Mode_line.svg.png" class="inline" width="22px"> 
  - *Premica* (ang. *Line*) 
  - Ustvari premico skozi dve izbrani točki.
* - <img src="./geogebra/images/32px-Mode_segment.svg.png" class="inline" width="22px"> 
  - *Daljica* (ang. *Segment*) 
  - Ustvari daljico med dvema izbranima točkama.
* - <img src="./geogebra/images/32px-Mode_ray.svg.png" class="inline" width="22px"> 
  - *Poltrak* (ang. *Ray*) 
  - Ustvari poltrak, ki se začne v eni točki in gre skozi drugo točko.
* - <img src="./geogebra/images/32px-Mode_vector.svg.png" class="inline" width="22px"> 
  - *Vektor* (ang. *Vector*) 
  - Ustvari vektor med dvema izbranima točkama.
:::
::::  


::::{dropdown} <img src="./geogebra/images/32px-Mode_orthogonal.svg.png" class="inline" width="22px">
:::{list-table}
:header-rows: 1
* - Orodje
  -
  - Opis
* - <img src="./geogebra/images/32px-Mode_orthogonal.svg.png" class="inline" width="22px"> 
  - *Pravokotnica* (ang. *Perpendicular line*) 
  - Ustvari pravokotnico glede na izbrano premico skozi določeno točko.
* - <img src="./geogebra/images/32px-Mode_parallel.svg.png" class="inline" width="22px"> 
  - *Paralelna* (ang. *Parallel line*) 
  - Ustvari paralelno premico glede na izbrani objekt skozi določeno točko.
* - <img src="./geogebra/images/32px-Mode_linebisector.svg.png" class="inline" width="22px"> 
  - *Simetrala daljice* (ang. *Line bisector*) 
  - Ustvari simetralo daljice med dvema izbranima točkama.
* - <img src="./geogebra/images/32px-Mode_angularbisector.svg.png" class="inline" width="22px"> 
  - *Simetrala kota* (ang. *Angle bisector*) 
  - Ustvari simetralo kota med tremi izbranimi točkami ali med dve izbranima premicama.
* - <img src="./geogebra/images/32px-Mode_tangent.svg.png" class="inline" width="22px"> 
  - *Tangente* (ang. *Tangent*) 
  - Ustvari tangento na krog ali krivuljo v določeni točki.
:::
::::

::::{dropdown} <img src="./geogebra/images/32px-Mode_polygon.svg.png" class="inline" width="22px">
:::{list-table}
:header-rows: 1
* - Orodje
  -
  - Opis  
* - <img src="./geogebra/images/32px-Mode_polygon.svg.png" class="inline" width="22px"> 
  - *Mnogokotnik* (ang. *Polygon*)
  - Ustvari zaprt mnogokotnik z izbranimi oglišči.
* - <img src="./geogebra/images/32px-Mode_regularpolygon.svg.png" class="inline" width="22px"> 
  - *Pravilen mnogokotnik* (ang. *Regular Polygon*) 
  - Ustvari pravilen mnogokotnik z določenim številom stranic med dvema izbranima točkama.
:::
::::

::::{dropdown} <img src="./geogebra/images/32px-Mode_circle.svg.png" class="inline" width="22px">
:::{list-table} 
:header-rows: 1
* - Orodje
  -
  - Opis
* - <img src="./geogebra/images/32px-Mode_circle2.svg.png" class="inline" width="22px"> 
  - *Krožnica s središčem in točko na njej* (ang. *Circle with Center and Point*) 
  - Ustvari krožnico z določenim središčem in točko na krožnici.
* - <img src="./geogebra/images/32px-Mode_circlepointradius.svg.png" class="inline" width="22px">
  - *Krožnica s središčem & polmer* (ang. *Circle with Center and Radius*) 
  - Ustvari krožnico z določenim središčem in polmerom.
* - <img src="./geogebra/images/32px-Mode_compasses.svg.png" class="inline" width="22px">
  - *Krožnica z polmerom* (ang. *Circle with Compass*) 
  - Ustvari krožnico z uporabo merila, ki ga nastavite med dvema izbranima točkama.
* - <img src="./geogebra/images/32px-Mode_circle3.svg.png" class="inline" width="22px"> 
  - *Krožnica skozi tri točke* (ang. *Circle through Three Points*) 
  - Ustvari krožnico, ki gre skozi tri izbrane točke.
* - <img src="./geogebra/images/32px-Mode_semicircle.svg.png" class="inline" width="22px"> 
  - *Polkrog* (ang. *Semicircle*) 
  - Ustvari polkrog z izbrano premerno daljico.
* - <img src="./geogebra/images/32px-Mode_circlearc3.svg.png" class="inline" width="22px"> 
  - *Krožni lok* (ang. *Arc*) 
  - Ustvari lok krožnice med dvema izbranima točkama z določenim središčem.
* - <img src="./geogebra/images/32px-Mode_circumcirclearc3.svg.png" class="inline" width="22px"> 
  - *Obodni lok* (ang. *Circumcircular arc*) 
  - Ustvari obodni krog trikotnika, ki gre skozi tri točke.
* - <img src="./geogebra/images/32px-Mode_circlesector3.svg.png" class="inline" width="22px">
  - *Krožni izsek* (ang. *Circular Sector*)
  - Ustvari krožni izsek z določenim središčem in dvema točkama na krožnici.
* -  <img src="./geogebra/images/32px-Mode_circumcirclesector3.svg.png" class="inline" width="22px">
  - *Obodni izek* (ang. *Circumcircular Sector*)
  - Ustvari vpisani krog trikotnika, ki se dotika vseh treh stranic.
:::
::::

::::{dropdown} <img src="./geogebra/images/32px-Mode_ellipse3.svg.png" class="inline" width="22px"> 
:::{list-table}  
:header-rows: 1  
* - Orodje  
  - 
  - Opis  
* - <img src="./geogebra/images/32px-Mode_ellipse3.svg.png" class="inline" width="22px">  
  - *Elipsa* (ang. *Ellipse*)  
  - Ustvari elipso iz dveh žarišč in točke.  
* - <img src="./geogebra/images/32px-Mode_hyperbola3.svg.png" class="inline" width="22px">  
  - *Hiperbola* (ang. *Hyperbola*)  
  - Ustvari hiperbolo.  
* - <img src="./geogebra/images/32px-Mode_parabola.svg.png" class="inline" width="22px">  
  - *Parabola* (ang. *Parabola*)  
  - Ustvari parabolo.  
* - <img src="./geogebra/images/32px-Mode_conic5.svg.png" class="inline" width="22px">  
  - *Konika skozi pet točk* (ang. (*Conic through Five Points*)  
  - Ustvari koniko, ki gre skozi pet izbranih točk.  
:::
::::

::::{dropdown} <img src="./geogebra/images/32px-Mode_angle.svg.png" class="inline" width="22px"> 
:::{list-table}  
:header-rows: 1  
* - Orodje 
  - 
  - Opis  
* - <img src="./geogebra/images/32px-Mode_angle.svg.png" class="inline" width="22px">  
  - *Kot* (ang. *Angle*)  
  - Ustvari in meri kot med dvema linijama.  
* - <img src="./geogebra/images/32px-Mode_anglefixed.svg.png" class="inline" width="22px">  
  - *Kot z dano velikostjo* (ang. *Angle with Given Size*)  
  - Ustvari kot določene mere.  
* - <img src="./geogebra/images/32px-Mode_distance.svg.png" class="inline" width="22px">  
  - *Razdalja / dolžina* (ang. *Distance or Length*)  
  - Izmeri razdaljo med točkama ali dolžino objekta.  
* - <img src="./geogebra/images/32px-Mode_area.svg.png" class="inline" width="22px">  
  - *Ploskev* (ang. (*Area*)  
  - Izmeri površino poligona ali zaprtih oblik.  
* - <img src="./geogebra/images/32px-Mode_slope.svg.png" class="inline" width="22px">  
  - *Naklon* (ang. *Slope*)  
  - Izračuna naklon premice.  
* - <img src="./geogebra/images/32px-Mode_createlist.svg.png" class="inline" width="22px">  
  - *Seznam* (ang. *List*)  
  - Ustvari seznam objektov.
* - <img src="./geogebra/images/32px-Mode_relation.svg.png" class="inline" width="22px">  
  - *Relacija* (ang. *Relation*)
  - Ustvari relacijo (enačbo) med objekti.
:::
::::


::::{dropdown} <img src="./geogebra/images/32px-Mode_mirroratline.svg.png" class="inline" width="22px">  
:::{list-table}  
:header-rows: 1  
* - Orodje  
  - 
  - Opis  
* - <img src="./geogebra/images/32px-Mode_mirroratline.svg.png" class="inline" width="22px">  
  - *Zrcali glede na premico* (ang. *Reflect about Line*) 
  - Ustvari sliko objekta zrcaljeno čez premico.  
* - <img src="./geogebra/images/32px-Mode_mirroratpoint.svg.png" class="inline" width="22px">  
  - *Zrcali glede na točko* (ang. *Reflect about Point*)
  - Ustvari sliko objekta zrcaljeno čez točko.  
* - <img src="./geogebra/images/32px-Mode_mirroratcircle.svg.png" class="inline" width="22px">  
  - *Zrcali glede na krog* (ang. *Reflect about Circle*)
  - Ustvari inverzijo objekta glede na krog.  
* - <img src="./geogebra/images/32px-Mode_rotatebyangle.svg.png" class="inline" width="22px">  
  - *Rotiraj okoli točke* (ang. *Rotate around Point*)
  - Rotira objekt za dan kot okoli neke točke.  
* - <img src="./geogebra/images/32px-Mode_translatebyvector.svg.png" class="inline" width="22px">  
  - *Translacija po vektorju* (ang. *Translate by Vector*)
  - Premakne objekt po določenem vektorju.  
* - <img src="./geogebra/images/32px-Mode_dilatefrompoint.svg.png" class="inline" width="22px">  
  - *Dilacija* (ang. *Dilate from Point*)
  - Skalira objekt od izbora točke z določenim faktorjem.  
:::
::::

::::{dropdown} <img src="./geogebra/images/32px-Mode_slider.svg.png" class="inline" width="22px">  
:::{list-table}  
:header-rows: 1  
* - Orodje  
  - 
  - Opis  
* - <img src="./geogebra/images/32px-Mode_slider.svg.png" class="inline" width="22px">  
  - *Drsnik* (ang. *Slider*)  
  - Ustvari parameter, kjer lahko animirate vrednosti.  
* - <img src="./geogebra/images/32px-Mode_text.svg.png" class="inline" width="22px">  
  - *Besedilo* (ang. *Text*)  
  - Vstavi besedilo v konstrukcijo.  
* - <img src="./geogebra/images/32px-Mode_buttonaction.svg.png" class="inline" width="22px">  
  - *Gumb* (ang. *Button*)  
  - Ustvari gumb za izvrševanje ukazov.  
* - <img src="./geogebra/images/32px-Mode_image.svg.png" class="inline" width="22px">  
  - *Slika* (ang. *Image*)  
  - Vstavi sliko iz naprave ali URL-ja.
* - <img src="./geogebra/images/32px-Mode_showcheckbox.svg.png" class="inline" width="22px">  
  - *Potrditveno polje* (ang. *Check Box*)  
  - Ustvari preklopno polje za vklop / izklop lastnosti.  
* - <img src="./geogebra/images/32px-Mode_textfieldaction.svg.png" class="inline" width="22px">  
  - *Vhodno polje* (ang. *Input Box*)  
  - Ustvari polje, kamor lahko ročno vnašate vrednosti.  

:::
::::


::::{dropdown} <img src="./geogebra/images/32px-Mode_translateview.svg.png" class="inline" width="22px">  
:::{list-table}  
:header-rows: 1  
* - Orodje 
  - 
  - Opis  
* - <img src="./geogebra/images/32px-Mode_translateview.svg.png" class="inline" width="22px"> 
  - *Premakni pogled* (ang. *Move View*)  
  - Premakne pogled grafičnega okna.
* - <img src="./geogebra/images/32px-Mode_zoomIn.svg.png" class="inline" width="22px">  
  - *Povečaj* (ang. *Zoom In*)  
  - Približa pogled.    
* - <img src="./geogebra/images/32px-Mode_zoomOut.svg.png" class="inline" width="22px">  
  - *Pomanjšaj* (ang. *Zoom Out*)  
  - Oddalji pogled.  
* - <img src="./geogebra/images/32px-Mode_showhideobject.svg.png" class="inline" width="22px">  
  - *Prikaži / skrij objekt* (ang. *Show/Hide Object*)  
  - Prikaže ali skrije izbrane objekte.   
* - <img src="./geogebra/images/32px-Mode_showhidelabel.svg.png" class="inline" width="22px">  
  - *Prikaži / skrij oznako* (ang. *Show/Hide Label*)  
  - Prikaže ali skrije napise/oznake objektov.    
* - <img src="./geogebra/images/32px-Mode_copyvisualstyle.svg.png" class="inline" width="22px">  
  - *Kopiraj slog* (ang. *Copy Visual Style*)  
  - Kopira grafične lastnosti iz enega objekta na drugega.   
* - <img src="./geogebra/images/24px-Notes-eraser.svg.png" class="inline" width="22px">  
  - *Izbriši* (ang. *Delete*)  
  - Izbriše izbran objekt. 
:::
::::

