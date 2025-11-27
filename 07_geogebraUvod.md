---
kernelspec:
  name: python
  display_name: Python 3
---

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
:label: ex_GeogebraAccount
Ustvarite račun Geogebra.
:::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

:::{solution} ex_GeogebraAccount
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
Geogebra se lahko uporablja v slovenskem jeziku, vmesnik je preveden, prav tako pa tudi ukazi, žal pa ni dokumentacije v slovenskem jeziku za ukaze (ki jih uporabljamo za ustvarjanje gradiva). Zaradi tega bomo vmesnik ohranili v angleščini, vendar upoštevajte, da če želite Geogebro uporabljati z otroki ali učenci, lahko jezik spremenite v meniju <img src="./geogebra/images/16px-Menu-options.svg.png" class="inline" width="22px">*Settings*.
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
* - <img src="./geogebra/images/32px-Mode_zoomin.svg.png" class="inline" width="22px">  
  - *Povečaj* (ang. *Zoom In*)  
  - Približa pogled.    
* - <img src="./geogebra/images/32px-Mode_zoomout.svg.png" class="inline" width="22px">  
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

Seveda, najlažji način za spoznavanje orodij je, da jih preizkusite sami v Geogebri!

:::{exercise}
:label: ex_GeogebraTools

1. Odprite Geogebro in ustvarite novo datoteko (verjetno bo to že privzeto narejeno).
2. Spremenite prikaz v <img src="./geogebra/images/16px-Menu_view_graphics.svg.png" class="inline" width="22px"> *Geometry*.
3. Z uporabo orodij <img src="./geogebra/images/32px-Mode_point.svg.png" class="inline" width="22px"> *Point*, <img src="./geogebra/images/32px-Mode_segment.svg.png" class="inline" width="22px"> *Segment*, <img src="./geogebra/images/32px-Mode_circle2.svg.png" class="inline" width="22px"> *Circle with Center and Point* in <img src="./geogebra/images/32px-Mode_polygon.svg.png" class="inline" width="22px"> *Polygon*, ustvarite naslednje objekte v Geogebri:

```{figure} ./geogebra/ex_GeogebraTools.png
:label: fig:ex_GeogebraTools
```
:::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

::::{solution} ex_GeogebraTools
:class: tip dropdown
1. Uporabite orodje <img src="./geogebra/images/32px-Mode_point.svg.png" class="inline" width="22px"> *Point* za ustvarjanje točk `A` in `B`.
2. Uporabite orodje <img src="./geogebra/images/32px-Mode_segment.svg.png" class="inline" width="22px"> *Segment* za ustvarjanje daljice `AB`.
3. Uporabite orodje <img src="./geogebra/images/32px-Mode_circle2.svg.png" class="inline" width="22px"> *Circle with Center and Point* za ustvarjanje krožnice s središčem v točki `C` in točko na krožnici `D`.
4. Uporabite orodje <img src="./geogebra/images/32px-Mode_polygon.svg.png" class="inline" width="22px"> *Polygon* za ustvarjanje trikotnika z oglišči `E`, `F` in `G`.

Lahko vidite vse korake spodaj v Geogebri:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/bmajgbvx/width/600/height/450/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/true/ctl/false", width="600px", height="450px", allowfullscreen=True)
:::
::::

## Vrstica za zamenjavo sloga

<img src="./geogebra/images/40px-Stylingbar_icon_graphics.svg.png" class="inline" width="22px"> *Vrstica za zamenjavo sloga* (ang. *Stylebar*) omogoča hitro spreminjanje grafičnih lastnosti izbranih objektov, kot so barva, debelina črte, slog črte in polnilo.
Ko izberete objekt v grafičnem oknu, se vrstica za zamenjavo sloga prikaže pod orodjarno in ponuja različne možnosti za prilagajanje videza izbranega objekta. 
Možnosti so odvisne od vrste izbranega objekta, če ni objekta izbranega, vrstica za zamenjavo sloga prikaže možnosti sloga za pogled. 

