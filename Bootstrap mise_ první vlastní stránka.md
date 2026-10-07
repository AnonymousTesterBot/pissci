# Bootstrap mise: první vlastní stránka

**Čas:** přibližně 60 minut  
**Technologie:** HTML + Bootstrap 5.3  
**Pravidlo dnešní práce:** bez vlastního CSS

## Co dnes vytvoříš?

Vytvoříš jednoduchou jednostránkovou prezentaci fiktivní akce.

Může to být například:

**festival • koncert • game jam • výstava • workshop • esport turnaj • design market**

Nebudeš začínat úplně od nuly. V první části dostaneš více podpory a vysvětlení. Postupně bude hotového kódu ubývat a některé věci už budeš hledat v dokumentaci sám.

Cílem není naučit se Bootstrap nazpaměť.

Cílem je pochopit, **jak s Bootstrapem pracovat a kde hledat řešení**.

---

# 1. Co vlastně Bootstrap dělá?

Bootstrap není nový programovací jazyk.

Pořád píšeme běžné HTML:

```html
<a href="#">Registrace</a>
```

Bootstrap nám k němu přidává velké množství připravených CSS tříd.

Například:

```html
<a href="#" class="btn btn-primary">
    Registrace
</a>
```

HTML říká:

> Toto je odkaz.

Třídy Bootstrapu říkají:

> Zobraz odkaz jako tlačítko a použij hlavní barevnou variantu.

---

## V Bootstrapu dnes narazíš hlavně na tři typy nástrojů

### Komponenty

Hotové části rozhraní, například:

```text
Navbar
Card
Button
Badge
```

### Layout

Řeší rozmístění prvků na stránce:

```text
container
row
col
```

### Utility

Malé pomocné třídy pro konkrétní úpravy:

```text
barvy
mezery
zarovnání
velikosti
stíny
zaoblení
```

Například:

```html
<div class="p-4 bg-dark text-white">
```

Nemusíš všechny názvy znát zpaměti.

Důležitější je začít přemýšlet:

> Potřebuji něco změnit. Má na to Bootstrap připravenou třídu?

---

# 2. Připrav projekt

Vytvoř soubor:

```text
index.html
```

Použij tento základ:

```html
<!doctype html>
<html lang="cs">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <title>Moje akce</title>

    <link
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css"
        rel="stylesheet">
</head>

<body>


    <script
        src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js">
    </script>

</body>

</html>
```

První odkaz připojuje Bootstrap CSS.

Díky němu budou fungovat například třídy:

```text
btn
container
card
bg-dark
```

Na konci stránky připojujeme také Bootstrap JavaScript.

Ten potřebují některé interaktivní komponenty. Dnes ho využije například rozbalovací navigace.

