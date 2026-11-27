---
title: "ADR — Theme Three"
type: index
owner: Three
updated: 2026-11-24
qmd: "Theme Three ADR architecture decision record MADR formato nessuna decisione"
---

# ADR — Theme Three

Un ADR del tema Three registrerebbe una scelta difficile da invertire, sorprendente o frutto di un trade-off reale. Template condiviso: [0000-template](../../../../Modules/Xot/docs/adr/0000-template.md).

## Formato MADR

Frontmatter (`title`, `type: decision`, `status`, `created`, `updated`, `decision-makers`, `module`, `qmd`) e sezioni nell'ordine: `## Contesto`, `## Driver della decisione`, `## Alternative scartate`, `## Decisione`, `## Conseguenze`, `## Conferma`. Nome file in kebab-case senza data né numero.

## ADR presenti

**Nessuno.** La sola questione aperta (archiviare Three oppure completarlo) è dichiarata nel [README docs](../README.md) come decisione ancora da prendere: non si registra come ADR una decisione che non c'è. Quando verrà presa, creare qui l'ADR con la prova nel codice.

## Harness minimo: ownership, evidenza e recupero (2026-11-27)

Questo indice appartiene a **theme_three_fila5**: ogni decisione su codice, dominio o tema va nell'ADR del package owner; il root registra soltanto i vincoli di composizione. Un ADR richiede una scelta reale con alternative e conseguenze, più una **Conferma** ripetibile (oppure la dichiarazione esplicita che manca). Non creare ADR fittizi per riempire un indice.

- [Confine LaravelDay/harness Xot](https://github.com/laraxot/module_xot_fila5/blob/dev/docs/adr/0042-laravel-day-harness-adoption-boundary.md); [ownership root](https://github.com/laraxot/base_ptvx_fila5/blob/dev/docs/adr/0001-harness-minimo-e-ownership.md).
- **BMAD**: la story owner-local conserva `scope`, `must_not_change`, `evidence`, `approval_required` nei cambi rischiosi.
- **ECC**: nessun marker di merge; distinguere la prova eseguita dal semplice riferimento a un test; se la conferma non è disponibile segnare `non eseguita`.
- **Second Brain**: QMD/Graphify e `.harness/memory/{facts,lessons}.md` sono puntatori a evidenza datata, non copie degli ADR. [Runbook](https://github.com/laraxot/base_ptvx_fila5/blob/dev/docs/harness/README.md) · [Rollout #15](https://github.com/laraxot/base_ptvx_fila5/issues/15).
