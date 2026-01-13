---
kernelspec:
  name: sagemath 
  display_name:  SageMath
---

(14_sage_analiza)=
# Analiza in SageMath

## Funkcije

:::{warning} Opozorilo!
SageMath je zelo podoben kot Python. V Pythonu (in v SageMathu) beseda **funkcije** je pogosto uporabljena za deli kode, ki jih lahko pokličemo z imenom in argumenti. Uporabljamo beseda `def` za definiranje teh funkcij.

V tem razdelku pa bomo govorili o **matematičnih funkcijah**, kot so $f(x) = x^2$ ali $g(x) = \sin(x)$. Te funkcije lahko definiramo in analiziramo v SageMathu.
:::

V Sage funkcije definiramo z naslednjo sintakso:

:::{code-cell} python
f(x)=(2*x+1)^3 # Pazite * za množenje
latex(f)
:::

Koda zgoraj definira funkcijo $$f:  x \ {\mapsto}\ {\left(2 \, x + 1\right)}^{3}.
$$ 

Funkcijo lahko nato pokličemo z določenimi vrednostmi:

:::{code-cell} python
f(2) # Vrednost funkcije pri x=2
::: 

Seveda, $$ f(2) = (2*2 + 1)^3 = 5^3 = 125. $$

Z metodo `expand()` lahko izraz funkcije razširimo:

:::{code-cell} python
f.expand()
:::

Obratno, z metodo `simplify_full()` lahko izraz funkcije poenostavimo:

:::{code-cell} python
g(x) = (x^2 - 1)/(x - 1)
g.simplify_full()
:::

Če imamo funkcijo definirano po delih, lahko uporabimo metodo `piecewise()`, npr. za funkcijo

$$h(x) = \begin{cases} x^2, & \text{če } x < 0 \\ x + 1, & \text{če } x \geq 0 \end{cases}$$

uporabimo:

:::{code-cell} python
h = piecewise([((x<0), x^2), ((x>=0), x + 1)])
h(-2), h(0), h(3)
:::

$$\begin{aligned} h(-2) & = (-2)^2 = 4, \\ h(0) & = 0 + 1 = 1, \\ h(3) & = 3 + 1 = 4. \end{aligned}$$

## Risanje grafov funkcij

Graf funkcije $f$ s spremenljivko $x$ v intervalu $[a, b]$ narišemo z ukazom `plot(f, x, a, b)`:

:::{code-cell} python
f(x) = x^2
plot(f,x,-2,2)
:::

Velikost grafa lahko prilagodimo z argumentoma `figsize=<velikost>`, npr. `figsize=4` za velikost 4x4 palcev:

:::{code-cell} python
plot(f,x,-2,2, figsize=4)
:::

Privzetne vrednosti lahko globalno nastavimo z ukazom:

:::{code-cell} python
sage.plot.graphics.Graphics.SHOW_OPTIONS['figsize']=5
:::

---

Grafa dveh ali več funkcij lahko narišemo skupaj, če namesto ene funkcije podamo seznam funkcij:

:::{code-cell} python
plot([f, cos(4*x)],x,-2,2)
:::

Drugi način je uporaba operatorja `+` za seštevanje grafov. S tem pristopom lahko neodvisno nastavljamo lastnosti posameznih grafov:

:::{code-cell} python
d1=plot(f,x,-2,2, color= 'green', legend_label='$f$')
d2=plot(cos(4*x),x,-2,2, 
    thickness=3, linestyle='--', 
    legend_label='$\\cos(x)$' ) # pazite dvojni poševnici za LaTeX
d1+d2
:::

Vsak grafični objekt v SageMath ima metodo `show()`, ki prikaže graf. Z njo lahko tudi nastavimo lastnosti grafa, kot so naslov, oznake osi in mreža:

:::{code-cell} python
d2.show(
title='Graf funkcije $\\cos(x)$', #naslov
fontsize=12, 
gridlines='mayor', #mrežne črte,
)
:::

Pazite, da metoda `show()` ne spremeni samega grafičnega objekta, ampak le način njegovega prikaza, to pomeni, da lahko večkrat pokličemo `show()` z različnimi nastavitvami:

:::{code-cell} python
d2.show(title='Prvi prikaz')
d2.show(title='Drugi prikaz z mrežo', gridlines=True)
:::