[Bootstrap dokumentace → Quick start](https://getbootstrap.com/docs/5.3/getting-started/introduction/?utm_source=chatgpt.com#quick-start)

---

# 3. Navigaci dnes dostaneš téměř hotovou

Navbar patří mezi složitější Bootstrap komponenty, protože kombinuje HTML, responzivní chování a JavaScript.

Dnes ji proto nebudeme stavět od začátku.

Jako první prvek do `<body>` vlož:

```html
<nav class="navbar navbar-expand-lg bg-dark" data-bs-theme="dark">

    <div class="container">

        <a class="navbar-brand" href="#uvod">
            PIXEL NIGHT
        </a>

        <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#menu"
            aria-controls="menu"
            aria-expanded="false"
            aria-label="Přepnout navigaci">

            <span class="navbar-toggler-icon"></span>

        </button>

        <div class="collapse navbar-collapse" id="menu">

            <div class="navbar-nav ms-auto">

                <a class="nav-link" href="#uvod">Úvod</a>
                <a class="nav-link" href="#program">Program</a>
                <a class="nav-link" href="#registrace">Registrace</a>

            </div>

        </div>

    </div>

</nav>
```

## Než budeš pokračovat

Najdi v kódu:

```text
navbar-brand
```

Který prvek stránky ovlivňuje?

Potom najdi:

```text
nav-link
```

A nakonec:

```text
navbar-expand-lg
```

Zmenši okno prohlížeče a sleduj, co se s navigací stane.

Potom zkus změnit:

```text
navbar-expand-lg
```

na:

```text
navbar-expand-md
```

### Otázka

Co se změnilo?

`md` a `lg` jsou **breakpointy** – hranice šířky obrazovky, od kterých Bootstrap změní chování prvku.

[Bootstrap dokumentace → Navbar → Responsive behaviors](https://getbootstrap.com/docs/5.3/components/navbar/?utm_source=chatgpt.com#responsive-behaviors)

---

# 4. Začínáme hlavní část stránky

Pod navigaci vytvoř:

```html
<section id="uvod">

</section>
```

Do sekce vlož:

```html
<div class="container">

</div>
```

## Co dělá `container`?

`container` vytváří hlavní prostor pro obsah.

Pomáhá například:

- udržet obsah v rozumné šířce,
- zarovnat ho doprostřed,
- vytvořit odstup od krajů obrazovky.

S `container` se v Bootstrapu budeš setkávat velmi často.

---

# 5. Potřebujeme dva sloupce

Chceme vytvořit přibližně toto rozložení:

```text
--------------------------------------------------

NÁZEV AKCE                INFORMACE
popis                     datum
tlačítka                  místo

--------------------------------------------------
```

K tomu použijeme **Bootstrap Grid**.

Jeho základní struktura vypadá takto:

```html
<div class="container">

    <div class="row">

        <div class="col">
            První sloupec
        </div>

        <div class="col">
            Druhý sloupec
        </div>

    </div>

</div>
```

Zapamatuj si hlavně pořadí:

```text
CONTAINER
    ↓
ROW
    ↓
COLUMN
```

Tedy:

```text
oblast s obsahem
    ↓
řádek
    ↓
sloupce
```

---

# 6. Grid používá systém 12 částí

Představ si jeden řádek rozdělený na 12 dílů:

```text
|1|2|3|4|5|6|7|8|9|10|11|12|
```

Pokud chceme dvě stejně široké poloviny:

```text
6 + 6 = 12
```

Pokud chceme jednu část větší:

```text
8 + 4 = 12
```

Do svého `container` proto vlož:

```html
<div class="row">

    <div class="col-lg-8">

    </div>

    <div class="col-lg-4">

    </div>

</div>
```

## Jak číst `col-lg-8`?

Rozděl si název:

```text
col - lg - 8
```

`col` = sloupec

`lg` = breakpoint

`8` = počet částí z dvanácti

Třída tedy říká:

> Od breakpointu `lg` má tento sloupec zabírat 8 částí z 12.

Na menších obrazovkách se tyto dva bloky zobrazí pod sebou.

### Vyzkoušej

Do obou sloupců dočasně napiš krátký text a měň šířku okna.

Sleduj, kdy se rozložení změní.

[Bootstrap dokumentace → Grid](https://getbootstrap.com/docs/5.3/layout/grid/?utm_source=chatgpt.com)

---

# 7. Vytvoř levou část hero sekce

Do:

```html
<div class="col-lg-8">
```

vlož:

```html
<h1 class="display-3 fw-bold">
    PIXEL NIGHT 2026
</h1>

<p class="lead">
    Kreativní večer plný designu,
    animace a digitálních experimentů.
</p>

<a href="#registrace" class="btn btn-primary">
    Chci dorazit
</a>
```

Podívej se na použité třídy.

### `display-3`

Vytvoří výrazný nadpis ve stylu Bootstrap „display heading“.

### `fw-bold`

Nastaví tučné písmo.

`fw` pochází z **font weight**.

### `lead`

Zvýrazní úvodní odstavec.

### `btn`

Vytvoří vzhled tlačítka.

### `btn-primary`

Určí jeho barevnou variantu.

---

# 8. První malý samostatný úkol

Vedle tlačítka:

```text
Chci dorazit
```

přidej druhé:

```text
Program
```

Tentokrát už nedostaneš hotový kód.

Druhé tlačítko má být pouze s obrysem.

V dokumentaci najdi:

**Components → Buttons → Outline buttons**

[Bootstrap dokumentace → Buttons](https://getbootstrap.com/docs/5.3/components/buttons/?utm_source=chatgpt.com#outline-buttons)

Výsledek by měl mít dvě různá tlačítka:

```text
[ Chci dorazit ]  [ Program ]
```

U druhého tlačítka nastav odkaz na:

```text
#program
```

---

# 9. Pravou část vytvoříme pomocí Card

Do:

```html
<div class="col-lg-4">
```

vložíme komponentu **Card**.

Její jednoduchý základ je:

```html
<div class="card">

    <div class="card-body">

        obsah karty

    </div>

</div>
```

`card` vytváří samotnou kartu.

`card-body` vytváří prostor pro její hlavní obsah.

## Tvůj úkol

Do karty doplň:

```text
Kdy a kde?

23. října 2026
Pardubice
17:00
```

Pro nadpis můžeš použít například:

```html
<h2 class="h4">
    Kdy a kde?
</h2>
```

### Proč `h2`, ale třída `h4`?

`<h2>` určuje **význam nadpisu ve struktuře HTML**.

Třída:

```text
h4
```

mění jeho **vizuální velikost**.

Struktura dokumentu a jeho vzhled tedy nemusí být totéž.

[Bootstrap dokumentace → Cards](https://getbootstrap.com/docs/5.3/components/card/?utm_source=chatgpt.com)

---

# 10. Stránka potřebuje více prostoru

Hero sekce je nyní pravděpodobně příliš nalepená na okolní obsah.

Změň:

```html
<section id="uvod">
```

na:

```html
<section id="uvod" class="py-5">
```

## Jak číst `py-5`?

```text
p  y  5
```

`p` = padding

`y` = horní a dolní strana

`5` = velikost mezery

Podobně:

```text
mb-4
```

znamená:

```text
m = margin
b = bottom
4 = velikost
```

### Experiment

U některého prvku vyzkoušej:

```text
mb-1
```

a potom:

```text
mb-5
```

Rozdíl si nejdříve prohlédni. Teprve potom vyber hodnotu, která se hodí k tvému návrhu.

[Bootstrap dokumentace → Spacing](https://getbootstrap.com/docs/5.3/utilities/spacing/?utm_source=chatgpt.com)

---

# 11. Přidej sekci Program

Pod hero sekci vytvoř:

```html
<section id="program" class="py-5 bg-body-tertiary">

    <div class="container">

        <h2 class="mb-4">
            Program
        </h2>

        <div class="row g-4">

            <!-- sem přijdou karty -->

        </div>

    </div>

</section>
```

## Co znamená `g-4`?

`g` zde znamená **gutter**.

Gutter je mezera mezi sloupci a řádky Bootstrap Gridu.

`g-4` tedy vytvoří prostor mezi našimi budoucími kartami.

---

# 12. Vytvoř první kartu programu

Do `row` vlož:

```html
<div class="col-md-4">

    <div class="card h-100">

        <div class="card-body">

            <h3 class="card-title">
                Type Lab
            </h3>

            <p class="card-text">
                Experimentování s typografií
                a vizuální hierarchií.
            </p>

            <a href="#" class="btn btn-primary">
                Více informací
            </a>

        </div>

    </div>

</div>
```

Tentokrát už bys měl velkou část kódu dokázat přečíst.

### `col-md-4`

Každý sloupec zabírá od breakpointu `md`:

```text
4 části z 12
```

Do jednoho řádku se tedy vejdou tři:

```text
4 + 4 + 4 = 12
```

Na menší obrazovce se zobrazí pod sebou.

### `h-100`

Nastaví kartě výšku `100 %` dostupného prostoru.

Díky tomu mohou být karty v jednom řádku stejně vysoké, i když mají různě dlouhý obsah.

---

# 13. Další dvě karty už vytvoř sám

Potřebujeme celkem **tři karty programu**.

První máš hotovou.

Vytvoř další dvě podle stejného principu.

Každá musí obsahovat:

- vlastní nadpis,
- vlastní krátký text,
- tlačítko.

Můžeš například použít:

```text
TYPE LAB
MOTION ARENA
AI REMIX
```

Lepší ale bude, když obsah přizpůsobíš vlastnímu tématu.

---

# 14. Jednu kartu zvýrazni

Vyber nejdůležitější část programu.

Tuto kartu odliš od ostatních.

Tentokrát už nedostaneš konkrétní třídu.

V dokumentaci prozkoumej:

**Utilities → Background**

a:

**Utilities → Shadows**

Zkus změnit například:

- pozadí,
- barvu textu,
- stín.

[Bootstrap dokumentace → Background](https://getbootstrap.com/docs/5.3/utilities/background/?utm_source=chatgpt.com)

[Bootstrap dokumentace → Shadows](https://getbootstrap.com/docs/5.3/utilities/shadows/?utm_source=chatgpt.com)

Pokud se po změně pozadí text špatně čte, musíš vyřešit také jeho barvu.

To už je součást samostatné práce.

---

# 15. Závěrečnou sekci postav s menší nápovědou

Na konec stránky vytvoř sekci:

```text
Chceš dorazit?

Krátký text o registraci

[ Registrovat se ]
```

Sekce musí mít:

```html
<section id="registrace">
```

Celý hotový kód už nedostaneš.

Použij ale věci, se kterými jsme dnes pracovali:

```text
container
py-5
text-center
btn
```

Chceš-li tmavé pozadí, najdi vhodnou Bootstrap utility v dokumentaci.

---

# 16. Teď z toho udělej svůj web

Funkční základ už máš.

Teď nesmí stránka zůstat pouze kopií našeho příkladu.

## Změň obsah

Uprav minimálně:

- název akce,
- popis,
- datum,
- místo,
- názvy a obsah programu.

## Uprav design

Pomocí dokumentace změň alespoň **čtyři věci**.

Můžeš řešit například:

- pozadí hero sekce,
- vzhled tlačítek,
- velikost nadpisu,
- mezery,
- vzhled jedné karty,
- stín,
- zaoblení,
- zarovnání textu.

Neexistuje jedno správné řešení.

---

# Jak pracovat s dokumentací?

Dokumentaci nemusíš číst od začátku do konce.

Představ si například, že chceš:

> více zaoblit kartu

Nejprve zkus odhadnout, kam taková vlastnost patří:

```text
border → radius
```

V dokumentaci otevři:

**Utilities → Borders**

Použij:

```text
Ctrl + F
```

a vyhledej:

```text
radius
```

Podívej se na příklady, jednu možnost vyzkoušej a zkontroluj výsledek.

Pokud nefunguje podle očekávání, vrať se do dokumentace a zkus zjistit proč.

**Tohle je správná práce s dokumentací.**

[Bootstrap dokumentace → Borders](https://getbootstrap.com/docs/5.3/utilities/borders/?utm_source=chatgpt.com)

---

# 17. Označ tři věci, které sis musel dohledat

Na tři místa ve svém HTML vlož komentář.

Například:

```html
<!-- DOC: hledal jsem, jak vytvořit outline tlačítko -->
```

nebo:

```html
<!-- DOC: hledal jsem, jak více zaoblit kartu -->
```

nebo:

```html
<!-- DOC: zjišťoval jsem rozdíl mezi breakpointy md a lg -->
```

Komentář napiš tam, kde jsi dané řešení skutečně použil.

Cílem je dokázat pojmenovat:

> Co jsem nevěděl a jak jsem to zjistil?

---

# Před odevzdáním

Vyzkoušej stránku nejprve v širokém okně a potom okno výrazně zúž.

Zkontroluj:

☐ navigace se na malé šířce sbalí

☐ odkazy v navigaci vedou na správné části stránky

☐ hero se na malé obrazovce nerozbije

☐ na větší obrazovce jsou karty vedle sebe

☐ na malé obrazovce jsou karty pod sebou

☐ všechny texty jsou dobře čitelné

☐ stránka má dostatek prostoru mezi prvky

☐ obsah není stejný jako ve vzoru

☐ provedl jsem alespoň čtyři vlastní úpravy pomocí Bootstrapu

☐ mám tři komentáře o práci s dokumentací

---

# Dnes nepoužíváme

❌ vlastní CSS soubor

❌ `<style>`

❌ atribut `style=""`

❌ Sass

Pokud potřebuješ něco upravit, polož si nejdříve otázku:

> **Umí to už Bootstrap?**

---

# Hotovo dříve?

V dokumentaci otevři sekci:

**Components**

Vyber jednu komponentu, kterou jsme dnes nepoužili.

Například:

```text
Badge
Alert
Accordion
Modal
Carousel
```

Nejdříve zjisti, jak funguje.

Potom si polož otázku:

> Hodí se tato komponenta na můj web?

Pokud ano, přidej ji.

Pokud ne, vyber jinou.

**Cílem není použít co nejvíce komponent. Cílem je naučit se Bootstrap používat.**