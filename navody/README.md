# Návody — konvence téhle sekce

Tenhle soubor je jen pro toho, kdo pracuje **v repozitáři webu**. Zdroj
pravdy o postupu je skill `/navod` v repozitáři appky
(`nazkouseno/.claude/skills/navod/SKILL.md`) a seznam zbývající práce
v `nazkouseno/docs/17-navody-plan.md`. Sem se píše jen to, co je místní.

## Co tu je

| Stránka | Skupina |
|---|---|
| `import-scenare.html` | Začínáme |
| `rozpoznani-scenare.html` | Začínáme |
| `dril.html` | Učení |
| `kolik-uz-umim.html` | Učení |
| `ctecka.html` | Text |
| `skrty.html` | Text |

`index.html` je rozcestník. Skupiny se v něm zobrazují **jen když mají
obsah** — prázdná skupina ani „chystáme se" tam nepatří.

## Kostra nové stránky

Nejrychlejší cesta je zkopírovat `skrty.html` a přepsat obsah. Drží se
tím hlavička, patička, skript na odkrývání i pořadí prvků v `<head>`.

Co po kopii projít:
1. `<title>`, `<meta name="description">`
2. `.guide-head` — `.crumb` zpátky na rozcestník, `.eyebrow` = skupina,
   `h1`, odstavec s tím, na jakou otázku stránka odpovídá
3. bloky `.way` (text vlevo, `.phone` se snímkem vpravo)
4. volitelně blok `.faq` na katalog krátkých vysvětlení
5. závěrečná prósa v `.policy`
6. `.contact-box` s mailem
7. položka v `index.html`

**Nové CSS nebylo potřeba ani u jedné z šesti stránek.** Když se zdá, že
je, podívej se nejdřív do tabulky ve skillu — stylopis skoro určitě už
tu věc umí.

## Místní pravidla, na která se snadno zapomene

- **Favicon** je `assets/img/favicon.svg`. Ze stránek v `navody/` na něj
  vede cesta `../assets/img/favicon.svg`.
- **Stylopis se linkuje s `?v=`** a teď je na `v=6`. Když sáhneš do
  `assets/css/site.css`, **zvedni verzi na všech sedmi stránkách**
  (`index.html`, `soukromi.html` a šest návodů) — jinak návštěvník se
  starou cache dostane rozbitou sazbu.
- **Kotvy** není potřeba nijak odsazovat. `html { scroll-padding-top }`
  v stylopisu to řeší globálně pro celý web; výška hlavičky je
  v proměnné `--header-h`.
- **Snímky** patří do `assets/img/navod/`, **700 px na šířku**, kolem
  130–260 kB. Do `<img>` vždycky `width="700" height="1522"` (kvůli
  poskakování sazby) a `alt`, který popisuje, co je na obrazovce.
- **Hlas:** kroky a instrukce „ty", podpora a vysvětlení „vy". Je to
  záměr, ne nedůslednost — appka mluví „ty", FAQ mluví „vy".
- ⚠️ **Web smí tvrdit jen to, co appka doopravdy umí,** a **nesmí tvrdit
  dostupnost v obchodě**, dokud tam appka není. Odznaky v hero mají
  proto zatím prázdný `href`.

## Vydání

`push` na `main` **je vydání** — GitHub Pages, žádná recenze, živé za
desítky sekund. Před pushem projít odkazy lokálně:

```
python3 -m http.server 8000
```

a ověřit, že všechno vrací 200 (včetně obrázků). Po pushi počítej s tím,
že první požadavek může vrátit 404, než deploy doběhne.