Ampak, če želimo trajno spremeniti lastnosti grafa, moramo to narediti pri ustvarjanju grafičnega objekta:

:::{code-cell} python
d2=plot(cos(4*x),x,-2,2, 
    axes_labels=['$s$','$m$'],
    #oznake osi ['os x','os y']
    color='red',
    figsize=5,
    )
d2.show()
:::

:::{code-cell} python
d2.show(axes_labels=['$x$','$y$'])
:::

:::{code-cell} python
d2
:::

--- 


Naj bosta funkciji $f$ in $g$ s predpisom
$$f(x)=\frac{2x^2 +x +2}{x+1} \qquad g(x)=\frac{\
cos(2x)}{2} $$
kaj se zgodi, če želimo narisati njuna grafa?

:::{code-cell} python
f=(2*x^2+x+2)/(x+1)
g=(cos(2*x))/2
plot([f,g], x, -5,5)
:::

Funkcija $g$ je prikazna slabo, ker je njegovo območje interval $[-1,1]$, medtem ko je območje funkcije $f$ veliko večje $(-\infty, \infty)$. Rešitev je, da omejimo območje grafa z argumentom `ymin` in `ymax`:

:::{code-cell} python
plot(((2*x^2+x+2)/(x+1),(cos(2*x))/2),x,-5,5,ymin=-10,
ymax=6)
:::

---

Z ukazom `implici_plot()`  lahko narišemo grafe, ki jih določajo implicitne enačbe, npr. krog s središčem v izhodišču in polmerom $2$:


:::{code-cell} python
x,y=var('x,y')
implicit_plot(x^2+y^2==4, (x, -3, 3), (y, -3,3))
:::

Polarne grafe lahko narišemo z ukazom `polar_plot()`. Za funkcijo $r(t)$ v polarnih koordinatah narišemo graf z ukazom `polar_plot(r,t, a, b, plot_points=M)`, kjer $t$ je kot v radianih, interval $[a,b]$ pa določa obseg kota. Parameter `plot_points=M` določa število točk, ki se uporabijo za risanje grafa (privzeta vrednost je 100):

Npr. naslednja koda izpiše družino krivulj, imenovanih krivulje vrnice, katerih enačbe so v obliko $r(t) = 1 + a \cos(kt)$:

:::{code-cell} python
t=var('t'); a=2; k=7/3
polar_plot(1+a*cos(k*t),t,0,k*6*pi,plot_points=4000)
:::

SageMath dejansko ne riše krivulj, temveč približke s črtami, argument `plot_points` določa, kako dober je približek.

:::{code-cell} python
polar_plot(1+a*cos(k*t),t,0,k*6*pi,plot_points=20)
:::

:::{exercise}
:label: ex-plot
1. Narišite graf $f(x)= \sin(2x)$ vzdolž intervala $[-3,3]$
2. Narišite grafe naslednjih funkcij. Spremenite lastnosti grafov, da bo slika čim boljša.
  - $\frac{2x^2}{2-x^2}$
  - $2 \sin (x) + \cos(x)$
  - $x e^{x} + \ln(x)$
  - $\frac{2x^2}{x^2+2}$
3. Kako je videti graf, ki ga določa enačba $\frac{x^2}{2}+\frac{y^2}{6}=2$?
4. Narišite družino Pascalovih konhoidov za polarno enačbo $r(θ) = a+ cos (\theta)$, ko se parameter $a$ spreminja od $0$ do $2$ s korakom $0,1$.
:::




## Limite 

Če je $f$ funkcija  in $a$ točka, lahko izračunamo limitno vrednost funkcije $f$ v točki $a$ z ukazom `limit(f, x=a)`:

:::{code-cell} python
g(x) = x^2 * cos(2*x)
limit(g, x=2)
:::

Lahko uporabimo SageMath za izračun nekaterih vrednosti v okolic točke $a = 2$:

:::{code-cell} python
g(x)=x^2 * cos(2*x)
zacetek =float(2-1/10) # Začnemo v bližini 2
korak=float(1/100) # Počasi se približujemo 2
st_priblizkov= 9 # št. korakov, da se zelo približamo
for i in range(9): print(g(zacetek+i*korak))
:::

Z desni strani:

:::{code-cell} python
zacetek =2+1/10
for i in range(9): print(g(zacetek-i*korak))
:::

Izgleda, da bi morala biti limita okoli $-2.6$. To lahko preverimo s SageMathom:

