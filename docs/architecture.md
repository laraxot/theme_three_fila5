---
title: "Three Theme Architecture"
type: architecture
tags: [theme, architecture, three]
created: 2026-08-04
updated: 2026-08-24
---
# Three Theme — Architecture

## Purpose
Three theme architecture and design patterns for Laraxot PTVX.

## Core Components

**Views:**
- Blade templates for base layouts
- Component-based structure

**Assets:**
- Vite build pipeline
- Tailwind CSS compilation

**Providers:**
- ThemeServiceProvider registration

## Quality Gates
- Build passes without errors
- Components render correctly
- Performance optimized
- Le modifiche PHP rispettano il gate canonico `cd laravel && ./vendor/bin/phpstan analyse Modules`
- PHPStan usa esclusivamente `laravel/phpstan.neon` (`level: max`): niente baseline,
  esclusioni, `--level` o soppressioni inline

---

<!-- Merged from ARCHITECTURE.md, which collided with this file on case-insensitive filesystems. -->

---
title: "Three Theme Architecture"
type: architecture
tags: [theme, architecture, three, frontend]
created: 2026-08-04
updated: 2026-08-24
---
# Three Theme — Architecture

## Purpose
Complex theme transforming complex functionality into ready-to-use experience

## Core Components

**Views:**
- Blade templates for Three-specific layouts
- Component-based structure
- Filament integration patterns

**Assets:**
- Vite-based build pipeline
- CSS/JS compilation with Tailwind

**Providers:**
- `ThreeThemeServiceProvider` — Theme registration
- View namespace configuration

## Design Decisions

| Decision | Rationale |
|----------|-----------|
| Blade templates | Laravel-native, component-friendly |
| Tailwind utility-first | Rapid, consistent styling |
| Vite bundler | Fast HMR, optimized builds |

## Integration Points
**Depends On:** Laravel, Blade, Tailwind CSS, Vite
**Active Theme:** Applied system-wide or tenant-specific

## Quality Gates
- **Build**: npm run build passes
- **Lint**: Tailwind/Pug linter checks
- **Preview**: Theme renders correctly in browser
- **PHP**: il gate effettivo è `./vendor/bin/phpstan analyse Modules` da `laravel/`;
  una story che modifica PHP del tema aggiunge test mirati quando quel file non è
  raggiunto dal perimetro `Modules`
