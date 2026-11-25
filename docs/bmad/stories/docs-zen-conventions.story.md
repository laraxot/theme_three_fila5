---
title: "Three — bonifica docs .md (convenzioni zen)"
type: story
status: done
module: Three
epic: docs-second-brain
created: 2026-11-25
updated: 2026-11-25
parent: ../../../../Modules/Xot/docs/bmad/stories/docs-zen-conventions-swarm.story.md
qmd: "three tema docs bonifica kebab-case index duplicate methods report frontmatter qmd"
---
# Three — bonifica docs `.md`

## Context and Problem Statement

Lane C dello swarm `laravel/Modules/Xot/docs/bmad/stories/docs-zen-conventions-swarm.story.md`.
Il tema era quasi a norma: solo 2 nomi non kebab e un report generico cross-modulo.

## Decision Drivers

- Richiesta utente / acceptance criteria della story
- Vincoli BMAD, second brain, Pest gate e dati sacri

## Considered Options

- Status quo (non fare)
- Implementare come descritto nel Decision Outcome

## Decision Outcome

Scelta: **implementare**, perché i driver sopra.

## Perche'

Lane C dello swarm `laravel/Modules/Xot/docs/bmad/stories/docs-zen-conventions-swarm.story.md`.
Il tema era quasi a norma: solo 2 nomi non kebab e un report generico cross-modulo.

## Prima / Dopo

| Metrica | Prima | Dopo |
|---|---:|---:|
| file `.md` | 64 | 64 (−1 eliminato, +1 questa story) |
| copie esatte (md5) | 0 | 0 |
| nomi datati | 0 | 0 |
| non kebab | 2 | 0 |
| senza frontmatter | 0 | 0 |
| senza `qmd` | 0 | 0 |
| annidamenti generati | 0 | 0 |

## Cosa e' stato rinominato/eliminato e perche'

- `adr/INDEX.md` → `adr/index.md`, `contracts/INDEX.md` → `contracts/index.md` (nessuna collisione; link aggiornati).
- Eliminato `wiki/duplicate-methods-report.md`: report grep generico su tutti i moduli (presente identico in altri
  moduli), nulla di specifico del tema; link reindirizzati a `wiki/duplicate-methods.md` (specifico Three).

## Casi lasciati in dubbio

- `bmad/prd.md` ("Author: Product Team", Draft) e `bmad/tech-spec.md`: semi-generici ma citano pipeline Blade/Tailwind/Vite
  del tema; lasciati.
- `raw/root-import/` e `stories/` vuote: non toccate (non sono `.md`).

## Gate

Solo `.md`: PHPStan/Pint/Pest non applicabili (skip documentato; PHPStan gia' 0). Verifica: misura ripetuta,
YAML frontmatter parse 0 errori, 0 riferimenti a file rimossi/rinominati.


### Consequences

- Buono, perché chiude il gap descritto nel Context
- Cattivo, perché richiede write-back docs, lock e quality gate

### Confirmation

Aggiungere prova ripetibile (Pest exit code + conteggio, PHPStan, o skip host documentato).
