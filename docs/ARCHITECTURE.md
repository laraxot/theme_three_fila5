---
title: "Three Theme Architecture"
type: architecture
tags: [theme, architecture, three, frontend]
created: 2026-08-04
updated: 2026-08-04
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
