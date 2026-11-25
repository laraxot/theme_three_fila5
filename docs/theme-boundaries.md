---
title: "Three — confini del tema e regole se venisse completato"
type: concept
theme: Three
status: active
updated: 2026-11-25
qmd: "three confini tema presentazione moduli composer laravel 13 migrazioni spatie permission team public_html asset binari no git lfs filament xotbase table class"
merged_from:
  - wiki/architecture-rules.md
  - bmad/one-migration-themes-boundary.md
  - bmad/laravel-13-composer-boundary.md
  - bmad/laravel-13-upgrade.md
  - bmad/spatie-permission-team-context.md
  - bmad/spatie-permission-teams-boundary.md
  - wiki/concepts/platform-leaf-dependency-and-theme.md
  - wiki/concepts/module-directory-structure-boundary.md
  - wiki/document-root-public-html.md
  - wiki/public-path-public-html.md
  - wiki/binary-assets.md
  - bmad/no-git-lfs.md
  - bmad/filament-blueprint.md
  - wiki/filament-admin-sub-navigation.md
  - wiki/filament-resource-schemas-tables.md
  - wiki/filament-table-architecture.md
  - wiki/filament-version.md
  - bmad/naming-conventions.md
---

# Three — confini del tema

## Scopo

Three non ha codice da governare (vedi [README](./README.md)). Questa pagina fissa i confini
che valgono per qualunque tema del progetto, cosi' che un eventuale completamento parta giusto.
Stack: Laravel 13, Filament 5, PHP 8.4.

## Il tema e' solo presentazione

- Un tema contiene Blade, CSS/JS, asset, traduzioni. **Niente** modelli Eloquent, migration,
  policy, Action di dominio: stanno nel modulo owner (regola "1 modello = 1 migrazione" vive
  in `laravel/Modules/`).
- Direzione dipendenze: Xot → Ptv → leaf (Progressioni, Indennita*, Performance). Il tema sta
  fuori: puo' rendere dati passati dai moduli, non fa `use Modules\<Dominio>\Models\...`.
- Struttura directory come i moduli: codice funzionale solo in `app/`, `database/` minuscolo,
  niente cartelle maiuscole in root.
- Autorizzazioni: il tema **consuma** lo stato (ruoli/permessi/team), non lo possiede. Modelli
  permission/role/team nel modulo User; con Spatie Permission 7 e teams serve
  `permission.models.team` (errore `TeamModelNotConfigured` → correggere config, poi
  `config:clear`).

## Composer

Framework e moduli in `laravel/composer.json`; pacchetti di modulo in
`Modules/<Mod>/composer.json`. Il tema dichiara un `composer.json` (e lo si aggiunge al
merge-plugin) solo se ha dipendenze PHP runtime o PSR-4 propri. Debugbar resta in Xot
(`fruitcake/laravel-debugbar`), mai nel tema.

## Asset e document root

- `public_path()` = `{repo}/public_html/`, mai `laravel/public/` (override in
  `laravel/app/Application.php`). Asset buildati in `public_html/themes/{Theme}/`.
  SSoT: `bashscripts/ai/wiki/memories/frontend-themes-css.md#public-path-is-public-html`.
- Binari (immagini, font, PDF) come blob git normali: **niente Git LFS** (`filter=lfs` in
  `.gitattributes`, `git lfs track`, file pointer al posto del contenuto). Regola di progetto:
  `bashscripts/ai/wiki/rules/git-workflow.md`.

## Filament (se il tema venisse completato)

- Estendere solo basi Xot (`XotBaseResource`, `XotBasePage`, `XotBaseWidget`, ...), mai classi
  Filament dirette. Nessuna `->label('...')`: chiavi in `lang/<locale>/`.
- Resource: vivono nei moduli, non nel tema. Override di viste Filament ammessi solo in
  `resources/views/filament/`.
- Colonne/filtri/azioni in `Tables/<Plurale>Table.php` (estende `XotBaseResourceTable`), mai
  `getTable*` sulla pagina List (`getTableColumns()` e' `final` in `XotBaseListRecords`).
  Canon: `laravel/Modules/Xot/docs/wiki/memories/tabella-appartiene-alla-resource-non-alla-pagina.md`;
  guardie `Modules/Xot/tests/Unit/Filament/TableColumnsBelongsToTableClassTest.php`.
- Le tab sopra una pagina di record (sub navigation) sono decise dalla Resource del modulo
  (`getRecordSubNavigation()`), non dal tema.
- Widget frontoffice montati esplicitamente nella pagina; niente `discoverWidgets` per il chrome.

## Insidie note

- Molti documenti precedenti descrivevano una pipeline Vite/Tailwind, Resource Filament e
  naming di permessi "di Three": **nessuno aveva codice corrispondente**. Non reintrodurli
  senza codice.
- Gate PHPStan unico: `cd laravel && php -d memory_limit=2G ./vendor/bin/phpstan analyse`
  (paths = `Modules/`); nessun neon di tema.