V vrstici za zamenjavo sloga se nahajajo samo osnovne možnosti, za dostop do naprednih možnosti sloga pa lahko kliknete na gumb <img src="./geogebra/images/32px-Settings.svg.png" class="inline" width="18px"> *Nastavitve* (ang. *Settings*), ki odpre pogovorno okno z več možnostmi za prilagajanje sloga izbranega objekta. Če ni izbranega objekta, gumb <img src="./geogebra/images/32px-Settings.svg.png" class="inline" width="18px"> *Nastavitve* odpre pogovorno okno z možnostmi za prilagajanje sloga pogleda.


:::{exercise}
:label: ex_Stylebar
1. V datoteki, ki ste jo ustvarili v vaji [Vaje %s](#ex_GeogebraTools), izberite daljico `AB` in zamenjate njeno barvo v rdečo, debelino črte na 4 in slog črte na črtkano.
2. Nato izberite točki `C` in `D` in zamenjate njun slog točke in barvo, tako da oboje točki sta zeleni in obliki točk sta križ <img src="./geogebra/images/16px-Stylingbar_point_cross.svg.png" class="inline" width="16px"> (to lahko delate v en korak z izbiro obeh točk hkrati).
3. Izberite trikotnik `EFG` in zamenjate barvo polnila na modro z 50% prosojnostjo.
4. Z uporabo gumba <img src="./geogebra/images/32px-Settings.svg.png" class="inline" width="18px"> *Nastavitve* dodajte *Napis* (ang. *Caption*) k dalici `AB`, ki naj bo "Daljica AB" in k točko `C`, ki naj bo "Središče krožnice". 
6. Z uporabo gumba <img src="./geogebra/images/32px-Mode_showhidelabel.svg.png" class="inline" width="18px"> *Prikaži / skrij oznako* (ang. *Show/Hide Label*) prikažite napise, ki ste jih dodali v prejšnjem koraku; skrijte vse druge oznake.
5. Prav tako uporabite gumb <img src="./geogebra/images/32px-Settings.svg.png" class="inline" width="18px"> *Nastavitve* za spreminjanje sloga pogleda, tako da so osi $x$ in $y$ prikazane z krepkim črto in zeleno barvo.
6. Z uporaba orodja <img src="./geogebra/images/32px-Mode_move.svg.png" class="inline" width="18px"> *Move* premaknite vse objekte, tako da bo daljica čim bolj vodoravna, krožnica ima središče na točki `(0,0)` in vse tri ogliščo trikotnika so v prvem kvadrantu.
:::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

::::{solution} ex_Stylebar
:class: tip dropdown
Na koncu, vaša konstrukcija naj izgleda nekako takole:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/ajgm7nav/width/600/height/600/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/true/rc/false/ld/false/sdz/true/ctl/false", width="600px", height="600px", allowfullscreen=True)
:::
::::

## Ukaze

GeoGebra poleg grafičnih orodij ponuja tudi algebrske vnose in ukaze. Vsako orodje ima ustrezen ukaz, zato ga je mogoče uporabljati brez miške.

:::{tip} Nasvet
Dokumentacija za ukaze je v angleščini, zato je priporočljivo, da imate ukaze uporabite v angleščini. 
Več o ukazih in njihovi uporabi najdete v [dokumentaciji Geogebre](https://geogebra.github.io/docs/manual/en/).
:::

:::{note} Opomba
Vsaka orodoja ima svoj ukaz, obratno pa ne velja, obstajajo več ukazov kot orodij. 
Večina uporabnikov Geogebra lahko brez težav dela z grafičnimi orodji, vendar moramo avtorji znati uporabljati ukaze. Tako bomo lahko delali hitreje in natančneje.
:::

Če hitro uporabimo ukaz, lahko ga vnesemo v _Vrstico za vnos_ (ang. _Input Bar_), ki se običajno nahaja na dnu zaslona. Alternativno, lahko ukaze vnesemo tudi neposredno v grafično okno ali v <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px"> _Algebrsko okno_ (ang. _Algebra View_). Oboje lahko najdemo v meni ju <img src="./geogebra/images/32px-Menu-view.svg.png" class="inline" width="22px"> _Views_.

Naljažje način za spoznavanje ukazov je, da jih preizkusite sami v Geogebri!

::::{exercise}
:label: ex_GeogebraUkazi-1

Sledite korake spodaj za ustvarjanje trikotnika v Geogebri.

1. Odprite Geogebro in ustvarite novo datoteko (verjetno bo to že privzeto narejeno).
2. Izberite prikaz v <img src="./geogebra/images/16px-Menu_view_graphics.svg.png" class="inline" width="22px"> *Geometry*.
3. Odprite *Input bar* (če ni že odprta) iz menija <img src="./geogebra/images/32px-Menu-view.svg.png" class="inline" width="22px"> *Views*.
--- 
Namesto prvih treh korakov lahko poskusite s konstrukcijo tukaj:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/s57srg3g/width/500/height/500/border/888888/sfsb/true/smb/true/stb/true/stbh/false/ai/true/asb/false/sri/false/rc/true/ld/true/sdz/true/ctl/false/szb/true", width="500px", height="500px", allowfullscreen=True)
:::

4. Vnosite `(0,0)` v vrstico za vnos in pritisnite {kbd}`Enter` za ustvarjanje točke $A$. Upoštevajte, da ime točke samodejno dodeli Geogebra.
5. Vnosite `C=(4,0)` v vrstico za vnos in pritisnite {kbd}`Enter` za ustvarjanje točke $C$. To je alternativni način za ustvarjanje točke z določenim imenom.
6. Vnosite niz `Cir` v vrstico za vnos in opazujte, kako se prikaže seznam ukazov, ki se začnejo z `Cir`. Izberite ukaz `Circle( <Point>, <Point> )` s seznama (lahko uporabite puščične tipke in {kbd}`Enter`. V vrstico za vnos se bo vnesel ukaz `Circle( <Point>, <Point> )` (prva beseda `<Point`> bo označena).
7. Napišite `A` namesto `<Point>` (pritisnite {kbd}`Tab` za samodejno dokončanje) in `C` namesto drugega `<Point>`, tako da bo ukaz videti takole: `Circle( A, C )`. Pritisnite {kbd}`Enter` za ustvarjanje krožnice s središčem v točki $A$ in polmerom $AC$.
8. Vnosite ukaz `d=Circle(C,A)` v vrstico za vnos in pritisnite {kbd}`Enter` za ustvarjanje krožnice s središčem v točki $C$ in polmerom $CA$. 
9. Opazujte, kako je krožnica samodejno poimenovana `d`; za to, uporabite <img src="./geogebra/images/40px-Stylingbar_icon_graphics.svg.png" class="inline" width="22px">_Stylebar_ za oznaki krožnic, da prikažete imeni. Spremenite slog krožnic, tako da bo oboje črtkane.
10. Z ukazom `Intersect(c,d)` ustvarite točki $B$ in $D$, ki je presečišče krožnic `c` in `d`.
11. Uporabite ukaz `t=Polygon(A,C,B)` za ustvarjanje trikotnika z oglišči $A$, $C$ in $B$.
12. Uporabite ukaz `InteriorAngles(t)` za prikaz notranjih kotov trikotnika $t$.
13. Z uporabo orodje <img src="./geogebra/images/32px-Mode_distance.svg.png" class="inline" width="22px"> *Distance or Length* izmerite dolžine stranice trikotnika $AB$. Za to, kliknite na orodje in nato kliknite na točko $A$ in torej na točko $B$. 
14. Uporabite orodje <img src="./geogebra/images/32px-Mode_move.svg.png" class="inline" width="22px"> *Move* za premijanje besedila z dolžinami stranica trikotnika, tako da vse je jasno vidno.
---
15. Dvakrat kliknite na besedilo, ki prikazuje dolžino AC, s čimer se odpre okno za urejanje besedila. Prikaže se nekaj podobnega kot `AC=distanceAC`. Kliknite na {kbd}`> Advanced`, uredite besedilo tako, da je zdaj `\operatorname{d}(A,C)=f` (**uredite, ne izbrizite**). Če LaTeX formule ne prikaže, kliknite na gumb {kbd}`LaTeX formula` in nato na {kbd}`Serif` (gumba so v zgornjem delu okna). V tab {kbd}`Preview` lahko vidite, kako bo besedilo videti, mora biti nekaj podobnega kot $\operatorname{d}(A,C)=4$. Kliknite na {kbd}`OK`, da shranite spremembe.
16. Ponovite prejšnji korak za dolžino stranice $BC$, vendar tokrat prikaze $\operatorname{d}(B,C)=4$ v besedilu. 
---
17. Ponovite korake 13-15 za dolžino stranice $
AB. Upoštevajte, da ni mogoče premakniti besedila tako, da se ne prekriva s sliko. Da bi to popravili, odprite okno za urejane nastavitve (<img src="./geogebra/images/16px-Menu-options.svg.png" class="inline" width="22px">*Settings*), pojdite na tab {kbd}`Position` in spremenite vrednosti v polji `Starting point` iz `Midpoint(A,B)` na `Midpoint(A,B)+(-1,0)`. Zaprite okno in premikanje besedilo, da bo vse jasno vidno.

::::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

::::{solution} ex_GeogebraUkazi-1
:class: tip dropdown
Na koncu, vaša konstrukcija naj izgleda nekako takole:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/qjmkhkwg/width/900/height/600/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/true/rc/false/ld/false/sdz/false/ctl/false", width="580px", height="600px", allowfullscreen=True)
:::
::::

:::{tip} Nasvet
Ko uporabite ukazi v Geogebri, je pomembno, da 
upoštevate naslednje nasvete:
- Točke so definirane z velikimi črkami (npr. A, B, C), medtem ko so premice, daljice in krožnice definirane z malimi črkami (npr. a, b, c).
- Pri vnosu koordinat točk uporabite oklepaje in vejice, npr. (2,3) za točko z $x$ koordinato 2 in $y$ koordinato 3.
- Ukaz $v=(1,2)$ ne definira točke, ampak vektor z komponentama 1 in 2.
- Uporabite {kbd}`Tab` za samodejno dokončanje imen ukazov in objektov.
- Uporabite {kbd}`↑` in {kbd}`↓` za navigacijo po zgodovini ukazov v vrstici za vnos.
- Z gumbom <img src="./geogebra/images/24px-Menu-help.svg.png" class="inline" width="18px"> *Help* (sl. *Pomoč*) (na desno od vrstice za vnos) lahko dostopate do dokumentacije Geogebre za ukaze.
:::

V [Vaji %s](#ex_GeogebraUkazi-1) ste se naučili
- Ustvariti geometrijske objekte z uporabo ukazov v vrstici za vnos.
- Meriti kotov in dolžin in z uporabo orodje.
- Prilagoditi besedilo z uporabo LaTeX formul.
- Nastavitev `Starting point` za pozicioniranje besedila.

---
Geogebra nam omogoča vizualizacijo osnovnih geometrijskih konstrukcij in iskanje vzorcev v njih. 
Na primer, pri konstrukciji v [Vaji %s](#ex_GeogebraUkazi-1) lahko opazimo, da je trikotnik $ABC$ vedno enakostraničen, ne samo za izbiro točko $A=(0,0)$ in $C=(4,0)$, ampak za katerokoli izbiro točk $A$ in $C$. 
To lahko vidimo, če povlečemo točki $A$ in $C$ z orodjem <img src="./geogebra/images/32px-Mode_move.svg.png" class="inline" width="18px"> *Move*. 
Opazimo da so dolžini stranici $AB$, $BC$ in $CA$ vedno enaki.
V Geogebri je to znano kot **test vlečenja** (ang. *dragging test*), ki nam pomaga pri odkrivanju in dokazovanju geometrijskih lastnosti.

::::{exercise}
:label: ex_dokazTrikotnik
1. Uporabite orodje <img src="./geogebra/images/32px-Mode_move.svg.png" class="inline" width="18px"> *Move* za premikanje točk $A$ in $C$ v konstrukciji iz [Vaje %s](#ex_GeogebraUkazi-1).
2. Opazujte dolžini stranici trikonike ter preverite, ali ostajata vedno enaki.
3. Na podlagi vaših opažanj, zapišite kratko izjavo, ki dokazuje, da je trikotnik $ABC$ vedno enakokrak.

Lahko poskusite s konstrukcijo tukaj:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/qjmkhkwg/width/900/height/600/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/true/rc/false/ld/false/sdz/false/ctl/true", width="560px", height="400px", allowfullscreen=True)
:::

::::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

:::{solution} ex_dokazTrikotnik
:class: tip dropdown

**Dokaz.** Dolžina strani $AB$ je enaka dolžini strani $AC$ ker sta točki $C$ in $B$ v krožnici s središčem v točki $A$. 
Podobno, dolžina strani $BC$ je enaka dolžini strani $AB$ ker sta točki $A$ in $B$ v krožnici s središčem v točki $C$.
Tako so dolžine strani $AB$, $AC$ in $BC$ vedno enake.
:::

V prešnji konstrukciji smo uporabili **test vlečenja** (ang. *dragging test*), ki nam pomaga pri odkrivanju in dokazovanju, da je trikotnik $ABC$ vedno enakostraničen.
S testom vlečenja lahko tudi vidimo, da so vsi koti v enakostraničnem trikotniku enaki in merijo $60^\circ$. To sledi iz dejstva, da je vsota notranjih kotov v trikotniku vedno $180^\circ$ in da so vsi trikotniki enakostranični.

::::{exercise}
:label: ex_TrikotnikKot
Vstvarite novo konstrukcijo v Geogebri, ki prikazuje, da vsota notranjih kotov v trikotniku vedno meri $180^\circ$.
::::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

::::{solution} ex_TrikotnikKot
:class: tip dropdown
1. Ustvarite tri točke `A`, `B` in `C` z orodjem <img src="./geogebra/images/32px-Mode_point.svg.png" class="inline" width="22px"> *Point*.
2. Ustvarite daljice `AB`, `BC` in `CA` z orodjem <img src="./geogebra/images/32px-Mode_segment.svg.png" class="inline" width="22px"> *Segment* ali z uporabo ukaza `Segment(A,B)`, `Segment(B,C)` in `Segment(C,A)`.
3. Ukaz `Angle(B,A,C)` uporabite za prikaz kota pri točki `A`; `Angle(A,B,C)` za prikaz kota pri točki `B` in `Angle(A,C,B)` za prikaz kota pri točki `C`.
4. Uporabite ukaz `ParallelLine(C,AB)` za ustvarjanje premice, ki gre skozi točko `C` in je vzporedna z daljico `AB`. 
5. Podobno vstvarite premico, ki gre skozi točko `A` in je vzporedna z daljico `BC` in premico, ki gre skozi točko `B` in je vzporedna z daljico `CA`.
6. Uporabite orodje <img src="./geogebra/images/32px-Mode_intersect.svg.png" class="inline" width="22px"> *Intersect * za ustvarjanje točk presečišča vsakih parov teh premic.
7. Uporabite ukaz `Angle` za prikaz kotov, ki jih tvorijo te premice z daljicami trikotnika. Za to, uporabite točke, ki ste jih ustvarili v prejšnjem koraku.
8. Z uporabo vrstice za zamenjavo sloga prilagodite slog kotov, tako da bodo vsi koti, ki so enaki enake barve.

Na koncu, vaša konstrukcija naj izgleda nekako takole:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/kj3d2jem/width/580/height/400/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/true/rc/true/ld/false/sdz/true/ctl/false", width="560px", height="600px", allowfullscreen=True)
:::

::::

## Algebrsko okno, proste točke vs. odvisne točke in kontrolni okvirček

Vrstica za vnos ni edini način za interakcijo z Geogebro z uporabo ukazov.
Lahko uporabimo tudi <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px"> *Algebrsko okno* (ang. *Algebra View*), ki prikazuje seznam vseh objektov v konstrukciji skupaj z njihovimi lastnostmi in vrednostmi.

:::{exercise}
:label: ex_pentagram
1. Ustvarite novo konstrukcijo v Geogebri.
2. Odprite <img src="./geogebra/images/32px-Menu-view.svg.png" class="inline" width="22px"> *Views* in izberite <img src="./geogebra/images/40px-Menu_view_algebra.svg.png" class="inline" width="22px"> *Algebra View*.
3. Z uporabo orodija <img src="./geogebra/images/32px-Mode_point.svg.png" class="inline" width="22px"> *Point* ustvarite točki `A` in `B`.
4. Vnosite ukaz `p=Polygon(A,B,5)` v vrstico za vnos in pritisnite {kbd}`Enter` za ustvarjanje pravilnega petkotnika `p` z oglišči `A` in `B`.
5. Vstvarite vse diagonale petkotnika, zato v vrstico za vnos vnesite ukazi:
   - `d1=Segment(A,C)`
   - `d2=Segment(C,E)`
   - `d3=Segment(E,B)`
   - `d4=Segment(B,D)`
   - `d5=Segment(D,A)`
6. Z uporabo orodj ali ukazov ustvarite presečišča diagonali in jih poimenujte `P`, `Q`, `R`, `S` in `T`.
7. Z uporabo ukaza `Polygon` ustvarite zvezdo določeno s točkami `P`, `Q`, `R`, `S`,`T` in oglišci petkotnika.
8. Skrijte petkotnik in diagonale z uporabo orodja <img src="./geogebra/images/32px-Mode_showhideobject.svg.png" class="inline" width="22px"> *Show/Hide Object* ali s klikom na krog levo od objektov v algebrskem oknu.
:::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

::::{solution} ex_pentagram
:class: tip dropdown
Na koncu, vaša konstrukcija naj izgleda nekako takole:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/keuambxs/width/1271/height/679/border/888888/sfsb/true/smb/true/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/false/ctl/false", width="560px", height="600px", allowfullscreen=True)
:::

::::

Upoštevajte, da so točke `A` in `B` **proste točke** (ang. *free points*), ker jih lahko premikamo kjerkoli v grafičnem oknu.
Vse ostale točke v konstrukciji so **odvisne točke** (ang. *dependent points*), ker so določene z drugimi objekti v konstrukciji in se premikajo glede na spremembe teh objektov.
Proste točke so običajno modre barve, medtem ko so odvisne točke sive barve. 
Seveda, to lahko spremenimo z uporabo vrstice za zamenjavo sloga ali v nastavitvah objekta, in torej barva ni zanesljiv indikator vrste točke.
V algebrskem oknu lahko vidimo katere objekte so proste in katere odvisne, saj so uporabimo gump *Sort by* in torej *Dependency* v vrstico za zamenjavo sloga algebrskega okna.

---

Kot smo videli, lahko uporabimo orodje <img src="./geogebra/images/32px-Mode_showhideobject.svg.png" class="inline" width="22px"> *Show/Hide Object* za prikaz ali skrivanje objektov v grafičnem oknu. 
To lahko storimo tudi v algebrskem oknu, kjer lahko kliknemo na krog levo od imena objekta za prikaz ali skrivanje objekta.
Poleg tega, lahko uporabimo tudi kontrolni okvirček (ang. *checkbox*), ki ga lahko ustvarimo z orodjem <img src="./geogebra/images/32px-Mode_showcheckbox.svg.png" class="inline" width="22px"> *Check Box* ali z ukazom `CheckBox()`.
Kontrolni okvirček vstavirte *Check Box* v grafično okno in booleansko vrednost v algebrskem oknu.
Nato lahko uporabimo to vrednost za nadzor vidljivosti drugih objektov v konstrukciji.


:::{exercise}
:label: ex_checkbox
1. V konstrukciji iz [Vaje %s](#ex_pentagram) ustvarite kontrolni okvirček, za kateri vnesete besedilo "Prikaži petkotnik in diagonale".
2. Uporabite ta kontrolni okvirček za nadzor vidljivosti petkotnika in njegovih diagonal.
:::

```{margin}
[Seznam vaj](#07_geogebraUvod_vaje)
```

::::{solution} ex_checkbox
:class: tip dropdown
1. Lahko uporabite ukaz `cb=CheckBox("Prikaži petkotnik in diagonale", p)` v vrstico za vnos za ustvarjanje kontrolnega okvirčka.
2. Upoštevajte, da je drugi argument ukaza `CheckBox` objekt ali seznam objektov, katerih vidljivost bo nadzorovana s kontrolnim okvirčkom. V tem primeru je to petkotnik `p` ampak diagonale niso vključene.
3. Če želite vključiti diagonale, odprite okno <img src="./geogebra/images/16px-Menu-options.svg.png" class="inline" width="22px">_Settings_) za vzake objekte, ki jih želite nadzorovati in pojdite na tab {kbd}`Advanced`. V polje {kbd}`Condition to show object` vnesite `cb` (ime kontrolnega okvirčka) in zaprite okno.

Na koncu, vaša konstrukcija naj izgleda nekako takole:

:::{code-cell} python
:tags: remove-input
IFrame("https://www.geogebra.org/material/iframe/id/rwcmkgfe/width/600/height/582/border/888888/sfsb/true/smb/false/stb/false/stbh/false/ai/false/asb/false/sri/false/rc/false/ld/false/sdz/true/ctl/false", width="570px", height="600px", allowfullscreen=True)
:::

::::

## Izvoz konstrukcij kot slike.

Lahko izvozimo naše konstrukcije iz Geogebre kot slike v različnih formatih, kot so `PNG`, `SVG` ali `PDF`.
Za izvoz konstrukcije kot slike, sledite tem korakom:
1. Pojdite na meni <img src="./geogebra/images/16px-Menu-file.svg.png" class="inline" width="22px"> *File* in izberite <img src="./geogebra/images/24px-Menu-download.svg.png" class="inline" width="22px"> *Download as...*.
2. V pogovornem oknu izberite želeni format slike (npr. `.png`, `.svg` ali `.pdf`).
3. Posebni format je `PGF/TikZ`, ki omogoča izvoz konstrukcije kot kode, ki jo lahko uporabimo v LaTeX dokumentih.




(07_geogebraUvod_vaje)=
## Vaje


- [Vaje %s](#ex_GeogebraAccount): Ustvarjanje računa Geogebra.
- [Vaje %s](#ex_GeogebraTools): Vaje za spoznavanje orodij Geogebre.
- [Vaje %s](#ex_Stylebar): Vaje za uporabo vrstice za zamenjavo sloga.
- [Vaje %s](#ex_GeogebraUkazi-1): Vaje za spoznavanje ukazov Geogebre.
- [Vaje %s](#ex_dokazTrikotnik): Vaje za dokazovanje lastnosti trikotnika z uporabo Geogebre.
- [Vaje %s](#ex_TrikotnikKot): Vaje za dokazovanje vsote notranjih kotov v trikotniku z uporabo Geogebre.
- [Vaje %s](#ex_pentagram): Vaje za ustvarjanje petkotnika in zvezde z uporabo Geogebre.
- [Vaje %s](#ex_checkbox): Vaje za uporabo kontrolnega okvirčka za nadzor vidljivosti objektov v Geogebri.


:::{exercise}
:label: ex_anglesCircle
Ustvarite konstrukcijo v Geogebri, kjer raziskujete razmerje med kotom $\alpha$ in kotom $\beta$, ki sta opisana v [Sliki %s](#fig:angles_circle). V tej konstrukciji je točka $A$ središče krožnice. 

Ugotovite in dokažite povezavo med tema kotoma z uporabo Geogebre in testa vlečenja.

```{figure} ./geogebra/ex_anglesCircle.png
:label: fig:angles_circle
:align: center
:width: 500px

Koti $\alpha$ in $\beta$ v krožnici.
```

:::
:::{exercise}
:label: ex_TriangleCenters
Ustvarite konstrukcijo v Geogebri, ki prikazuje ortocenter, težišče in središče krožnice opisanega trikotnika. 
:::

:::{exercise}
:label: ex_midPointsCuadrilateral
Ustvarite konstrukcijo v Geogebri z naslednjimi elementi:
1. Štirikotnik $\square ABCD$.
2. Sredine stranic $E$, $F$, $G$ in $H$.
3. Štirikotnik $\square EFGH$.
4. Ne glede na točke $A$, $B$, $C$ in $D$, štirikotnik $\square EFGH$ ima vedno posebno lastnost. Ugotovite katero in dokažite z uporabo Geogebre in testa vlečenja.
:::