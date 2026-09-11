# HAFŤák kvíz

Interaktivní kvíz „Je váš pes připravený na HAFťák?" pro blog e-shopu
[granulejehlicka.cz](https://www.granulejehlicka.cz/).

## Obsah

- `index.html` — celý kvíz v jednom souboru. Žádné závislosti, žádný build.

## Jak funguje

Šest otázek, každá odpověď má 0 až 2 body. Podle součtu se zobrazí jeden ze tří
výsledků s doporučeními a odkazy na e-shop.

Kvíz hlásí svoji výšku rodičovské stránce přes `postMessage`, takže se iframe
může sám dorovnat. Když to prostředí nedovolí, funguje na pevné výšce 700 px,
což pokryje i nejvyšší obrazovku na mobilu (687 px).

Pozadí je průhledné, aby kvíz splynul s okolním článkem.

## Barvy

- `#009cdd` — hlavička
- `#db9319` — ukazatel postupu, odznak výsledku, hlavní tlačítko

Na obou je tmavý text. Bílá má na těchto barvách kontrast 3,09:1 a 2,56:1,
což je pod hranicí čitelnosti.

## Vložení do článku

```html
<iframe id="kviz-haftak" src="ADRESA-KVIZU" style="width:100%;height:700px;border:0;" title="Je váš pes připravený na HAFťák?" loading="lazy"></iframe>
<script>window.addEventListener('message',function(e){if(e.data&&e.data.kviz==='haftak'&&e.data.vyska){document.getElementById('kviz-haftak').style.height=(e.data.vyska+20)+'px';}});</script>
```

## Úpravy

Otázky, odpovědi i výsledky jsou v poli `OTAZKY` a `VYSLEDKY` na začátku
skriptu v `index.html`. Body u odpovědí určují, který výsledek se zobrazí.