:::{code-cell} python
l=limit(g,x=2)
print("l=",l)
print("ki je približno", l.n())
:::


Funkcija $g$ ni zelo zanimiva, ker je zvezna v točki $a=2$. To pomeni, da $$ \lim_{x\to 2} g(x) = g(2)$$.

:::{code-cell} python
bool(limit(g,x=2)==g(2))
:::

To laho vidimo tudi tako, da narišemo graf funkcije $g$ v okolici točke $2$:

:::{code-cell} python
plot(g,x,1.5,2.5,ymin=-3.5, ymax=1)
:::


Zdaj si oglejmo funkcijo $$h(x) = \frac{x^2 + x - 2}{x-4}.$$ Najdimo $$\lim_{x\to 4} h(x).$$

:::{code-cell} python
h(x)=(x^2 + x - 2)/ (x-4)
limit(h,x=4)
:::

Ko pa narišemo graf funkcije $h$ opazimo, da:

:::{code-cell} python
plot(h,x, 3,5,ymax=1000,ymin=-1000)
:::

$$\lim_{x\to 4 ^{-}} h(x) = - \infty \quad \text{ in } \quad \lim_{x\to 4 ^{+}} h(x) = \infty$$

To pomeni, da limita $$\lim_{x\to 4} h(x)$$ ne obstaja. Ugotovimo lahko tudi s SageMathom, da $$\lim_{x\to 4 ^{-}} h(x) = - \infty \quad \text{ in } \quad \lim_{x\to 4 ^{+}} h(x) = \infty$$ s ukaza:

:::{code-cell} python
limit(h,x=4, dir='left') #ali dir='minus'
:::

:::{code-cell} python
limit(h,x=4, dir='plus') #ali dir='right'
:::

:::{exercise}
:label:ex-Limite

1. Uporabite SageMath za izračun naslednjih limite. Če limita ne obstaja, izračunajte stranski limiti. 
Za preverjanje odgovora narišite grafe okoli ustreznih točk.
- $$\lim_{x\to 2} \frac{x^2 +2x -8}{x-2}$$
- $$\lim_{x\to 0} \frac{\tan(x)}{|x|}$$
- $$\lim_{x\to (\pi/2)} \sec(x)$$

2. Naj bo $g(x)=\frac{\cos(x)}{x}$. Izračunajte limito $\lim_{x\to \infty} g(x)$.
- Razmislimo o funkcijah $f(x) = \frac{1}{x}$ in $h(x) = \frac{-1}{x}$.
- Opazimo, da če je $x >0$, torej je $h(x) \leq g(x) \leq f(x)$. Zakaj?
- Kakšne sta vrednosti $\lim_{x\to \infty} f(x)$ in $\lim_{x\to \infty} h(x)$?
- Kaj slednje pove o $\lim_{x\to \infty} g(x)$ ?
- Narišite graf, ki pikazuje zgoraj opisano situacijo.
:::



## Odvod

Odvodi lahko izračunamo z ukazom `diff(f, x)`, kjer je $f$ funkcija in $x$ spremenljivka:

:::{code-cell} python
f(x) = x*exp(x)
fp=diff(f,x)
fp
:::

Ukaz `derivative()` deluje enako:

:::{code-cell} python
derivative(f,x)
:::

Prvi argument je funkcija, ki jo želimo odvesti, drugi argument pa spremenljivka glede na katero odvajamo.

:::{code-cell} python
y=var('y')
p=(x+1)*(y^2+y+1); 
print(p)
print(derivative(p,x)); 
print(derivative(p,y))
:::

Ukaza `diff()` in `derivative()` vrne drugo funkcijo, ki jo lahko ovrednotimo kot katerokoli drugo funkcijo.

:::{code-cell} python
print(fp)
fp(2)
:::

:::{code-cell} python
h(x) = (x^2 + x - 2)/(x-4)
hp = derivative(h,x)
hp
:::

Uporabimo lahko ukaz `solve()` za iskanje kritičnih točk funkcije, torej točk, kjer je odvod enak nič:

:::{code-cell} python
solve( fp(x) == 0,x)
:::

To lahko preverimo z risanjem grafa funkcije in njenega odvoda:

:::{code-cell} python
g1=plot(f,x,-2,1 )
g2=plot(fp,x,-2,1, color='red' )
g1+g2
:::

Za funkcijo $h$:

