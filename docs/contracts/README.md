---
title: "Contratti — Theme Three"
type: index
owner: Three
updated: 2026-11-24
qmd: "Theme Three contract assenti tema non registrabile presentation-contract"
---

# Contratti — Theme Three

Standard: [contract-authoring-standard](../../../../Modules/Xot/docs/contracts/contract-authoring-standard.md).

## Stato

**Nessun contract in Three.** Motivo: Three non è un tema funzionante. Contiene un solo file Blade (`resources/views/components/blocks/links/grid.blade.php`, byte a byte identico a quello di One e Zero) e nessuna Action, classe PHP, `theme.json`, `composer.json`, `package.json` o `vite.config.js`; nessun file di `config/` e nessun codice dei moduli lo nomina (`rg 'Three'` su `laravel/config` e `Modules/*/app`, 2026-11-24). Un contract descriverebbe un comportamento che non esiste.

## File presenti

- [index.md](index.md): registro operativo

## Harness minimo: ownership, evidenza e recupero (2026-11-27)

I contratti di **theme_three_fila5** restano accanto alle Action, interfacce o superfici di questo package; root e Xot definiscono lo standard, non copiano le promesse. Un contratto comportamentale esplicita **Input, Output, Invarianti, Effetti collaterali, Errori, Non fa**; ogni ID di invariante punta a un group Pest effettivo oppure segnala `non dimostrata`. Se esiste la classe, il docblock deve rimandare al file con `@contract` e `@see`; per temi senza classi PHP non inventare Action/contratti.

- [Standard Xot](https://github.com/laraxot/module_xot_fila5/blob/dev/docs/contracts/contract-authoring-standard.md) · [ownership root](https://github.com/laraxot/base_ptvx_fila5/blob/dev/docs/adr/0001-harness-minimo-e-ownership.md) · [runbook ECC/Second Brain](https://github.com/laraxot/base_ptvx_fila5/blob/dev/docs/harness/README.md).
- **BMAD**: prima di cambiare una promessa, fissa nella story owner scope, esclusioni, evidenza e approvazioni richieste.
- **ECC**: i marker di merge rendono invalido l'indice; citare una suite non significa averla eseguita. Distingui `pass`, `fail`, `non eseguito` e registra il debito in [rollout #15](https://github.com/laraxot/base_ptvx_fila5/issues/15).
