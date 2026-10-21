---
title: "Three — scopo, confini e come servirlo meglio"
type: concept
theme: Three
status: active
created: 2026-09-02
updated: 2026-09-02
tags: [scopo, confini, tema, tema-vuoto, documentazione, archiviazione]
qmd: "scopo tema three vuoto un solo blade nessun theme.json nessun riferimento archiviare"
---

# Three — scopo, confini e come servirlo meglio

## Lo scopo, dedotto dal codice

Il codice di Three è, per intero:

```
Themes/Three/resources/views/components/blocks/links/grid.blade.php
```

Un file. Nessun altro. Non c'è `composer.json`, non c'è `theme.json`, non c'è
`package.json`, non c'è `vite.config.js`, non c'è `tailwind.config.js`, non c'è `app/`,
non c'è `lang/`, non c'è `public/`, non c'è un solo file `.css` o `.js`.

Quell'unico file è **byte a byte identico** all'omonimo di One e di Zero:

```bash
cmp Themes/Three/resources/views/components/blocks/links/grid.blade.php \
    Themes/Zero/resources/views/components/blocks/links/grid.blade.php    # nessuna differenza
```

E nessuna configurazione lo nomina. `pub_theme` e `adm_theme` valgono `Zero` su tutti
gli host reali e `One` su `localhost`; la stringa `Three` non compare in `config/`, in
`Modules/*/app`, in `Modules/*/config`, né in `app/`. L'unica occorrenza in tutto il
codice PHP è un dato di test in un modulo che non c'entra
(`Modules/Tenant/tests/Unit/TenantStatementCoverageTest.php:699`, un record chiamato
`'Three'`).

Accanto a quell'unico file Blade ci sono **54 documenti Markdown** in `docs/` (55
contando questa pagina).

Da qui la formulazione in una riga:

> **Three, oggi, non è un tema: è una cartella di documentazione con dentro un file
> Blade duplicato da Zero, che nessuna configurazione seleziona e nessun codice
> nomina.**

Questa non è una critica agli autori dei 54 documenti. È il fatto che va scritto per
primo, perché ogni altra affermazione su Three dipende da esso: non c'è un
comportamento da descrivere, quindi non c'è uno scopo da dedurre — solo uno da
decidere.

## I confini, e dove oggi sono rotti

### 1. 54 documenti per 1 file di codice

Il rapporto documentazione/codice è 54:1. Fra i 54 ci sono
`docs/architecture-rules.md`, `docs/filament-version.md`,
`docs/laravel-13-upgrade.md`, `docs/laravel-13-composer-boundary.md`,
`docs/code-redundancy-audit.md`, `docs/quality-audit.md`. Sono documenti che descrivono
architettura, versioni e qualità di un tema che consiste in un componente Blade copiato.

Il rischio non è lo spreco: è che quei documenti vengano letti da un agente o da una
persona come descrizione di uno stato reale. Un `quality-audit.md` su un file solo dice
qualcosa sul metodo di chi lo ha generato, non sul tema.

### 2. Il README descrive un tema che non c'è

`README.md` promette "Release automation" con `./.github/workflows/semantic-release.yml`
e `./changelog.md`: la cartella `.github/` non esiste e il changelog è `CHANGELOG.md`.
Il testo — "il tema che trasforma complessita in vantaggio operativo", "Cosa promette",
"Filosofia" — è identico, paragrafo per paragrafo, a quello di One e di Zero. È un
modello compilato con un nome diverso, non una descrizione.

Un README che descrive tre unità diverse con le stesse parole non sta descrivendo
nessuna delle tre.

### 3. Il tema non è registrabile

Perché un tema sia selezionabile da `xra.php` servono almeno `theme.json` (come Zero,
che dichiara `"type": "pub"`, `"active": true`) e una struttura `resources/views/`
completa: Three non ha né l'uno né l'altra. Se domani qualcuno scrivesse
`'pub_theme' => 'Three'`, `XotData::getPubThemeViewPath()`
(`Modules/Xot/app/Datas/XotData.php:351`) fallirebbe con
`realpath not find dir[…/Themes/Three/resources/views/…]` alla prima view richiesta. Il
tema non è incompleto: è non funzionante per costruzione.

### 4. L'unico file è una copia

`components/blocks/links/grid.blade.php` esiste identico in tutti e tre i temi. Se è un
blocco riusabile, il suo posto è `Modules/UI/resources/views/components/blocks/`, dove
altri blocchi già stanno — non tre volte sotto tre temi.

## Come servire meglio lo scopo

Le mosse qui sono meno di altrove perché lo spazio delle scelte è piccolo: o Three
diventa un tema, o smette di fingere di esserlo.

### 1. Decidere: archiviare oppure completare

**Archiviare** è la scelta che il codice suggerisce. `Themes/Three/` si sposta sotto
un percorso di archivio con una riga di motivazione, i 54 documenti seguono, e il repo
smette di contenere un'unità che nessuna configurazione può usare.

