---
title: "Cosa migliorare: tema Three"
type: report
theme: Three
updated: 2026-09-01
qmd: "cosa migliorare three phpstan phpmd phpinsights coverage debito priorita"
---

# Cosa migliorare — tema Three

Ogni affermazione qui sotto viene da un comando eseguito il 1 settembre 2026, dopo il
ripristino di `vendor/` a 330 pacchetti. Le misure precedenti a quella data giravano su
un autoloader dimezzato e non valgono.

## I numeri

| | |
|---|---:|
| Errori PHPStan (modulo isolato) | — |
| Rilievi PHPMD su `app/` | 0 |
| PHPInsights — Code | 100 % |
| PHPInsights — Architecture | 100 % |
| PHPInsights — Style | 100 % |
| File PHP | 1 |
| Casi di test | 0 |
| Casi di test per file | 0.00 |
| Coverage di riga | **mai misurata** |
| `@phpstan-ignore` | 0 |
| `TODO`/`FIXME`/`HACK` | 0 |
| File `.md` sotto `docs/` | 53 |

## Il quadro

Il tema Three è **un file PHP da 39 righe**, nessun `composer.json`, nessuna
cartella `app/`, zero test — e **47 file `.md`** sotto `docs/` che lo documentano.

Quarantasette documenti per trentanove righe di codice. O il tema è stato progettato e mai
scritto, e allora la documentazione è un progetto travestito da manuale; o è stato
svuotato, e allora la documentazione descrive qualcosa che non esiste più. Va deciso quale
delle due, perché sono due lavori diversi.

## Cosa fare, in ordine di resa

1. **Alzare la densità di test.** 1 file PHP e 0 casi: 0.00 per file. Non serve un piano di copertura totale, serve un test sui percorsi che si rompono.

## Come rifare ogni numero

```bash
cd laravel
php -d memory_limit=-1 ./vendor/bin/phpstan analyse Themes/Three
./tools/phpmd.sh Themes/Three/app     # non la root: aborta sulle classi anonime
./tools/phpinsights.sh Themes/Three
XDEBUG_MODE=coverage ./vendor/bin/pest Themes/Three/tests -c Themes/Three/phpunit.xml --coverage --min=0
```

Prima di fidarsi di qualunque numero: il tree deve essere fermo e `vendor/` completo.

```bash
/usr/bin/find Modules -newermt '-70 seconds' -type f | wc -l   # deve dare 0
php -r 'echo count(require "vendor/composer/autoload_classmap.php");'   # ~25358, non 13041
```

Quadro comparativo di tutte le unità: [`docs/quality-audit.md`](../../../../docs/quality-audit.md).