:::{code-cell} python
solve( hp(x) == 0, x)
:::

:::{code-cell} python
plot(h,x,-3,10,ymin=-50, ymax=50)
:::

Sestavljamo tangente na naše funkcije v točki $(a, f(a))$. Tangentna črta funkcije $f(a)$ je predstavljena z enačbo:
$$y = f(a) + f'(a)(x - a).$$

:::{code-cell} python
T_f = fp(0)*( x - 0 ) + f(0)
:::

:::{code-cell} python
p1=plot(f,x,-1,1,ymin=-2, ymax=2,color='blue')
p2=plot(T_f,x,-1,1,ymin=-2, ymax=2, color='green' )
p3=point([0,f(0)], color='red', size=30)
p1+p2+p3
:::


:::{exercise}
:label: ex-odvodi
Za funkcije $f$, $g$ in $h$, opisane spodaj, izračunajte
- odvod
- kritične točke (če obstajajo)
- tangentno črto v točki (po lastni izbiri)
- nariši graf in tangentno črto

$$ f(x)= x^{2} e^{3x} \cos(2x) \qquad g(x)=\frac{x^2+1}{x-2} \qquad h(x) = x \cos(x) $$
:::



## Integrali

SageMath lahko izračuna določene in nedoločene integrale.

Najprej se bomo osredotočili na nedoločeni integral, ki ga izračunamo z ukazom `integral()`, ki ima podobne argumente kot ukaz 'derivative()'.  

:::{code-cell} python
f(x) = x*exp(x)
I_f= integral(f,x) #nedoločena integrala
I_f
:::

:::{code-cell} python
h(x) = (x^2 + x - 2)/(x-4)
I_h= integral(h,x); I_h
:::

Rezultat je funkcija, ki je le ena od _primitivnih funkcij_. Ostale se razlikujejo po konstanti. Da je to pravilno, lahko preverimo tako, da izračunamo odvod. 

:::{code-cell} python
print(f); derivative(I_f,x)
:::

:::{code-cell} python
print(h); derivative(I_h,x)
:::

Nista videti povsem enaka, vendar lahko to preverimo z malo algebre... ali...

:::{code-cell} python
print(  bool(f==derivative(I_f,x)),
        bool(h==derivative(I_h,x))  )  
::: 

Obstaja nekaj funkcij, ki so videti nedolžne, vendar njihovi primitivi nimajo _zaprte oblike_.

Klasični primer je funkcija $e^{-x^2}$, ki je temeljna v verjetnosti.

:::{code-cell} python
plot(exp(-x^(2)),x,-pi,pi, figsize=3)
:::

:::{code-cell} python
integral(exp(-x^(2)),x)
:::

Rezultat vključuje funkcijo $\operatorname{erf}(x)$, ki se sicer imenuje _funkcija napake_ (ang. _error function_),  ki nima preprostega izraza.

---

Za izračun določenega integrala moramo ukazu `integral()` podati integracijski limiti.

:::{code-cell} python
integral(f, x,0,1)
:::

:::{code-cell} python
integral(h, x,0,1)
:::

V vsakem primeru je rezultat  številko (po pričakovanjih).

Kot smo že omenili, bo SageMath vedno dajal prednost simboličnim izračunom, če želimo dobiti numerične približke, lahko uporabimo funkcijo `n()`.

:::{code-cell} python
n(integral(f, x,0,1))
:::

:::{code-cell} python
n(integral(h, x,0,1))
:::

Funkcija $e^{-x^2}$ je pomembna v verjetnosti, ker predstavlja gostoto normalne porazdelitve. Celoten integral od $-\infty$ do $\infty$  (ker je to celotna verjetnost). Preverimo to s SageMathom:

:::{code-cell} python
integral(exp(-x^(2)),x, -infinity, infinity)
:::

:::{code-cell} python
n(integral(exp(-x^(2)),x, -infinity, infinity))
:::

To je

$$ \int_{-\infty}^{\infty} e^{-x^2} \, dx = \sqrt{\pi} \approx 1.77245385090552. $$


:::{exercise}
:label:ex-integrali

S programom SageMath izračunajte naslednje integrale.

- $$\int \frac{x+1}{x^2+2x+1} dx $$
- $$\int_{-\pi/4}^{\pi/4} \sec(x) dx$$
- $$\int x e^{x^2} dx$$

:::



