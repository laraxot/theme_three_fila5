---
title: "Three — stato qualita' misurato"
type: audit
theme: Three
status: active
updated: 2026-11-25
qmd: "three quality audit completamento phpstan phpmd phpinsights test coverage metodi duplicati omonimi ridondanza zero"
merged_from:
  - bmad/quality-audit.md
  - wiki/cosa-migliorare.md
  - completion-status.md
  - project-completion-gaps.md
  - wiki/code-redundancy-audit.md
  - wiki/duplicate-methods.md
  - wiki/concepts/duplicate-method-bodies.md
  - wiki/concepts/method-name-homonyms.md
  - wiki/concepts/php-method-name-homonyms-theme-impact.md
---

# Three — stato qualita'

## Misura (2026-11-25)

| Indicatore | Valore |
|---|---:|
| File codice | 1 Blade (39 righe), 0 PHP |
| Test (`*Test.php`) | 0 |
| Metodi duplicati / omonimi / corpi identici | 0 (non c'e' PHP) |
| TODO/FIXME | 0 |
| Story BMAD | 3 (`0.1` blocked, 2 docs done) |

Le misure storiche (PHPInsights 100%, PHPMD 0, PHPStan 0) sono vere ma **non dicono nulla**:
sono il punteggio di un solo file. Il censimento di progetto su omonimi e corpi duplicati sta in
`docs/wiki/method-name-homonym-census.md` e `docs/wiki/duplicate-method-bodies-census.md`.

## Cosa manca per "completo"

Non e' un problema di qualita' ma di esistenza: il completamento dipende dalla decisione della
story [0.1](./bmad/stories/0.1.archive-or-complete-decision.story.md). Se si completa: test sui
percorsi che si rompono, coverage misurata, `theme.json` registrabile.

## Come rifare le misure

```bash
cd laravel
md5sum Themes/{One,Three,Zero}/resources/views/components/blocks/links/grid.blade.php
find Themes/Three -path '*/docs' -prune -o -type f -print | grep -v '/.git/'
php -d memory_limit=2G ./vendor/bin/phpstan analyse Themes/Three   # solo se compare PHP
```

## Insidie

- Prima di fidarsi di un numero: tree fermo e `vendor/` completo (un autoloader dimezzato ha
  prodotto misure false a settembre 2026).
- PHPMD va puntato su `app/`, non sulla root: una classe anonima nei test fa abortire l'analisi
  e stampare zero rilievi.
- `reportUnmatchedIgnoredErrors` non conta i `@phpstan-ignore` inline.
