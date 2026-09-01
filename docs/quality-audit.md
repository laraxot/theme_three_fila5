---
title: "Audit di qualita: tema Three"
type: report
theme: Three
updated: 2026-09-01
qmd: "audit qualita three phpstan phpmd phpinsights pest coverage soppressioni collisioni case"
---

# Audit di qualita — tema Three

Misurato il 1 settembre 2026 a tree fermo. Ogni numero viene da un comando
eseguito, non da una stima; i comandi sono in fondo, cosi la misura si puo
rifare e contestare.

## Stato misurato

| Metrica | Valore |
|---|---:|
| File PHP | 1 |
| Righe di codice | 39 |
| File di test `*Test.php` | 0 |
| Casi di test | 0 |
| Casi di test per file PHP | 0.00 |
| `@phpstan-ignore` nel codice | 0 |
| Rilievi PHPMD su `app/` | 0 |
| PHPInsights — Code | 100.0 % |
| PHPInsights — Complexity | 100.0 % |
| PHPInsights — Architecture | 100.0 % |
| PHPInsights — Style | 100.0 % |
| File `.md` sotto `docs/` | 47 |
| `TODO`/`FIXME`/`HACK` | 0 |
| Test con casi che non girano (senza suffisso `Test.php`) | 0 |
| Collisioni di case nel codice | 0 |
| Collisioni di case nei docs | 0 |
| Marker di conflitto | 0 |
| File `.lock` committati | 0 |
| File `.code-workspace` | 1 |

PHPStan su tutto `Modules/` e a **0 errori, exit 0**, con `ignoreErrors` vuoto in
`phpstan.neon` e `reportUnmatchedIgnoredErrors: true`. Quello zero pero non copre le
soppressioni scritte nel codice come commenti `@phpstan-ignore`: quelle non passano
da `ignoreErrors` e non vengono contate da nessun gate.

## Cosa non va

### Il tema e' quasi vuoto

1 file PHP, 39 righe, nessun `composer.json`, nessuna cartella `app/`, nessun test.
I 47 file `.md` sotto `docs/` documentano un tema che non ha ancora codice.
Il `100 %` di PHPInsights qui non e' un punteggio di qualita': e' il punteggio di un
file solo.

## Coverage

**`docs/coverage.md` non esiste in questo tema.** Il pilastro 5 dello standing
order lo richiede. Va creato alla prossima run di Pest, con il comando canonico:

```bash
cd laravel
XDEBUG_MODE=coverage ./vendor/bin/pest Themes/Three/tests -c Themes/Three/phpunit.xml --coverage --min=0
```

Servono **entrambe** le opzioni: `-c` sposta il perimetro di coverage, il path
sposta il bootstrap di `Pest.php` e `Helpers.php`.

## Cosa questa misura non vede

- **Il database di test non risponde.** `10.100.200.53:3306` e irraggiungibile: i
  test che scrivono vengono saltati, non falliti. Un conteggio di test verdi qui
  dentro non dice quanti test hanno davvero girato.
- **PHPStan e a zero, ma le soppressioni inline non sono contate da nessun gate.**
  `reportUnmatchedIgnoredErrors` controlla `ignoreErrors` nel neon, non i commenti
  `@phpstan-ignore` sparsi nel codice.
- **PHPMD misurato su `app/`, non sulla root del tema.** Puntandolo alla root,
  una singola classe anonima nei test fa abortire tutta l'analisi e stampare zero
  rilievi. Uno zero PHPMD sulla root non e una prova di pulizia.
- **I file sotto `tests/` senza suffisso `Test.php` non sono tutti test.** Una
  prima passata ne aveva contati 62 come "test che non girano": verificati uno a uno,
  47 sono stub, fake, helper e classi base che correttamente non hanno il suffisso.
  Il conteggio qui sopra riporta solo i file che contengono davvero casi di test.
- **PHPInsights `Complexity 100 %` su tutte e 22 le unita.** Un valore identico
  ovunque non sta discriminando niente: va trattato come non informativo finche
  non se ne capisce la configurazione.

## Come rifare la misura

```bash
cd laravel
php -d memory_limit=-1 ./vendor/bin/phpstan analyse Themes/Three
./tools/phpmd.sh Themes/Three/app          # non la root: aborta sulle classi anonime
./tools/phpinsights.sh Themes/Three
XDEBUG_MODE=coverage ./vendor/bin/pest Themes/Three/tests -c Themes/Three/phpunit.xml --coverage --min=0
grep -rc "@phpstan-ignore" --include=*.php Themes/Three | grep -v ":0$"
```

Prima di fidarsi di qualunque numero: verificare che nessun altro agente stia
scrivendo sul tree, altrimenti la misura e falsa e diversa a ogni run.

```bash
/usr/bin/find Modules -newermt '-70 seconds' -type f | wc -l   # deve dare 0
```

Audit complessivo e confronto fra tutte le unita: [`docs/quality-audit.md`](../../../../docs/quality-audit.md) nella root del progetto.

