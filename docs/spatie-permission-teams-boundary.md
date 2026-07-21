---
title: "Spatie Permission teams boundary"
type: rule
tags: ['laravel', 'permission']
created: 2026-07-14
updated: 2026-07-14
qmd: "spatie permission teams boundary"
related:
  - "./agent-confidence-discipline.md"
  - "./agent-confidence-protocol.md"
  - "./agent-edit-discipline.md"
---

# Spatie Permission teams boundary

## Rule

Three follows the same boundary as the active themes: authorization package configuration is not theme-owned.

## Laravel 13 note

With Laravel 13 and Spatie Permission 7, the teams feature requires `permission.models.team`. If the dashboard fails with `TeamModelNotConfigured`, fix the permission config and clear the config cache; do not patch theme views.

## References

- User module fix note: [../../../laravel/Modules/User/docs/spatie-permission-teams-laravel-13.md](../../../laravel/Modules/User/docs/spatie-permission-teams-laravel-13.md)
- Xot bridge note: [../../../laravel/Modules/Xot/docs/spatie-permission-team-model-laravel-13.md](../../../laravel/Modules/Xot/docs/spatie-permission-team-model-laravel-13.md)
