---
title: documentazione tema Three
module: Three
type: index
status: approved
tags: [documentation, readme, tema, second-brain]
updated: "2026-07-27"
related:
  - ../README.md
  - ../../../../docs/wiki/troubleshooting/phpstan-stale-ignore-pattern.md
---

# 🎨 Tema Three - Tema Sperimentale Laraxot

[![Laravel 12.x](https://img.shields.io/badge/Laravel-12.x-red.svg)](https://laravel.com/)
[![Filament 5.x](https://img.shields.io/badge/Filament-5.x-blue.svg)](https://filamentphp.com/)
[![PHP 8.4](https://img.shields.io/badge/PHP-8.4-blueviolet.svg)](https://www.php.net/)
[![PHPStan Level 10](https://img.shields.io/badge/PHPStan-Level%2010-brightgreen.svg)](https://phpstan.org/)
[![Experimental](https://img.shields.io/badge/Status-Experimental-yellow.svg)](#)

> **Tema Three**: Tema sperimentale e laboratorio per nuove features e design patterns in Laraxot PTVX.

## 📋 Overview

Tema **Three** è il tema sperimentale di Laraxot PTVX, dedicato a:
- Ricerca e sviluppo di nuovi pattern UI
- Prototipazione di features avanzate
- Testing di dipendenze e integrazioni
- Innovazione incrementale del design system

**Mappa knowledge base locale**: Il [README in root](../README.md) è la vetrina (valore, release, onboarding); questo file indica **dove** trovare regole, wiki e audit per chi sviluppa o per gli agenti AI.

## 🎯 Scopo

Tema Three Laraxot PTVX — laboratorio di innovazione e documentazione operativa.

## Qualità (2026-07-27)

- PHPStan: `analyse Modules` (o `Modules Themes`). Mai `Themes` da solo — [phpstan-stale-ignore-pattern](../../../../docs/wiki/troubleshooting/phpstan-stale-ignore-pattern.md).
- Remote: `cd laravel/Themes/Three && git remote -v`.

## Dove iniziare

- [code redundancy audit](./code-redundancy-audit.md)
- [architecture rules](./architecture-rules.md)
- [agent edit discipline](./agent-edit-discipline.md)
- [agent confidence protocol](./agent-confidence-protocol.md)
- [second brain](./second-brain.md)


## Struttura tipica

```text
Three/
├── README.md          ← vetrina (root package)
├── docs/
│   ├── README.md      ← questo indice
│   └── wiki/          ← second brain (se presente)
├── app/ o resources/
└── composer.json
```

## Namespace / confini

- Namespace: `Themes\Three`
- Non duplicare qui la filosofia marketing: resta nel README root.

## Indice file in docs/ (root)

| Argomento | File |
| :--- | :--- |
| agent-confidence-discipline | [agent-confidence-discipline.md](./agent-confidence-discipline.md) |
| agent-confidence-protocol | [agent-confidence-protocol.md](./agent-confidence-protocol.md) |
| agent-edit-discipline | [agent-edit-discipline.md](./agent-edit-discipline.md) |
| architecture-rules | [architecture-rules.md](./architecture-rules.md) |
| code-redundancy-audit | [code-redundancy-audit.md](./code-redundancy-audit.md) |
| changelog | [changelog.md](./changelog.md) |
| context-compression | [context-compression.md](./context-compression.md) |
| docs-archive-policy | [docs-archive-policy.md](./docs-archive-policy.md) |
| filament-version | [filament-version.md](./filament-version.md) |
| laravel-13-composer-boundary | [laravel-13-composer-boundary.md](./laravel-13-composer-boundary.md) |
| laravel-13-upgrade | [laravel-13-upgrade.md](./laravel-13-upgrade.md) |
| naming-conventions | [naming-conventions.md](./naming-conventions.md) |
| release-marketing-standard | [release-marketing-standard.md](./release-marketing-standard.md) |
| second-brain | [second-brain.md](./second-brain.md) |
| spatie-permission-team-context | [spatie-permission-team-context.md](./spatie-permission-team-context.md) |
| spatie-permission-teams-boundary | [spatie-permission-teams-boundary.md](./spatie-permission-teams-boundary.md) |

## Collegamenti

- [README root (vetrina)](../README.md)
- [Xot (framework base)](../../../Modules/Xot/docs/README.md)
- [Wiki progetto](../../../../docs/wiki/README.md)
- [Standard README doppio](../../../../docs/wiki/standards/module-theme-readme-dual.md)

## Per agenti

1. Leggere scopo in questo file.
2. Aprire `docs/wiki/index.md` se esiste.
3. Seguire [disciplina issue GitHub](../../../../docs/wiki/how-to/github-issue-agent-discipline.md) prima di modifiche sostanziali.
