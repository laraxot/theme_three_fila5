---
title: "Filament Blueprint — Theme Three"
type: filament-blueprint
status: active
theme: Three
created: 2026-10-21
updated: 2026-10-21
tags: [bmad, filament, blueprint, theme, three, xotbase]
qmd: "filament blueprint theme three xotbase resource widget tenant policy phpstan gate"
related:
  - ./architecture.md
  - ./tech-spec.md
  - ../../../../Modules/Xot/docs/bmad/filament-blueprint.md
---

# Scopo

Contratto Filament del tema **Three**. Three non e' oggi registrabile come tema
(mancano `theme.json`, `composer.json`, `app/` e `lang/`): il blueprint definisce
cosa sarebbe ammesso se il tema venisse completato o riattivato.

## Regole non negoziabili

1. Estendere solo `XotBaseResource`, `XotBaseWidget`, `XotBasePage` o le altre basi
   Xot; mai le classi Filament dirette.
2. Nessuna label hardcoded: niente `->label('...')`, chiavi in `lang/<locale>/`.
3. Logica di business nelle Queueable Action del modulo owner; il tema resta
   presentazione (Blade, asset, traduzioni).
4. Nessun modello, migration o policy nel tema.

## Resource e widget

- Resource PHP: nessuna in Three; le Resource vivono nei moduli.
- Widget frontoffice: montaggio **esplicito** nella pagina o nel pannello; non
  usare `discoverWidgets` per il chrome del tema.
- Override di viste Filament ammesso solo in `resources/views/filament/`.

## Form, table e infolist

Usare la triad `*Form`, `*Table`, `*Infolist` e enum tipizzati quando il tema
verra' attivato. Nessun campo duplicato dai moduli.

## Tenant e policy

Ogni query passa dal modulo owner e rispetta tenant e policy del modello. Il tema
non crea elenchi cross-tenant.

## Gate PHPStan

Il gate e' `cd laravel && php -d memory_limit=2G ./vendor/bin/phpstan analyse Modules`
con il solo `laravel/phpstan.neon`. Nessun neon di tema, nessuna analisi del solo
tema come gate.

## Riferimenti

- Architettura del tema: [architecture.md](./architecture.md)
- Specifica tecnica: [tech-spec.md](./tech-spec.md)
- Contratto Xot: [filament-blueprint.md](../../../../Modules/Xot/docs/bmad/filament-blueprint.md)
- Organizzazione docs: [../../../../Modules/Xot/docs/conventions/docs-organization.md](../../../../Modules/Xot/docs/conventions/docs-organization.md)
