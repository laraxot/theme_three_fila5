---
title: "Handoff multi-org sync (STORY-003)"
type: handoff
tags: [git, multi-org, bmad, story-003]
created: 2026-07-21
updated: 2026-07-23
module: "Three"
issues:
  - "https://github.com/provtv/theme_three_fila5/issues/1"
discussions:
  - "https://github.com/provtv/theme_three_fila5/discussions/2"
---

# Handoff — multi-org sync (STORY-003)

## Scopo

Allineare questo owner ai remote raggiungibili (**0 0**, working tree clean) e documentare decisioni di sessione 2026-07-21.

## Perché

Un tree dirty o un remote dietro/avanti **non** è sincronizzato, anche se l’altro org è a posto. Su PTVX i path vivono in `gitmodules.ini` con org `provtv` (+ `laraxot` se esiste).

## Link

| Tipo | URL |
|------|-----|
| Issue owner | https://github.com/provtv/theme_three_fila5/issues/1 |
| Discussion | https://github.com/provtv/theme_three_fila5/discussions/2 |
| Hub base issue | https://github.com/provtv/base_ptv_fila5/issues/203 |
| Hub base discussion | https://github.com/provtv/base_ptv_fila5/discussions/204 |
| Story monorepo | `docs/stories/STORY-003-multi-org-sync-geo-boundary-bashscripts.md` |

## Regole rapide

1. `cd` owner → `git remote -v` → fetch tutti → merge senza force → push tutti
2. Dopo edit PHP: phpstan/phpmd/phpinsights scoped (prompt `02-gitmodules-sync.md`)
3. Mai `git restore` — forward-only
4. UI: non reintrodurre `InteractiveMap` (dominio Geo)

## Note owner

Tema: discussion locale abilitata.

### Playbook push dual-remote (2026-07-22)


### Caso User 2026-07-23 (unrelated)

`merge-base` vuoto vs un org → STOP. User: laraxot `3ea7273a` OK; provtv unrelated.
[../../../Modules/User/docs/wiki/troubleshooting/git-push-dual-remote-unrelated.md](../../../Modules/User/docs/wiki/troubleshooting/git-push-dual-remote-unrelated.md).

## Stato sync 2026-07-23 (sessione successiva)

- **Remotes:** entrambi raggiungibili — `laraxot` (`git@github.com:laraxot/theme_three_fila5.git`), `provtv` (`git@github.com:provtv/theme_three_fila5.git`).
- **Working tree:** dirty su `docs/git-multi-org-sync-handoff.md` + `docs/multi-org-sync-laraxot-provtv.md` (note di sessione precedente, non conflitto) → committato con `chore(Three): sync locale — commit lavoro in sospeso` (`1fd89e7`).
- **Sync:** 0 commit mancanti da entrambi i remote, 1 commit nostro non ancora pubblicato su entrambi → pushato senza conflitti su `laraxot` (`fd1ac8c..1fd89e7`) e `provtv` (`fd1ac8c..1fd89e7`).
- Nessun merge/rebase in corso, nessun marker di conflitto, nessuna correzione di codice necessaria.
- **Stato finale:** branch `dev` allineato a entrambi `laraxot/dev` e `provtv/dev`, working tree pulito.
