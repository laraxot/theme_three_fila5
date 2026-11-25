---
title: "Three — operazioni sul repo: sync multi-org, release, tooling"
type: how-to
theme: Three
status: active
updated: 2026-11-25
qmd: "three git sync multi org laraxot provtv remote push no-thin unshallow unrelated histories semantic release changelog graphify second brain agent pandoc"
merged_from:
  - bmad/git-multi-org-sync-handoff.md
  - bmad/gitmodules-sync-session.md
  - bmad/multi-org-sync-laraxot-provtv.md
  - wiki/prompts/push.md
  - bmad/release-marketing-standard.md
  - bmad/pandoc-guide.md
  - wiki/ai-tooling.md
  - bmad/graphify-map.md
  - bmad/second-brain.md
  - wiki/agent-confidence-discipline.md
  - wiki/agent-confidence-protocol.md
  - wiki/agent-edit-discipline.md
  - wiki/docs-archive-policy.md
  - wiki/context-compression.md
---

# Three — operazioni sul repo

## Sync multi-organizzazione

Il repo ha due remote: `laraxot` (upstream, `git@github.com:laraxot/theme_three_fila5.git`) e
`provtv` (`git@github.com:provtv/theme_three_fila5.git`), branch `dev`. Prompt di progetto:
`bashscripts/tools/prompts/02-gitmodules-sync.md`.

1. `git remote -v` — mai assumere l'org; `git fetch --all --prune`.
2. `git status --short --branch`: modifiche locali si committano prima del merge (niente
   stash/reset/restore/checkout/force).
3. Per ogni remote: `git rev-list --left-right --count HEAD...<remote>/dev`.
   `N 0` → push fast-forward; `* M>0` → merge forward-only e ricontrollo; `0 0` → allineato.
4. Chiusura: `0 0` su ogni remote raggiungibile e tree pulito.

Casi reali visti (luglio 2026):

- push respinto `did not receive expected object` / `unpack failed` → clone shallow:
  `git fetch --unshallow` oppure `git push --no-thin`.
- `dev` remoto rigenerato senza antenato comune → `git merge --allow-unrelated-histories` con
  revisione manuale dei conflitti add/add (di solito contenuto identico).

## Release

`.releaserc.json` nel root del tema (semantic-release); il changelog di release e'
`../CHANGELOG.md`, quello della documentazione e' [CHANGELOG.md](./CHANGELOG.md). Il README non
deve promettere funzionalita' che il codice non ha.

## Tooling

- graphify: per un solo Blade non serve un grafo dedicato; la lettura diretta costa meno.
- Pandoc (export documentazione): `~/.local/bin/pandoc`, uso generico, nessuna config di tema.
- Disciplina agenti, second brain, compressione contesto: regole di progetto, non di tema —
  `bashscripts/ai/wiki/rules/00-TRIGGER_MAP.md`, `bashscripts/ai/wiki/rules/second-brain.md`.
- Niente cartelle `legacy/`/`archive/` in `docs/`: lo storico sta in git.
