---
title: "Documentazione Theme Three"
type: index
tags: [theme, three, documentation]
created: 2026-07-21
updated: 2026-10-06
qmd: "theme three documentation index architecture product requirements wiki bmad"
---

# Documentazione Theme Three

Parti da [index.md](./index.md): raccoglie tutti i documenti Markdown del tema
e li ordina per argomento.

## Struttura attuale

- I documenti generali e di prodotto sono in questa cartella.
- `bmad/` contiene story BMAD.
- `epics/` contiene epic e relative story.
- `prompts/` contiene prompt operativi.
- `wiki/` contiene concetti e note di conoscenza.

Aggiorna l'indice quando aggiungi o sposti documentazione. La normalizzazione
delle altre cartelle e' tracciata in [`docs-reorg.md`](../../docs-reorg.md).

<!-- swarm-docs:index:start -->

## Mappa della documentazione (indice di radice, generato dalla passata swarm-docs 2026-10-06)

Sezione generata: raggruppamento euristico per nome e titolo, nessun file e' stato spostato o rinominato. Marcatori: `[orfano]` = prima di questa passata nessun file della cartella `docs/` lo linkava; `[dup]` = sospetto duplicato (vedi sezione dedicata); `[marker di merge]` = contiene `<<<<<<<` o `>>>>>>>` non risolti.

### Entry point e struttura

- Modulo o tema: [../README.md](../README.md) (vetrina), [../../../Modules/Xot/docs/README.md](../../../Modules/Xot/docs/README.md) (docs del modulo base Xot)
- [index.md](./index.md): indice gia' presente
- [purpose.md](./purpose.md): scopo (esiste anche l'equivalente italiano/inglese, possibile duplicato)
- [scopo.md](./scopo.md): scopo (esiste anche l'equivalente italiano/inglese, possibile duplicato)
- Architettura: [architecture.md](./architecture.md)
- Architettura: [architecture-rules.md](./architecture-rules.md)
- [wiki/index.md](./wiki/index.md)
- Story BMAD (posizione canonica): [bmad/stories/](./bmad/stories/) (1 file)

### Sottocartelle

| Cartella | File .md (ricorsivo) | Entry point | Nota |
| --- | --- | --- | --- |
| [bmad/](./bmad/) | 1 | nessuno |  |
| [epics/](./epics/) | 1 | nessuno |  |
| [prompts/](./prompts/) | 1 | nessuno |  |
| [wiki/](./wiki/) | 7 | [index.md](./wiki/index.md) |  |

### File di radice per argomento

#### Agenti AI e regole di lavoro (7)

- [agent-confidence-discipline.md](./agent-confidence-discipline.md): Disciplina agenti per massimizzare la confidenza
- [agent-confidence-protocol.md](./agent-confidence-protocol.md): Massima confidenza agente
- [agent-edit-discipline.md](./agent-edit-discipline.md): agent edit discipline — puntatore
- [ai-tooling.md](./ai-tooling.md): Strumenti AI nel tema Three
- [context-compression.md](./context-compression.md): KiloCLI Contestazione Contesto Configurazione per Three
- [graphify-map.md](./graphify-map.md): Three Theme — Mappa Graphify
- [second-brain.md](./second-brain.md): second brain — puntatore tema

#### PHPStan, qualita e test (4)

- [code-redundancy-audit.md](./code-redundancy-audit.md): Code redundancy audit — Three
- [duplicate-methods-report.md](./duplicate-methods-report.md): Report: Metodi con nome duplicato nei moduli e nei temi [dup]
- [duplicate-methods.md](./duplicate-methods.md): Metodi duplicati — Three [dup]
- [quality-audit.md](./quality-audit.md): Audit di qualita: tema Three

#### Git, sync e conflitti (4)

- [git-multi-org-sync-handoff.md](./git-multi-org-sync-handoff.md): Handoff multi-org sync (STORY-003)
- [gitmodules-sync-session.md](./gitmodules-sync-session.md): Gitmodules sync session — note modulo/tema
- [multi-org-sync-laraxot-provtv.md](./multi-org-sync-laraxot-provtv.md): Sincronizzazione multi-organizzazione (laraxot + provtv)
- [no-git-lfs.md](./no-git-lfs.md): Git LFS vietato: linea guida e prototipo .gitattributes

#### Architettura e pattern (3)

- [architecture-rules.md](./architecture-rules.md): architecture rules — Theme Three
- [architecture.md](./architecture.md): Three Theme Architecture
- [filament-table-architecture.md](./filament-table-architecture.md): Dove si configura la tabella di una Resource Filament

#### Prodotto, roadmap e pianificazione (4)

- [cosa-migliorare.md](./cosa-migliorare.md): Cosa migliorare: tema Three
- [prd.md](./prd.md): Product Requirements Document (PRD) - Three Theme
- [release-marketing-standard.md](./release-marketing-standard.md): Release e README marketing — Three
- [tech-spec.md](./tech-spec.md): Technical Specification - Three Theme

#### Filament, UI e grafici (5)

- [filament-admin-sub-navigation.md](./filament-admin-sub-navigation.md): Sub navigation del pannello admin
- [filament-resource-schemas-tables.md](./filament-resource-schemas-tables.md): Filament Resource: Schemas e Tables (tema Three)
- [filament-version.md](./filament-version.md): Filament Version Declaration — Three
- [one-migration-themes-boundary.md](./one-migration-themes-boundary.md): Temi — nessuna migrazione owner
- [pandoc-guide.md](./pandoc-guide.md): Pandoc Documentation Generation Guide

#### Configurazione, permessi e confini (8)

- [binary-assets.md](./binary-assets.md): Asset binari
- [document-root-public-html.md](./document-root-public-html.md): Document root: public_html, non laravel/public
- [frameworks.md](./frameworks.md): Three — Framework Integration Notes
- [laravel-13-composer-boundary.md](./laravel-13-composer-boundary.md): Laravel 13 Composer boundary for Three
- [laravel-13-upgrade.md](./laravel-13-upgrade.md): Upgrade Laravel 13 - Theme Three 🐄✨
- [public-path-public-html.md](./public-path-public-html.md): public_path = public_html (tema)
- [spatie-permission-team-context.md](./spatie-permission-team-context.md): Spatie Permission Team Context
- [spatie-permission-teams-boundary.md](./spatie-permission-teams-boundary.md): Spatie Permission teams boundary

#### Indici, standard e meta-documentazione (6)

- [changelog.md](./changelog.md): Changelog — Three Theme
- [docs-archive-policy.md](./docs-archive-policy.md): Docs archive policy
- [naming-conventions.md](./naming-conventions.md): Naming Conventions — Three Theme
- [purpose.md](./purpose.md): Three — scopo del tema e come raggiungerlo meglio
- [readme-en.md](./readme-en.md): Three Theme — README (English)
- [scopo.md](./scopo.md): Three — scopo, confini e come servirlo meglio

### Sospetti duplicati (richiedono approvazione per il consolidamento)

Nessun file e' stato toccato. Proposte di destinazione nella story [swarm-phpstan-modular-docs-org](../../../Modules/Xot/docs/bmad/stories/swarm-phpstan-modular-docs-org.story.md).

- stesso nome normalizzato (maiuscole, `_`/`-`, `-en`, `-report`): [duplicate-methods-report.md](./duplicate-methods-report.md), [duplicate-methods.md](./duplicate-methods.md)

### Senza front matter (0)

nessuno

<!-- swarm-docs:index:end -->
