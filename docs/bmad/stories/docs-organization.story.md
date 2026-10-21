---
title: "Organizzazione docs — Theme Three"
type: story
status: done
theme: Three
epic: docs-governance
story_id: "theme-three-docs-organization"
track: quick-flow
created: 2026-10-21
updated: 2026-10-21
tags: [docs, theme, three, bmad, index, frontmatter, links]
qmd: "theme three docs organization canonical index frontmatter qmd link audit filament blueprint"
related:
  - ./0.1.archive-or-complete-decision.story.md
  - ../../../../One/docs/bmad/stories/docs-organization.story.md
  - ../../../../Zero/docs/bmad/stories/docs-organization.story.md
  - ../../../../../Modules/Xot/docs/bmad/stories/phpstan-modules-swarm-20261021.story.md
---

# Organizzazione docs — Theme Three

## Obiettivo

Consolidare la documentazione del tema Three attorno a un indice unico, eliminare
gli ingressi duplicati e allineare frontmatter, qmd, link e blueprint Filament.

## Baseline verificata

- 54 file `.md`; 0 senza frontmatter, 21 senza `qmd`.
- `docs/INDEX.md` cancellato da un processo concorrente durante il lavoro;
  `docs/index.md` conteneva 43 link relativi rotti.
- `bmad/readme.md` era un secondo indice con mappa generata e link non rebasati.
- Nessuna coppia case-only residua.

## Acceptance criteria

- [x] Un solo indice canonico: `docs/index.md`.
- [x] `bmad/readme.md` è solo l'ingresso del dossier BMAD, non un secondo indice.
- [x] Frontmatter YAML valido e `qmd` presente in tutti i `.md` attivi.
- [x] Nessun link relativo rotto negli indici e nei README del tema.
- [x] `filament-blueprint.md` descrive il contratto Filament del tema.
- [x] `architecture/README.md` documenta la cartella architettura.

## Lavoro eseguito

| Area | Azione | Esito |
| --- | --- | --- |
| Indice | Riscritto `index.md` dopo la cancellazione concorrente di `INDEX.md` | 0 link rotti |
| README | Aggiornato `README.md`; `bmad/readme.md` ridotto a ingresso | Navigazione unica |
| Frontmatter | Aggiunto `qmd` ai file attivi mancanti | 0 mancanti |
| Link | Rebase automatico dei link con basename univoco | 49 link corretti |
| Blueprint | Creato `bmad/filament-blueprint.md` | Contratto XotBase + widget FO espliciti |
| Architettura | Creato `architecture/README.md` | Cartella non più vuota |
| Story | Creata questa story nel percorso canonico | Tracciamento BMAD |

## Verifica

```bash
find laravel/Themes/Three/docs -type f | tr 'A-Z' 'a-z' | sort | uniq -d  # vuoto
# frontmatter/qmd: 57 file attivi, 0 senza frontmatter, 0 senza qmd
# link relativi: 0 rotti in indici/README; debito residuo nei documenti storici
git diff --check -- laravel/Themes/Three/docs                  # solo whitespace storico
```

Nessun codice applicativo toccato: Pest e PHPStan non applicabili a un diff
docs-only. Nessun commit/push.

## Debito residuo

- Link relativi rotti in documenti storici verso moduli assenti nel checkout o
  documenti rimossi in passate pulizie; non sono negli indici/README.
- Three resta uno skeleton: mancano `theme.json`, `composer.json`, `app/` e `lang/`.
  La docs lo dichiara, non lo nasconde.
- Rischio di scritture concorrenti: `INDEX.md` è stato cancellato da un altro
  processo durante la sessione; prima di nuovi edit ricontrollare `git status`.

## Note docs-guardian (swarm PHPStan 2026-10-21b)

Temi già organizzati: nessun nuovo contenuto di feature. Dominio PHPStan residuo
documentato nei moduli (Progressioni/Sigma/Ptv/Pdnd), non qui.