**Completare** significa dare a Three ciò che ha Zero: `theme.json`, `composer.json`,
`package.json`, `vite.config.js`, `tailwind.config.js`, `postcss.config.js`,
`resources/views/layouts/`, `resources/views/pages/` (solo shell generiche e `auth`),
`resources/css/app.css`, `resources/js/app.js`. È giustificato solo se esiste una
ragione visiva per un terzo tema, e quella ragione va scritta **prima** del codice.

```bash
cd laravel
find Themes/Three -type f -not -path '*/docs/*' -not -name '.*' | wc -l   # 4 oggi: 1 blade + README + CHANGELOG + .code-workspace
find Themes/Three/docs -name '*.md' | wc -l                               # 55 con questa pagina
grep -rn "'Three'" config --include='*.php'                               # 0 oggi
```

### 2. Se si archivia, decidere prima dove va il Blade

`components/blocks/links/grid.blade.php` è l'unico contenuto. Se serve a One e Zero, va
promosso a `Modules/UI/resources/views/components/blocks/links/grid.blade.php` e i tre
temi lo consumano via `x-ui::`; se non serve a nessuno, sparisce con il resto.

```bash
cd laravel
cmp Themes/Three/resources/views/components/blocks/links/grid.blade.php \
    Themes/Zero/resources/views/components/blocks/links/grid.blade.php
ls Modules/UI/resources/views/components/blocks/
```

### 3. Non lasciare 54 documenti a descrivere il nulla

Qualunque sia la decisione, i documenti la devono seguire. Se Three si archivia, i 54
`.md` si archiviano con lui; se si completa, `quality-audit.md`,
`code-redundancy-audit.md` e `architecture-rules.md` vanno rigenerati su codice che
esiste. Lasciarli come sono significa mantenere 54 affermazioni non verificabili in un
second brain che altri agenti interrogano.

```bash
cd laravel
head -20 Themes/Three/docs/quality-audit.md         # su quale codice è stato misurato?
head -20 Themes/Three/docs/code-redundancy-audit.md
```

### 4. Riscrivere il README su ciò che è vero

Tre righe oneste ("tema non attivo, un solo componente, in valutazione per
archiviazione") valgono più di trenta righe di modello. E i due link morti
(`.github/workflows/semantic-release.yml`, `changelog.md`) o si fanno esistere o si
tolgono.

```bash
cd laravel/Themes/Three
ls .github/workflows/semantic-release.yml changelog.md 2>&1
diff <(sed -n '1,20p' README.md) <(sed -n '1,20p' ../One/README.md)   # oggi: quasi identici
```

## Cosa NON è compito di Three

- **Non** serve traffico. Nessun host lo seleziona: `pub_theme` è `Zero` in produzione,
  `One` su `localhost`.
- **Non** è il posto dove documentare l'architettura del progetto: `architecture-rules.md`,
  `laravel-13-upgrade.md`, `filament-version.md` descrivono il monorepo, non questo tema,
  e la loro casa è `docs/wiki/`.
- **Non** contiene PHP e non deve contenerne: un tema è markup e asset.
- **Non** ospita pagine di dominio: se un giorno avrà `resources/views/pages/`, sotto ci
  vanno shell generiche e `auth`, non `tickets/`, `news/`, `services/`.
- **Non** scrive in `laravel/public`. Il `public_path()` di questo progetto è
  `public_html/` (`laravel/app/Application.php:16-18`), come da SSoT
  [`public-path-is-public-html`](../../../../docs/wiki/memories/public-path-is-public-html.md).

## Verifica

```bash
cd laravel

# quanto codice c'è davvero
find Themes/Three -type f -not -path '*/docs/*' -not -name '.*' | sort
find Themes/Three -name '*.blade.php' | wc -l          # 1 oggi
find Themes/Three/docs -name '*.md' | wc -l            # 55 con questa pagina

# nessuna configurazione lo nomina
grep -rn "'Three'\|Themes/Three\|Themes\\\\Three" config Modules app --include='*.php' --include='*.json'

# manca tutto ciò che serve a un tema
for f in theme.json composer.json package.json vite.config.js tailwind.config.js postcss.config.js; do
  [ -e "Themes/Three/$f" ] && echo "OK  $f" || echo "--  $f manca"
done

# l'unico file è una copia
cmp Themes/Three/resources/views/components/blocks/links/grid.blade.php \
    Themes/Zero/resources/views/components/blocks/links/grid.blade.php && echo "IDENTICO a Zero"
cmp Themes/Three/resources/views/components/blocks/links/grid.blade.php \
    Themes/One/resources/views/components/blocks/links/grid.blade.php  && echo "IDENTICO a One"
```

## Collegamenti

- [Themes/Zero/docs/scopo.md](../../Zero/docs/scopo.md) — il tema attivo in produzione
- [Themes/One/docs/scopo.md](../../One/docs/scopo.md) — il tema di sviluppo locale
- [public-path-is-public-html](../../../../docs/wiki/memories/public-path-is-public-html.md) — perché non esiste `laravel/public`
- [Modules/UI/docs/scopo.md](../../../Modules/UI/docs/scopo.md) — dove promuovere un blocco riusabile
