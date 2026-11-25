---
title: "Theme Three — scopo e stato reale"
type: readme
theme: Three
status: active
updated: 2026-11-25
qmd: "theme three scopo guscio un solo blade blocks links grid identico one zero nessun theme.json non registrabile decisione archiviare completare"
merged_from:
  - bmad/purpose.md
  - bmad/scopo.md
  - bmad/readme.md
  - bmad/readme-en.md
  - glossary.md
---

# Theme Three — scopo e stato reale

## Lo scopo in una frase

Three oggi **non e' un tema funzionante**: e' un repo con un solo file Blade, identico a quello
di One e Zero, che nessuna configurazione seleziona. Lo scopo non si deduce dal codice: va
**deciso** (archiviare o completare) — story
[0.1.archive-or-complete-decision](./bmad/stories/0.1.archive-or-complete-decision.story.md)
(`blocked`, attende il maintainer; issue `laraxot/theme_three_fila5#7`, discussion `#8`).

## Evidenza (verificata 2026-11-25)

| Fatto | Valore |
|---|---|
| Codice | 1 file: `resources/views/components/blocks/links/grid.blade.php` (39 righe) |
| Duplicato | md5 identico all'omonimo in `Themes/One` e `Themes/Zero` |
| PHP / CSS / JS / test | 0 |
| `theme.json`, `composer.json`, `package.json`, `vite.config.*`, `lang/`, `app/` | assenti |
| Selezionato da config | no: `pub_theme`/`adm_theme` non valgono mai `Three` |
| Registrabile | no: `XotData::getPubThemeViewPath()` fallirebbe su `realpath` alla prima view |

Root del repo: `.gitattributes`, `.gitignore`, `.releaserc.json` (semantic-release),
`CHANGELOG.md`, `README.md`, `_theme_three_fila5.code-workspace`, `docs/`, `resources/`.

## Glossario minimo

- **Blocco `links/grid`**: sezione con titolo, descrizione e griglia di link opzionali, stili
  inline. Unico elemento di presentazione del tema.
- **Tema non registrabile**: privo dei file che lo rendono selezionabile come `pub_theme`.
- **Release automatica**: `.releaserc.json` del repo tema; il changelog di release e' `../CHANGELOG.md`.

## Le due strade (dalla story 0.1)

1. **Archiviare**: prima decidere dove va `grid.blade.php` (promuoverlo in
   `Modules/UI/resources/views/components/blocks/links/` se serve a One/Zero, altrimenti
   rimuoverlo); la documentazione segue il tema.
2. **Completare**: replicare lo scaffolding minimo di Zero (`theme.json`, `composer.json`,
   `package.json`, `vite.config.js`, layout, `resources/css/app.css`, `resources/js/app.js`)
   e scrivere **prima** la ragione visiva di un terzo tema. Solo dopo, story di implementazione.

Finche' la decisione non c'e', non si scrive documentazione che descriva architettura,
pipeline Vite/Tailwind o Resource Filament: non esistono.

## Documentazione

- [Mappa argomenti](./00-INDEX.md)
- [Confini tema e regole se venisse completato](./theme-boundaries.md)
- [Stato qualita' misurato](./quality-status.md)
- [Operazioni repo: sync multi-org, release, tooling](./repo-operations.md)
- [ADR](./adr/README.md) · [Contratti](./contracts/README.md) · [Changelog docs](./CHANGELOG.md)
