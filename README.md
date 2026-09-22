# Three: il tema che trasforma complessita in vantaggio operativo

Tema Laraxot pensato per trasformare funzionalita complesse in esperienza pronta, documentata e governabile.

## Perche guardarlo adesso

- Riduce attrito operativo con convenzioni Laraxot gia pronte.
- Porta documentazione, release e changelog nello stesso flusso verificabile.
- Aiuta team e agenti AI a capire subito scopo, confini e prossime mosse.
- E pensato per crescere: semantic versioning, auto release e changelog automatico sono gia configurati.

## Cosa promette

Questo tema non e solo codice: e una vetrina operativa. Mostra dove intervenire, cosa leggere, come rilasciare e come mantenere alta la confidenza tecnica.

## Release automation

- Workflow: [Semantic Release](./.github/workflows/semantic-release.yml)
- Config: [.releaserc.json](./.releaserc.json)
- Changelog: [changelog.md](./changelog.md)

## Documentazione essenziale

- **[Indice docs (entrypoint)](./docs/README.md)** — obbligatorio per navigazione e agenti
- [Audit ridondanza](./docs/code-redundancy-audit.md)
- [Protocollo confidenza](./docs/agent-confidence-protocol.md)
- [Disciplina agenti](./docs/agent-edit-discipline.md)
- [Architecture Rules](./docs/architecture-rules.md)
- [Context Compression](./docs/context-compression.md)
- [Docs Archive Policy](./docs/docs-archive-policy.md)
- [Filament Version](./docs/filament-version.md)
- [Laravel 13 Composer Boundary](./docs/laravel-13-composer-boundary.md)
- [Laravel 13 Upgrade](./docs/laravel-13-upgrade.md)
- [Second Brain](./docs/second-brain.md)

## Scopo e confini

Three, oggi, non è un tema: è una cartella di documentazione con dentro un file Blade
duplicato da Zero. Misurato il 2026-09-02: **1** file `.blade.php`
(`components/blocks/links/grid.blade.php`, byte a byte identico a quello di One e di
Zero) contro **54** documenti Markdown in `docs/`. Mancano `theme.json`,
`composer.json`, `package.json`, `vite.config.js`, `tailwind.config.js`, `app/`, `lang/`
e `public/`; nessuna configurazione lo nomina (`pub_theme` è `Zero` in produzione, `One`
su `localhost`). Non è incompleto: non è registrabile.

Misure e le quattro mosse per decidere — archiviare oppure completare:
[`docs/scopo.md`](./docs/scopo.md).

## Filosofia

Scopo prima del codice. DRY prima dell'orgoglio. KISS prima dell'astrazione. La release automatica non sostituisce il giudizio: lo rende tracciabile.
